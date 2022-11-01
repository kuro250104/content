## Introduction

## Obtaining and Using MySQL Metadata

Il existe trois types d'informations que vous souhaitez obtenir de MySQL.

  - **Information about the result of queries** − Il s'agit du nombre d'enregistrements affectés par toute instruction SELECT, UPDATE ou DELETE.
  - **Information about the tables and databases** − Il s'agit d'informations relatives à la structure des tables et des bases de données.
  - **Information about the MySQL server** − Il s'agit notamment de l'état du serveur de la base de données, du numéro de version, etc.

Il est très facile d'obtenir toutes ces informations à l'invite MySQL, mais en utilisant les API PERL ou PHP, nous devons 
appeler explicitement diverses API pour obtenir toutes ces informations.

## Obtaining the Number of Rows Affected by a Query

Voyons maintenant comment obtenir ces informations.

### Exemple PERL

Dans les scripts DBI, le nombre de lignes concernées est renvoyé par la commande **do( )** ou par la commande
**execute( )**, selon la façon dont vous exécutez la requête.

``` php
# Method 1
# execute $query using do( )
my $count = $dbh->do ($query);
# report 0 rows if an error occurred
printf "%d rows were affected\n", (defined ($count) ? $count : 0);

# Method 2
# execute query using prepare( ) plus execute( )
my $sth = $dbh->prepare ($query);
my $count = $sth->execute ( );
printf "%d rows were affected\n", (defined ($count) ? $count : 0);
```

### Exemple PHP

En PHP, invoquez la fonction **mysql_affected_rows( )** pour connaître le nombre de lignes modifiées par une requête.

``` php
$result_id = mysql_query ($query, $conn_id);
# report 0 rows if the query failed
$count = ($result_id ? mysql_affected_rows ($conn_id) : 0);
print ("$count rows were affected\n");
```

## Listing Tables and Databases

Il est très facile de répertorier toutes les bases de données et les tables disponibles sur un serveur de base de 
données. Votre résultat peut être nul si vous ne disposez pas des privilèges suffisants.

Outre la méthode présentée dans le bloc de code suivant, vous pouvez utiliser les requêtes **SHOW TABLES**
ou **SHOW DATABASES** pour obtenir la liste des tables ou des bases de données en PHP ou en PERL.

### Exemple PERL

``` php
# Get all the tables available in current database.
my @tables = $dbh->tables ( );

foreach $table (@tables ){
   print "Table Name $table\n";
}
```

### Exemple PHP

Essayez l'exemple suivant pour obtenir des informations sur la base de données.
Copiez et collez l'exemple suivant en tant que mysql_example.php :

``` html
<html>
   <head>
      <title>Getting MySQL Database Info</title>
   </head>
   <body>
      <?php
         $dbhost = 'localhost';
         $dbuser = 'root';
         $dbpass = 'root@123';
         $dbname = 'TUTORIALS';
         $mysqli = new mysqli($dbhost, $dbuser, $dbpass, $dbname);
         $tutorial_count = null;
		 
         if($mysqli->connect_errno ) {
            printf("Connect failed: %s<br />", $mysqli->connect_error);
            exit();
         }
         printf('Connected successfully.<br />');
		 
         if ($result = mysqli_query($mysqli, "SELECT DATABASE()")) {
            $row = mysqli_fetch_row($result);
            printf("Default database is %s<br />", $row[0]);
            mysqli_free_result($result);
         }
         $mysqli->close();
      ?>
   </body>
</html>
```

## Sortie

Accédez au fichier mysql_example.php déployé sur le serveur web apache et vérifiez la sortie.

``` bash
Connected successfully.
Default database is tutorials
```

## Getting Server Metadata

Il existe quelques commandes importantes dans MySQL qui peuvent être exécutées soit à l'invite MySQL, soit 
à l'aide d'un script comme PHP, pour obtenir diverses informations importantes sur le serveur de base de données.

Command & Description :

  - **SELECT VERSION( )** - Chaîne de la version du serveur
  - **SELECT DATABASE( )** - Nom de la base de données actuelle (vide si aucune)
  - **SELECT USER( )** - Nom d'utilisateur actuel
  - **SHOW STATUS** - Indicateurs d'état du serveur
  - **SHOW VARIABLES** - Variables de configuration du serveur
