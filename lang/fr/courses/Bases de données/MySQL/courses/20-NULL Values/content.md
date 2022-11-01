## Introduction

Nous avons vu la commande SQL **SELECT** avec la clause **WHERE** pour récupérer des données d'une table MySQL, mais 
lorsque nous essayons de donner une condition, qui compare la valeur du champ ou de la colonne à **NULL**, cela ne
fonctionne pas correctement.

Pour faire face à une telle situation, MySQL fournit trois opérateurs, à savoir

  - **IS NULL** − Cet opérateur renvoie vrai, si la valeur de la colonne est NULL.
  - **IS NOT NULL** − Cet opérateur renvoie vrai, si la valeur de la colonne n'est pas NULL.
  - **<=>** − Cet opérateur compare des valeurs, ce qui (contrairement à l'opérateur =) est vrai même pour deux valeurs NULL.

Les conditions impliquant **NULL** sont spéciales. Vous ne pouvez pas utiliser = NULL ou != NULL pour rechercher des
valeurs NULL dans les colonnes. Ces comparaisons échouent toujours car il est impossible de savoir si elles sont vraies ou non. 
Parfois, même NULL = NULL échoue.

Pour rechercher des colonnes qui sont ou ne sont pas NULL, utilisez IS NULL ou IS NOT NULL.

## Using NULL values at the Command Prompt

Supposons qu'il existe une table appelée tcount_tbl dans la base de données TUTORIALS et qu'elle contient deux colonnes,
à savoir tutorial_author et tutorial_count, où un tutorial_count NULL indique que la valeur est inconnue.

### Exemple

Essayez les exemples suivants :

``` sql
root@host# mysql -u root -p password;
Enter password:*******

mysql> use TUTORIALS;
Database changed

mysql> create table tcount_tbl
   -> (
   -> tutorial_author varchar(40) NOT NULL,
   -> tutorial_count  INT
   -> );
Query OK, 0 rows affected (0.05 sec)

mysql> INSERT INTO tcount_tbl
   -> (tutorial_author, tutorial_count) values ('mahran', 20);

mysql> INSERT INTO tcount_tbl
   -> (tutorial_author, tutorial_count) values ('mahnaz', NULL);

mysql> INSERT INTO tcount_tbl
   -> (tutorial_author, tutorial_count) values ('Jen', NULL);

mysql> INSERT INTO tcount_tbl
   -> (tutorial_author, tutorial_count) values ('Gill', 20);

mysql> SELECT * from tcount_tbl;
+-----------------+----------------+
| tutorial_author | tutorial_count |
+-----------------+----------------+
|     mahran      |       20       |
|     mahnaz      |      NULL      |
|      Jen        |      NULL      |
|     Gill        |       20       |
+-----------------+----------------+
4 rows in set (0.00 sec)

mysql>
```

Vous pouvez constater que = et != ne fonctionnent pas avec des valeurs NULL comme suit :

``` sql
mysql> SELECT * FROM tcount_tbl WHERE tutorial_count = NULL;
Empty set (0.00 sec)

mysql> SELECT * FROM tcount_tbl WHERE tutorial_count != NULL;
Empty set (0.01 sec)
```

Pour trouver les enregistrements où la colonne tutorial_count est ou n'est pas NULL, les requêtes doivent être écrites
comme indiqué dans le programme suivant.

``` sql 
mysql> SELECT * FROM tcount_tbl 
   -> WHERE tutorial_count IS NULL;
+-----------------+----------------+
| tutorial_author | tutorial_count |
+-----------------+----------------+
|     mahnaz      |      NULL      |
|      Jen        |      NULL      |
+-----------------+----------------+
2 rows in set (0.00 sec)
mysql> SELECT * from tcount_tbl 
   -> WHERE tutorial_count IS NOT NULL;
+-----------------+----------------+
| tutorial_author | tutorial_count |
+-----------------+----------------+
|     mahran      |       20       |
|     Gill        |       20       |
+-----------------+----------------+
2 rows in set (0.00 sec)
```

## Handling NULL Values in a PHP Script

Vous pouvez utiliser la condition **if...else** pour préparer une requête basée sur la valeur NULL.

L'exemple suivant prend le tutorial_count de l'extérieur et le compare ensuite avec la valeur disponible dans la table.

#### Exemple

Copiez et collez l'exemple suivant en tant que mysql_example.php.

``` html
<html>
   <head>
      <title>Handling NULL</title>
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
   
         if( isset($tutorial_count )) {
            $sql = 'SELECT tutorial_author, tutorial_count
               FROM  tcount_tbl
               WHERE tutorial_count = ' + $tutorial_count;
         } else {
            $sql = 'SELECT tutorial_author, tutorial_count
               FROM  tcount_tbl
               WHERE tutorial_count IS NULL';
         }
         $result = $mysqli->query($sql);
         if ($result->num_rows > 0) {
            while($row = $result->fetch_assoc()) {
               printf("Author: %s, Count: %d <br />",
                  $row["tutorial_author"], 
                  $row["tutorial_count"]);               
            }
         } else {
            printf('No record found.<br />');
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
No record found.
```


