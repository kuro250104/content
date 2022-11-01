## Introduction

Un index de base de données est une structure de données qui améliore la vitesse des opérations dans une table. Les 
index peuvent être créés à partir d'une ou de plusieurs colonnes, ce qui permet d'effectuer des recherches aléatoires
rapides et d'ordonner efficacement l'accès aux enregistrements.

Lors de la création d'un index, il faut prendre en considération toutes les colonnes qui seront utilisées pour effectuer 
des requêtes SQL et créer un ou plusieurs index sur ces colonnes.

En pratique, les index sont également un type de tables, qui conservent la clé primaire ou le champ d'index et un
pointeur vers chaque enregistrement dans la table actuelle.

Les utilisateurs ne peuvent pas voir les index, ils sont juste utilisés pour accélérer les requêtes et seront utilisés 
par le moteur de recherche de la base de données pour localiser les enregistrements très rapidement.

Les instructions INSERT et UPDATE prennent plus de temps sur les tables ayant des index, alors que les instructions 
SELECT deviennent rapides sur ces tables. La raison en est que lors de l'insertion ou de la mise à jour, la base de
données doit également insérer ou mettre à jour les valeurs d'index.

## Simple and Unique Index

Vous pouvez créer un index unique sur une table. Un index unique signifie que deux lignes ne peuvent pas avoir la
même valeur d'index. Voici la syntaxe pour créer un index sur une table.

``` sql
CREATE UNIQUE INDEX index_name ON table_name ( column1, column2,...);
```

Vous pouvez utiliser une ou plusieurs colonnes pour créer un index.

Par exemple, nous pouvons créer un index sur tutorials_tbl en utilisant tutorial_author.

``` sql
CREATE UNIQUE INDEX AUTHOR_INDEX ON tutorials_tbl (tutorial_author)
```

Vous pouvez créer un index simple sur une table. Il suffit d'omettre le mot clé **UNIQUE** dans la requête pour créer un
index simple. Un index simple permet de dupliquer les valeurs dans une table.

Si vous souhaitez indexer les valeurs d'une colonne dans un ordre décroissant, vous pouvez ajouter le mot réservé
DESC après le nom de la colonne.

``` sql
mysql> CREATE UNIQUE INDEX AUTHOR_INDEX ON tutorials_tbl (tutorial_author DESC)
```

## ALTER command to add and drop INDEX

Il existe quatre types d'instructions permettant d'ajouter des index à une table.

  - **ALTER TABLE tbl_name ADD PRIMARY KEY (column_list)** − Cette instruction ajoute une PRIMARY KEY, ce qui signifie que les valeurs indexées doivent être uniques et ne peuvent pas être NULL.
  - **ALTER TABLE tbl_name ADD UNIQUE index_name (column_list)** − Cette instruction crée un index pour lequel les valeurs doivent être uniques (sauf pour les valeurs NULL, qui peuvent apparaître plusieurs fois).
  - **ALTER TABLE tbl_name ADD INDEX index_name (column_list)** − Cela ajoute un index ordinaire dans lequel toute valeur peut apparaître plus d'une fois.
  - **ALTER TABLE tbl_name ADD FULLTEXT index_name (column_list)** − Cela crée un index spécial FULLTEXT qui est utilisé à des fins de recherche de texte.

Le bloc de code suivant est un exemple pour ajouter un index dans une table existante.

``` sql
mysql> ALTER TABLE testalter_tbl ADD INDEX (c);
```

Vous pouvez supprimer un INDEX en utilisant la clause **DROP** avec la commande ALTER.

Essayez l'exemple suivant pour supprimer l'index créé ci-dessus.

``` sql
mysql> ALTER TABLE testalter_tbl DROP INDEX (c);

```

Vous pouvez supprimer un INDEX en utilisant la clause DROP avec la commande ALTER.

## ALTER Command to add and drop the PRIMARY KEY

Vous pouvez également ajouter une clé primaire de la même manière. Mais assurez-vous que la clé primaire fonctionne
sur les colonnes qui sont NOT NULL.

Le bloc de code suivant est un exemple pour ajouter la clé primaire dans une table existante. Il s'agit d'abord de 
rendre une colonne NOT NULL et ensuite de l'ajouter comme clé primaire.

``` sql
mysql> ALTER TABLE testalter_tbl MODIFY i INT NOT NULL;
mysql> ALTER TABLE testalter_tbl ADD PRIMARY KEY (i);
```

Vous pouvez utiliser la commande ALTER pour supprimer une clé primaire comme suit.

``` sql
mysql> ALTER TABLE testalter_tbl DROP PRIMARY KEY;
```

Pour supprimer un index qui n'est pas une PRIMARY KEY, vous devez spécifier le nom de l'index.

## Displaying INDEX Information

Vous pouvez utiliser la commande **SHOW INDEX** pour afficher la liste de tous les index associés à une table. La sortie au
format vertical (spécifié par \G) est souvent utile avec cette commande, afin d'éviter un long retour à la ligne.

Essayez l'exemple suivant :

``` sql
mysql> SHOW INDEX FROM table_name\G
```