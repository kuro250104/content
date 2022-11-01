## Introduction

Il peut arriver que vous ayez besoin d'une copie exacte d'une table et que **CREATE TABLE .... SELECT** ne 
vous convient pas car la copie doit inclure les mêmes index, les mêmes valeurs par défaut, etc.

Vous pouvez gérer cette situation en suivant les étapes indiquées ci-dessous :

  - Utilisez SHOW CREATE TABLE pour obtenir une instruction CREATE TABLE qui spécifie la structure de la table source, les index et tout le reste.
  - Modifiez l'instruction pour remplacer le nom de la table par celui de la table clone et exécutez l'instruction. Vous obtiendrez ainsi la table clone exacte.
  - Si vous souhaitez que le contenu de la table soit également copié, exécutez également une instruction INSERT INTO ... SELECT, également.

### Exemple

Essayez l'exemple suivant pour créer une table clone pour **tutorials_tbl**.

**Étape 1** - Obtenez la structure complète de la table.

``` sql
mysql> SHOW CREATE TABLE tutorials_tbl \G;
*************************** 1. row ***************************
      Table: tutorials_tbl
Create Table: CREATE TABLE `tutorials_tbl` (
   `tutorial_id` int(11) NOT NULL auto_increment,
   `tutorial_title` varchar(100) NOT NULL default '',
   `tutorial_author` varchar(40) NOT NULL default '',
   `submission_date` date default NULL,
   PRIMARY KEY  (`tutorial_id`),
   UNIQUE KEY `AUTHOR_INDEX` (`tutorial_author`)
) TYPE = MyISAM
1 row in set (0.00 sec)

ERROR:
No query specified
```

**Étape 2** - Renommez cette table et créez une autre table.

``` sql
mysql> CREATE TABLE clone_tbl (
   -> tutorial_id int(11) NOT NULL auto_increment,
   -> tutorial_title varchar(100) NOT NULL default '',
   -> tutorial_author varchar(40) NOT NULL default '',
   -> submission_date date default NULL,
   -> PRIMARY KEY  (tutorial_id),
   -> UNIQUE KEY AUTHOR_INDEX (tutorial_author)
-> ) TYPE = MyISAM;
Query OK, 0 rows affected (1.80 sec)
```

**Étape 3** - Après avoir exécuté l'étape 2, vous allez créer une table clone dans votre base de données. Si vous 
voulez copier les données de l'ancienne table, vous pouvez le faire en utilisant l'instruction INSERT INTO.... SELECT.

``` sql
mysql> INSERT INTO clone_tbl (tutorial_id,
   -> tutorial_title,
   -> tutorial_author,
   -> submission_date)
   
   -> SELECT tutorial_id,tutorial_title,
   -> tutorial_author,submission_date
   -> FROM tutorials_tbl;
Query OK, 3 rows affected (0.07 sec)
Records: 3  Duplicates: 0  Warnings: 0
```

Enfin, vous aurez un clone exact de la table que vous vouliez avoir.
