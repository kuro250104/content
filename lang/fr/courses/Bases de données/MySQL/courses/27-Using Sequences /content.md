## Introduction

Une séquence est un ensemble d'entiers 1, 2, 3, ... qui sont générés dans l'ordre sur une demande spécifique. Les
séquences sont fréquemment utilisées dans les bases de données car de nombreuses applications exigent que chaque ligne 
d'une table contienne une valeur unique et les séquences fournissent un moyen facile de les générer.

Ce chapitre décrit comment utiliser les séquences dans MySQL.

## Using AUTO_INCREMENT Column

La façon la plus simple d'utiliser les séquences dans MySQL est de définir une colonne comme **AUTO_INCREMENT** et de
laisser à MySQL le soin de s'occuper du reste.

### Exemple

Essayez l'exemple suivant. Il va créer une table et ensuite insérer quelques lignes dans cette table où il n'est pas 
nécessaire de donner l'ID de l'enregistrement car il est incrémenté automatiquement par MySQL.

``` sql
mysql> CREATE TABLE insect
   -> (
   -> id INT UNSIGNED NOT NULL AUTO_INCREMENT,
   -> PRIMARY KEY (id),
   -> name VARCHAR(30) NOT NULL, # type of insect
   -> date DATE NOT NULL, # date collected
   -> origin VARCHAR(30) NOT NULL # where collected
);
Query OK, 0 rows affected (0.02 sec)
mysql> INSERT INTO insect (id,name,date,origin) VALUES
   -> (NULL,'housefly','2001-09-10','kitchen'),
   -> (NULL,'millipede','2001-09-10','driveway'),
   -> (NULL,'grasshopper','2001-09-10','front yard');
Query OK, 3 rows affected (0.02 sec)
Records: 3  Duplicates: 0  Warnings: 0
mysql> SELECT * FROM insect ORDER BY id;
+----+-------------+------------+------------+
| id |    name     |    date    |   origin   |
+----+-------------+------------+------------+
|  1 |  housefly   | 2001-09-10 |   kitchen  |
|  2 |  millipede  | 2001-09-10 |  driveway  |
|  3 | grasshopper | 2001-09-10 | front yard |
+----+-------------+------------+------------+
3 rows in set (0.00 sec)
```

## Obtain AUTO_INCREMENT Values

La fonction **LAST_INSERT_ID( )** est une fonction SQL, vous pouvez donc l'utiliser à partir de n'importe quel client
qui comprend comment émettre des instructions SQL. Sinon, les scripts PERL et PHP fournissent des fonctions exclusives
pour récupérer la valeur auto incrémentée du dernier enregistrement.

### Exemple PERL

Utilisez l'attribut **mysql_insertid** pour obtenir la valeur **AUTO_INCREMENT** générée par une requête. Cet attribut
est accessible via un handle de base de données ou un handle d'instruction, selon la façon dont vous émettez la requête.

L'exemple suivant y fait référence par le biais du handle de la base de données.

``` php
$dbh->do ("INSERT INTO insect (name,date,origin)
VALUES('moth','2001-09-14','windowsill')");
my $seq = $dbh->{mysql_insertid};
```

### Exemple PHP

Après avoir émis une requête qui génère une valeur AUTO_INCREMENT, récupérez la valeur en appelant 
la commande **mysql_insert_id( )**.

``` php
mysql_query ("INSERT INTO insect (name,date,origin)
VALUES('moth','2001-09-14','windowsill')", $conn_id);
$seq = mysql_insert_id ($conn_id);
```

## Renumbering an Existing Sequence

Il peut arriver que vous ayez supprimé de nombreux enregistrements d'une table et que vous souhaitiez remettre tous
les enregistrements en séquence. Cela peut être fait en utilisant une astuce simple, mais vous devez faire très attention 
à le faire si votre table a des jointures avec l'autre table.

Si vous déterminez que le reséquencement d'une colonne AUTO_INCREMENT est inévitable, la façon de procéder est de
supprimer la colonne de la table, puis de la rajouter.

L'exemple suivant montre comment renuméroter les valeurs d'id dans la table en utilisant cette technique.

``` sql
mysql> ALTER TABLE insect DROP id;
mysql> ALTER TABLE insect
   -> ADD id INT UNSIGNED NOT NULL AUTO_INCREMENT FIRST,
   -> ADD PRIMARY KEY (id);
```

## Starting a Sequence at a Particular Value

Par défaut, MySQL commencera la séquence à partir de 1, mais vous pouvez également spécifier tout autre nombre au
moment de la création de la table.

Le programme suivant est un exemple qui montre comment MySQL va commencer la séquence à partir de 100.

``` sql
mysql> CREATE TABLE insect
   -> (
   -> id INT UNSIGNED NOT NULL AUTO_INCREMENT = 100,
   -> PRIMARY KEY (id),
   -> name VARCHAR(30) NOT NULL, # type of insect
   -> date DATE NOT NULL, # date collected
   -> origin VARCHAR(30) NOT NULL # where collected
);
```

Vous pouvez également créer la table, puis définir la valeur de la séquence initiale avec la commande **ALTER TABLE**.

``` sql
mysql> ALTER TABLE t AUTO_INCREMENT = 100;
```