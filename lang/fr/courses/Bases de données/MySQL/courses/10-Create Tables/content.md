## Introduction

Pour commencer, la commande de création de table nécessite les détails suivants :

  - Nom de la table
  - Nom des champs
  - Définitions pour chaque champ

### Syntaxe

Voici une syntaxe SQL générique permettant de créer une table MySQL -

``` bash
CREATE TABLE table_name (column_name column_type);
```

Maintenant, nous allons créer la table suivante dans la base de données **TUTORIALS**.

``` sql
create table tutorials_tbl(
   tutorial_id INT NOT NULL AUTO_INCREMENT,
   tutorial_title VARCHAR(100) NOT NULL,
   tutorial_author VARCHAR(40) NOT NULL,
   submission_date DATE,
   PRIMARY KEY ( tutorial_id )
);
```

Ici, quelques points nécessitent une explication :

  - L'attribut de champ **NOT NULL** est utilisé parce que nous ne voulons pas que ce champ soit NULL. Ainsi, si un utilisateur tente de créer un enregistrement avec une valeur NULL, MySQL émettra une erreur.
  - L'attribut de champ **AUTO_INCREMENT** indique à MySQL d'aller de l'avant et d'ajouter le prochain numéro disponible au champ id.
  - Le mot clé **PRIMARY KEY** est utilisé pour définir une colonne comme clé primaire. Vous pouvez utiliser plusieurs colonnes séparées par une virgule pour définir une clé primaire.

## Creating Tables from Command Prompt

Il est facile de créer une table MySQL à partir de l'invite mysql>. Vous utiliserez la commande
SQL **CREATE TABLE** pour créer une table.

### Exemple

Voici un exemple, qui créera tutoriels_tbl :

``` sql
root@host# mysql -u root -p
Enter password:*******
mysql> use TUTORIALS;
Database changed
mysql> CREATE TABLE tutorials_tbl(
   -> tutorial_id INT NOT NULL AUTO_INCREMENT,
   -> tutorial_title VARCHAR(100) NOT NULL,
   -> tutorial_author VARCHAR(40) NOT NULL,
   -> submission_date DATE,
   -> PRIMARY KEY ( tutorial_id )
   -> );
Query OK, 0 rows affected (0.16 sec)
mysql>
```

**NOTE** − MySQL ne termine pas une commande tant que vous ne donnez pas un point-virgule ( ;) à la fin de la commande SQL.

## Creating Tables Using PHP Script

PHP utilise la fonction mysqli **query()** ou **mysql_query()** pour créer une table MySQL. Cette fonction prend deux paramètres et renvoie TRUE en cas de succès ou FALSE en cas d'échec.

### Syntaxe

``` bash
$mysqli->query($sql,$resultmode)
```

Paramètre et description :

  - **$sql** - Requis - Requête SQL pour créer une table MySQL.
  - **$resultmode** - Facultatif - Soit la constante MYSQLI_USE_RESULT ou MYSQLI_STORE_RESULT selon le comportement souhaité. Par défaut, MYSQLI_STORE_RESULT est utilisé.

### Exemple

Essayez l'exemple suivant pour créer une table.
Copiez et collez l'exemple suivant en tant que mysql_example.php :

``` html
<html>
   <head>
      <title>Creating MySQL Table</title>
   </head>
   <body>
      <?php
         $dbhost = 'localhost';
         $dbuser = 'root';
         $dbpass = 'root@123';
         $dbname = 'TUTORIALS';
         $mysqli = new mysqli($dbhost, $dbuser, $dbpass, $dbname);
         
         if($mysqli->connect_errno ) {
            printf("Connect failed: %s<br />", $mysqli->connect_error);
            exit();
         }
         printf('Connected successfully.<br />');
   
         $sql = "CREATE TABLE tutorials_tbl( ".
            "tutorial_id INT NOT NULL AUTO_INCREMENT, ".
            "tutorial_title VARCHAR(100) NOT NULL, ".
            "tutorial_author VARCHAR(40) NOT NULL, ".
            "submission_date DATE, ".
            "PRIMARY KEY ( tutorial_id )); ";
         if ($mysqli->query($sql)) {
            printf("Table tutorials_tbl created successfully.<br />");
         }
         if ($mysqli->errno) {
            printf("Could not create table: %s<br />", $mysqli->error);
         }

         $mysqli->close();
      ?>
   </body>
</html>
```

### Sortie

Accédez au fichier mysql_example.php déployé sur le serveur web apache et vérifiez la sortie.

``` bash
Connected successfully.
Table tutorials_tbl created successfully.
```
