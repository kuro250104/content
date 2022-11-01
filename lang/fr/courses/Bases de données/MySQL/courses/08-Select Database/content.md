## Introduction

Une fois que vous êtes connecté au serveur MySQL, il est nécessaire de sélectionner une base de données avec laquelle 
travailler. En effet, il peut y avoir plusieurs bases de données disponibles sur le serveur MySQL.

## Selecting MySQL Database from the Command Prompt

Il est très simple de sélectionner une base de données à partir de l'invite mysql>. Vous pouvez utiliser la commande
SQL use pour sélectionner une base de données.

### Exemple

Voici un exemple pour sélectionner une base de données appelée **TUTORIALS** :

``` bash
[root@host]# mysql -u root -p
Enter password:******
mysql> use TUTORIALS;
Database changed
mysql> 
```

Maintenant, vous avez sélectionné la base de données TUTORIALS et toutes les opérations suivantes seront effectuées sur
la base de données TUTORIALS.

**NOTE** − Tous les noms des bases de données, des tables et des champs des tables sont sensibles à la casse. Vous
devez donc utiliser les noms appropriés lorsque vous donnez une commande SQL.

## Selecting a MySQL Database Using PHP Script

PHP utilise la fonction **mysqli_select_db** pour sélectionner la base de données sur laquelle les requêtes doivent
être effectuées. Cette fonction prend deux paramètres et retourne TRUE en cas de succès ou FALSE en cas d'échec.

### Syntaxe

``` bash
mysqli_select_db ( mysqli $link , string $dbname ) : bool
```

Paramètre et description :

  - **$link** - Requis - Un identifiant de lien retourné par mysqli_connect() ou mysqli_init().
  - **$dbname** - Obligatoire - Nom de la base de données à connecter.

### Exemple

Essayez l'exemple suivant pour sélectionner une base de données.

Copiez et collez l'exemple suivant en tant que mysql_example.php :

``` html
<html>
   <head>
      <title>Selecting MySQL Database</title>
   </head>
   <body>
   <?php
      $dbhost = 'localhost';
      $dbuser = 'root';
      $dbpass = 'root@123';
      $conn = mysqli_connect($dbhost, $dbuser, $dbpass);

      if(! $conn ) {
         die('Could not connect: ' . mysqli_error($conn));
      }
      echo 'Connected successfully<br />';
      $retval = mysqli_select_db( $conn, 'TUTORIALS' );
      if(! $retval ) {
         die('Could not select database: ' . mysqli_error($conn));
      }
      echo "Database TUTORIALS selected successfully\n";
      mysqli_close($conn);
   ?>
   </body>
</html>
```

### Sortie

Accédez au fichier mysql_example.php déployé sur le serveur web apache et vérifiez la sortie.

``` bash
Database TUTORIALS selected successfully
```