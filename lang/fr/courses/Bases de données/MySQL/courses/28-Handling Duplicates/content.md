## Introduction

En général, les tables ou les ensembles de résultats contiennent parfois des enregistrements en double. La plupart du 
temps, cela est autorisé mais il est parfois nécessaire d'arrêter les enregistrements en double. Il est nécessaire 
d'identifier les enregistrements en double et de les supprimer de la table. Ce chapitre décrit comment empêcher
l'apparition d'enregistrements en double dans une table et comment supprimer les enregistrements en double déjà existants.

## Preventing Duplicates from Occurring in a Table

Vous pouvez utiliser une **PRIMARY KEY** ou un index **UNIQUE** sur une table avec les champs appropriés pour arrêter
les enregistrements en double.

Prenons un exemple - La table suivante ne contient pas d'index ou de clé primaire, elle autorise donc les 
enregistrements en double pour **first_name** et **last_name**.

``` sql
CREATE TABLE person_tbl (
   first_name CHAR(20),
   last_name CHAR(20),
   sex CHAR(10)
);
```

Pour empêcher la création de plusieurs enregistrements avec les mêmes valeurs de prénom et de nom de famille
dans cette table, ajoutez une **PRIMARY KEY** à sa définition. Dans ce cas, il est également nécessaire de déclarer
que les colonnes indexées sont **NOT NULL**, car une **PRIMARY KEY** n'autorise pas les valeurs **NULL**.

``` sql
CREATE TABLE person_tbl (
   first_name CHAR(20) NOT NULL,
   last_name CHAR(20) NOT NULL,
   sex CHAR(10),
   PRIMARY KEY (last_name, first_name)
);
```

La présence d'un index unique dans une table provoque normalement une erreur si vous insérez dans la table un
enregistrement qui duplique un enregistrement existant dans la ou les colonnes qui définissent l'index.

Utilisez la commande **INSERT IGNORE** plutôt que la commande **INSERT**. Si un enregistrement ne duplique pas un
enregistrement existant, MySQL l'insère comme d'habitude. Si l'enregistrement est un doublon, le mot-clé **IGNORE**
indique à MySQL de le rejeter silencieusement sans générer d'erreur.

L'exemple suivant n'entraîne pas d'erreur et, en même temps, il n'insère pas d'enregistrements en double.

``` sql
mysql> INSERT IGNORE INTO person_tbl (last_name, first_name)
   -> VALUES( 'Jay', 'Thomas');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT IGNORE INTO person_tbl (last_name, first_name)
   -> VALUES( 'Jay', 'Thomas');
Query OK, 0 rows affected (0.00 sec)
```

Utilisez la commande **REPLACE** plutôt que la commande INSERT. Si l'enregistrement est nouveau, il est inséré comme 
avec INSERT. S'il s'agit d'un doublon, le nouvel enregistrement remplace l'ancien.

``` sql
mysql> REPLACE INTO person_tbl (last_name, first_name)
   -> VALUES( 'Ajay', 'Kumar');
Query OK, 1 row affected (0.00 sec)

mysql> REPLACE INTO person_tbl (last_name, first_name)
   -> VALUES( 'Ajay', 'Kumar');
Query OK, 2 rows affected (0.00 sec)
```

Les commandes INSERT IGNORE et REPLACE doivent être choisies en fonction du comportement de traitement des doublons 
que vous souhaitez appliquer. La commande INSERT IGNORE conserve le premier jeu d'enregistrements dupliqués
et élimine les autres. La commande REPLACE conserve le dernier jeu d'enregistrements en double et efface les précédents.

Une autre façon de renforcer l'unicité est d'ajouter un index **UNIQUE** plutôt qu'une PRIMARY KEY à une table.

``` sql
CREATE TABLE person_tbl (
   first_name CHAR(20) NOT NULL,
   last_name CHAR(20) NOT NULL,
   sex CHAR(10)
   UNIQUE (last_name, first_name)
);
```

## Counting and Identifying Duplicates

Voici la requête pour compter les enregistrements en double avec prénom et nom dans une table.

``` sql
mysql> SELECT COUNT(*) as repetitions, last_name, first_name
   -> FROM person_tbl
   -> GROUP BY last_name, first_name
   -> HAVING repetitions > 1;
```

Cette requête renvoie une liste de tous les enregistrements en double dans la table person_tbl. En général, 
pour identifier des ensembles de valeurs qui sont dupliquées, suivez les étapes indiquées ci-dessous.

  - Déterminez les colonnes qui contiennent les valeurs susceptibles d'être dupliquées.
  - Énumérez ces colonnes dans la liste de sélection des colonnes, ainsi que le **COUNT(*)**.
  - Énumérez également les colonnes dans la clause **GROUP BY**.
  - Ajoutez une clause **HAVING** qui élimine les valeurs uniques en exigeant que le nombre de groupes soit supérieur à un.


## Eliminating Duplicates from a Query Result

Vous pouvez utiliser la commande **DISTINCT** avec l'instruction SELECT pour trouver les enregistrements uniques 
disponibles dans une table.

``` sql
mysql> SELECT DISTINCT last_name, first_name
   -> FROM person_tbl
   -> ORDER BY last_name;
```

Une alternative à la commande DISTINCT consiste à ajouter une clause GROUP BY qui nomme les colonnes que vous sélectionnez.
Cela a pour effet de supprimer les doublons et de ne sélectionner que les combinaisons uniques de valeurs dans 
les colonnes spécifiées.

``` sql
mysql> SELECT last_name, first_name
   -> FROM person_tbl
   -> GROUP BY (last_name, first_name);
```

## Removing Duplicates Using Table Replacement

Si vous avez des enregistrements en double dans une table et que vous voulez supprimer tous les enregistrements en 
double de cette table, suivez la procédure indiquée ci-dessous.

``` sql
mysql> CREATE TABLE tmp SELECT last_name, first_name, sex
   -> FROM person_tbl;
   -> GROUP BY (last_name, first_name);

mysql> DROP TABLE person_tbl;
mysql> ALTER TABLE tmp RENAME TO person_tbl;
```

Une façon simple de supprimer les enregistrements en double d'une table est d'ajouter un INDEX ou une PRIMARY KEY à 
cette table. Même si cette table est déjà disponible, vous pouvez utiliser cette technique pour supprimer les
enregistrements en double et vous serez en sécurité à l'avenir également.

``` sql
mysql> ALTER IGNORE TABLE person_tbl
   -> ADD PRIMARY KEY (last_name, first_name);
```