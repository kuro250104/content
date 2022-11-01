## Introduction

La commande MySQL **ALTER** est très utile lorsque vous voulez changer le nom de votre table, un champ de la table ou
si vous voulez ajouter ou supprimer une colonne existante dans une table.

Commençons par la création d'une table appelée testalter_tbl.

``` sql
root@host# mysql -u root -p password;
Enter password:*******

mysql> use TUTORIALS;
Database changed

mysql> create table testalter_tbl
   -> (
   -> i INT,
   -> c CHAR(1)
   -> );
Query OK, 0 rows affected (0.05 sec)
mysql> SHOW COLUMNS FROM testalter_tbl;
+-------+---------+------+-----+---------+-------+
| Field |  Type   | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
|   i   | int(11) | YES  |     |   NULL  |       |
|   c   | char(1) | YES  |     |   NULL  |       |
+-------+---------+------+-----+---------+-------+
2 rows in set (0.00 sec)
```

## Dropping, Adding or Repositioning a Column

Si vous voulez supprimer une colonne existante i de la table MySQL ci-dessus, vous utiliserez la clause **DROP**
avec la commande **ALTER**, comme indiqué ci-dessous.

``` sql
mysql> ALTER TABLE testalter_tbl  DROP i;
```

Une clause DROP ne fonctionnera pas si la colonne est la seule qui reste dans la table.

Pour ajouter une colonne, utilisez ADD et spécifiez la définition de la colonne. L'instruction suivante 
restaure la colonne i dans la table testalter_tbl.

``` sql
mysql> ALTER TABLE testalter_tbl ADD i INT;
```

Après avoir émis cette instruction, testalter contiendra les deux mêmes colonnes que lorsque vous avez créé la table,
mais n'aura pas la même structure. Ceci est dû au fait que de nouvelles colonnes sont ajoutées à la fin de la table par
défaut. Ainsi, même si i était à l'origine la première colonne de mytbl, c'est maintenant la dernière.

``` sql
mysql> SHOW COLUMNS FROM testalter_tbl;
+-------+---------+------+-----+---------+-------+
| Field |  Type   | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
|   c   | char(1) | YES  |     |   NULL  |       |
|   i   | int(11) | YES  |     |   NULL  |       |
+-------+---------+------+-----+---------+-------+
2 rows in set (0.00 sec)
```

Pour indiquer que vous souhaitez qu'une colonne occupe une position spécifique dans le tableau, utilisez FIRST pour en 
faire la première colonne ou **AFTER col_name** pour indiquer que la nouvelle colonne doit être placée après le nom_col.

Essayez les instructions **ALTER TABLE** suivantes, en utilisant **SHOW COLUMNS** après chacune d'entre elles pour voir 
l'effet de chacune d'entre elles...

``` sql
ALTER TABLE testalter_tbl DROP i;
ALTER TABLE testalter_tbl ADD i INT FIRST;
ALTER TABLE testalter_tbl DROP i;
ALTER TABLE testalter_tbl ADD i INT AFTER c;
```

Les spécificateurs FIRST et AFTER ne fonctionnent qu'avec la clause ADD. Cela signifie que si vous souhaitez 
repositionner une colonne existante dans une table, vous devez d'abord la **DROP**, puis **ADD** à la nouvelle position.

## Altering (Changing) a Column Definition or a Name

Pour modifier la définition d'une colonne, utilisez la clause **MODIFY** ou **CHANGE** avec la commande ALTER.

Par exemple, pour changer la colonne c de CHAR(1) en CHAR(10), vous pouvez utiliser la commande suivante :

``` sql
mysql> ALTER TABLE testalter_tbl MODIFY c CHAR(10);
```

Avec **CHANGE**, la syntaxe est un peu différente. Après le mot-clé CHANGE, vous nommez la colonne que vous voulez 
modifier, puis vous spécifiez la nouvelle définition, qui inclut le nouveau nom.

Essayez l'exemple suivant :

``` sql
mysql> ALTER TABLE testalter_tbl CHANGE i j BIGINT;
```

Si vous utilisez maintenant CHANGE pour reconvertir j de BIGINT en INT sans changer le nom de la colonne, l'instruction sera la suivante :

``` sql
mysql> ALTER TABLE testalter_tbl CHANGE j j INT;
```

**L'effet de ALTER TABLE sur les attributs de valeur nulle et par défaut** - Lorsque vous MODIFIEZ ou CHANGEZ 
une colonne, vous pouvez également spécifier si la colonne peut ou non contenir des valeurs NULL et quelle est sa 
valeur par défaut. En fait, si vous ne le faites pas, MySQL attribue automatiquement des valeurs pour ces attributs.

Le bloc de code suivant est un exemple, où la colonne **NOT NULL** aura la valeur 100 par défaut.

``` sql
mysql> ALTER TABLE testalter_tbl 
   -> MODIFY j BIGINT NOT NULL DEFAULT 100;
```

Si vous n'utilisez pas la commande ci-dessus, MySQL remplira les valeurs NULL dans toutes les colonnes.

## Altering (Changing) a Column's Default Value

Vous pouvez modifier une valeur par défaut pour n'importe quelle colonne en utilisant la commande **ALTER**.

Essayez l'exemple suivant.

``` sql
mysql> ALTER TABLE testalter_tbl ALTER i SET DEFAULT 1000;
mysql> SHOW COLUMNS FROM testalter_tbl;
+-------+---------+------+-----+---------+-------+
| Field |  Type   | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
|   c   | char(1) | YES  |     |   NULL  |       |
|   i   | int(11) | YES  |     |   1000  |       |
+-------+---------+------+-----+---------+-------+
2 rows in set (0.00 sec)
```

Vous pouvez supprimer la contrainte par défaut de toute colonne en utilisant la clause DROP avec la commande **ALTER**.

``` sql
mysql> ALTER TABLE testalter_tbl ALTER i DROP DEFAULT;
mysql> SHOW COLUMNS FROM testalter_tbl;
+-------+---------+------+-----+---------+-------+
| Field |  Type   | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
|   c   | char(1) | YES  |     |   NULL  |       |
|   i   | int(11) | YES  |     |   NULL  |       |
+-------+---------+------+-----+---------+-------+
2 rows in set (0.00 sec)
```

## Altering (Changing) a Table Type

Vous pouvez utiliser un type de table en utilisant la clause **TYPE** avec la commande ALTER. Essayez l'exemple suivant pour changer le type de table testalter_tbl en MYISAM.

Pour connaître le type actuel d'une table, utilisez l'instruction **SHOW TABLE STATUS**.

``` sql
mysql> ALTER TABLE testalter_tbl TYPE = MYISAM;
mysql>  SHOW TABLE STATUS LIKE 'testalter_tbl'\G
*************************** 1. row ****************
           Name: testalter_tbl
           Type: MyISAM
     Row_format: Fixed
           Rows: 0
 Avg_row_length: 0
    Data_length: 0
Max_data_length: 25769803775
   Index_length: 1024
      Data_free: 0
 Auto_increment: NULL
    Create_time: 2007-06-03 08:04:36
    Update_time: 2007-06-03 08:04:36
     Check_time: NULL
 Create_options:
        Comment:
1 row in set (0.00 sec)
```

## Renaming (Altering) a Table

Pour renommer une table, utilisez l'option **RENAME** de l'instruction **ALTER TABLE**.

Essayez l'exemple suivant pour renommer **testalter_tbl** en **alter_tbl**.

``` sql
mysql> ALTER TABLE testalter_tbl RENAME TO alter_tbl;
```

Vous pouvez utiliser la commande ALTER pour créer et déposer la commande INDEX sur un fichier MySQL.
Nous discuterons en détail de cette commande dans le chapitre suivant.
