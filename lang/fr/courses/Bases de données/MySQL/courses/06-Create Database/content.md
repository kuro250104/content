## Introduction

### Create Database Using mysqladmin

Vous aurez besoin de privilèges spéciaux pour créer ou supprimer une base de données MySQL. Donc, en supposant que 
vous avez accès à l'utilisateur root, vous pouvez créer n'importe quelle base de données en utilisant le binaire 
mysql **mysqladmin**.

### Exemple

Voici un exemple simple pour créer une base de données appelée **TUTORIALS** :

``` bash
[root@host]# mysqladmin -u root -p create TUTORIALS
Enter password:******
```

Cela va créer une base de données MySQL appelée TUTORIALS.

## Create a Database using PHP Script

PHP utilise la fonction mysqli **query()** ou **mysql_query()** pour créer ou supprimer une base de données MySQL.
Cette fonction prend deux paramètres et renvoie TRUE en cas de succès ou FALSE en cas d'échec.

### Syntaxe

``` bash
$mysqli->query($sql,$resultmode)
```

Paramètre et description :

  - **$sql** - Requis - Requête SQL pour créer une base de données MySQL.
  - **$resultmode** - Facultatif - Soit la constante MYSQLI_USE_RESULT ou MYSQLI_STORE_RESULT selon le comportement souhaité. Par défaut, MYSQLI_STORE_RESULT est utilisé.

### Exemple

Essayez l'exemple suivant pour créer une base de données.

Copiez et collez l'exemple suivant en tant que mysql_example.php :

``` html
<html>
   <head><title>Creating MySQL Database</title></head>
   <body>
      <?php
         $dbhost = 'localhost';
         $dbuser = 'root';
         $dbpass = 'root@123';
         $mysqli = new mysqli($dbhost, $dbuser, $dbpass);
         
         if($mysqli->connect_errno ) {
            printf("Connect failed: %s<br />", $mysqli->connect_error);
            exit();
         }
         printf('Connected successfully.<br />');

         if ($mysqli->query("CREATE DATABASE TUTORIALS")) {
            printf("Database TUTORIALS created successfully.<br />");
         }
         if ($mysqli->errno) {
            printf("Could not create database: %s<br />", $mysqli->error);
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
Database TUTORIALS created successfully.
```
