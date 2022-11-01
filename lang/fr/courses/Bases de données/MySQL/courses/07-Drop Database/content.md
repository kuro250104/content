## Introduction

## Drop a Database using mysqladmin

Vous devez disposer de privilèges spéciaux pour créer ou supprimer une base de données MySQL. Ainsi, en supposant 
que vous ayez accès à l'utilisateur root, vous pouvez créer n'importe quelle base de données en utilisant le
binaire mysql **mysqladmin**.

Faites attention lorsque vous supprimez une base de données car vous perdrez toutes les données disponibles
dans votre base.

Voici un exemple de suppression d'une base de données (TUTORIALS) créée dans le chapitre précédent.

``` bash
[root@host]# mysqladmin -u root -p drop TUTORIALS
Enter password:******
```

Cela vous donnera un avertissement et vous confirmera si vous voulez vraiment supprimer cette base de données ou non.

``` bash
Dropping the database is potentially a very bad thing to do.
Any data stored in the database will be destroyed.

Do you really want to drop the 'TUTORIALS' database [y/N] y
Database "TUTORIALS" dropped
```

## Drop Database using PHP Script

PHP utilise la fonction mysqli **query()** ou **mysql_query()** pour déposer une base de données MySQL. Cette fonction 
prend deux paramètres et renvoie TRUE en cas de succès ou FALSE en cas d'échec.


### Syntaxe

``` bash
$mysqli->query($sql,$resultmode)
```

Paramètre et description :

  - **$sql** - ( Requis ) - Requête SQL pour déposer une base de données MySQL.
  - **$resultmode** - ( Facultatif ) - Soit la constante MYSQLI_USE_RESULT ou MYSQLI_STORE_RESULT selon le comportement souhaité. Par défaut, MYSQLI_STORE_RESULT est utilisé.

### Exemple

Essayez l'exemple suivant pour déposer une base de données.

Copiez et collez l'exemple suivant comme mysql_example.php :

``` html
<html>
   <head><title>Dropping MySQL Database</title></head>
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

         if ($mysqli->query("Drop DATABASE TUTORIALS")) {
            printf("Database TUTORIALS dropped successfully.<br />");
         }
         if ($mysqli->errno) {
            printf("Could not drop database: %s<br />", $mysqli->error);
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
Database TUTORIALS dropped successfully.
```