## Introduction

La commande SQL SELECT est utilisée pour extraire des données de la base de données MySQL. Vous pouvez utiliser cette 
commande à l'invite mysql> ainsi que dans tout script tel que PHP.

### Syntaxe

Voici la syntaxe SQL générique de la commande SELECT pour extraire des données de la table MySQL.

``` sql
SELECT field1, field2,...fieldN 
FROM table_name1, table_name2...
[WHERE Clause]
[OFFSET M ][LIMIT N]
```

  - Vous pouvez utiliser un ou plusieurs tableaux séparés par des virgules pour inclure diverses conditions à l'aide d'une clause WHERE, mais cette dernière est une partie facultative de la commande SELECT.
  - Vous pouvez extraire un ou plusieurs champs dans une seule commande SELECT.
  - Vous pouvez spécifier une étoile (*) à la place des champs. Dans ce cas, la commande SELECT renverra tous les champs.
  - Vous pouvez spécifier n'importe quelle condition à l'aide de la clause WHERE.
  - Vous pouvez spécifier un décalage en utilisant OFFSET à partir duquel SELECT commencera à renvoyer les enregistrements. Par défaut, le décalage commence à zéro.
  - Vous pouvez limiter le nombre de retours à l'aide de l'attribut LIMIT.

## Fetching Data from a Command Prompt

Cette opération utilise la commande SQL SELECT pour récupérer les données de la table MySQL tutorials_tbl.

### Exemple

L'exemple suivant renvoie tous les enregistrements de la table **tutoriels_tbl** :

``` sql
root@host# mysql -u root -p password;
Enter password:*******
mysql> use TUTORIALS;
Database changed
mysql> SELECT * from tutorials_tbl 
+-------------+----------------+-----------------+-----------------+
| tutorial_id | tutorial_title | tutorial_author | submission_date |
+-------------+----------------+-----------------+-----------------+
|           1 | Learn PHP      | John Poul       | 2007-05-21      |
|           2 | Learn MySQL    | Abdul S         | 2007-05-21      |
|           3 | JAVA Tutorial  | Sanjay          | 2007-05-21      |
+-------------+----------------+-----------------+-----------------+
3 rows in set (0.01 sec)

mysql>
```

## Fetching Data Using a PHP Script

PHP utilise la fonction **mysqli query()** ou **mysql_query()** pour sélectionner des enregistrements dans une 
table MySQL. Cette fonction prend deux paramètres et renvoie TRUE en cas de succès ou FALSE en cas d'échec.

### Syntaxe

``` bash
$mysqli->query($sql,$resultmode)
```

Paramètre et description : 

  - **$sql** - Requis - Requête SQL pour sélectionner les enregistrements d'une table MySQL.
  - **$resultmode** - Facultatif - Soit la constante MYSQLI_USE_RESULT ou MYSQLI_STORE_RESULT selon le comportement souhaité. Par défaut, MYSQLI_STORE_RESULT est utilisé.

### Exemple

Essayez l'exemple suivant pour sélectionner un enregistrement d'une table.
Copiez et collez l'exemple suivant dans le fichier mysql_example.php :

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
         $sql = "SELECT tutorial_id, tutorial_title, tutorial_author, submission_date FROM tutorials_tbl";
		 
         $result = $mysqli->query($sql);
           
         if ($result->num_rows > 0) {
            while($row = $result->fetch_assoc()) {
               printf("Id: %s, Title: %s, Author: %s, Date: %d <br />", 
                  $row["tutorial_id"], 
                  $row["tutorial_title"], 
                  $row["tutorial_author"],
                  $row["submission_date"]);               
            }
         } else {
            printf('No record found.<br />');
         }
         mysqli_free_result($result);
         $mysqli->close();
      ?>
   </body>
</html>
```

### Sortie

Accédez au fichier mysql_example.php déployé sur le serveur web apache et vérifiez la sortie. Ici, nous avons saisi
plusieurs enregistrements dans la table avant d'exécuter le script de sélection.

``` sql
Connected successfully.
Id: 1, Title: MySQL Tutorial, Author: Mahesh, Date: 2021
Id: 2, Title: HTML Tutorial, Author: Mahesh, Date: 2021
Id: 3, Title: PHP Tutorial, Author: Mahesh, Date: 2021
Id: 4, Title: Java Tutorial, Author: Mahesh, Date: 2021
Id: 5, Title: Apache Tutorial, Author: Suresh, Date: 2021
```