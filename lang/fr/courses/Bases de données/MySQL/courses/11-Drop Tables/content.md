## Introduction

Il est très facile de supprimer une table MySQL existante, mais vous devez être très prudent lorsque vous supprimez
une table existante car les données perdues ne seront pas récupérées après la suppression d'une table.

### Syntaxe

Voici une syntaxe SQL générique permettant de supprimer une table MySQL.

``` sql
DROP TABLE table_name ;
```

## Dropping Tables from the Command Prompt

Pour supprimer des tables à partir de l'invite de commande, nous devons exécuter la commande DROP TABLE SQL à l'invite 
mysql> prompt.

### Exemple

Le programme suivant est un exemple qui supprime le **tutoriel_tbl** :

``` bash
root@host# mysql -u root -p
Enter password:*******
mysql> use TUTORIALS;
Database changed
mysql> DROP TABLE tutorials_tbl
Query OK, 0 rows affected (0.8 sec)
mysql>
```

## Dropping Tables Using PHP Script

PHP utilise la fonction **mysqli query()** ou **mysql_query()** pour déposer une table MySQL. Cette fonction prend
deux paramètres et retourne TRUE en cas de succès ou FALSE en cas d'échec.

### Syntaxe

``` bash
$mysqli->query($sql,$resultmode)
```

Paramètre et description :

  - **$sql** - Requis - Requête SQL pour supprimer une table.
  - **$resultmode** - Facultatif - Soit la constante MYSQLI_USE_RESULT ou MYSQLI_STORE_RESULT selon le comportement souhaité. Par défaut, MYSQLI_STORE_RESULT est utilisé.

### Exemple

Essayez l'exemple suivant pour supprimer une table.
Copiez et collez l'exemple suivant en tant que mysql_example.php :

``` html
<html>
   <head><title>Dropping MySQL Table</title></head>
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
		 
         if ($mysqli->query("Drop Table tutorials_tbl")) {
            printf("Table tutorials_tbl dropped successfully.<br />");
         }
         if ($mysqli->errno) {
            printf("Could not drop table: %s<br />", $mysqli->error);
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
Table tutorials_tbl dropped successfully.
```