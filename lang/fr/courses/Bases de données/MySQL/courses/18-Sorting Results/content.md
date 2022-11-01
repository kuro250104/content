## Introduction

Nous avons vu la commande SQL SELECT pour extraire des données d'une table MySQL. Lorsque vous sélectionnez des lignes,
le serveur MySQL est libre de les renvoyer dans n'importe quel ordre, sauf si vous lui donnez des instructions contraires
en indiquant comment trier le résultat. Mais vous triez un ensemble de résultats en ajoutant une clause ORDER BY qui 
nomme la ou les colonnes que vous voulez trier.

### Syntaxe

Le bloc de code suivant est une syntaxe SQL générique de la commande SELECT avec la clause ORDER BY pour trier les
données d'une table MySQL.

``` sql
SELECT field1, field2,...fieldN table_name1, table_name2...
ORDER BY field1, [field2...] [ASC [DESC]]
```

   - Vous pouvez trier le résultat renvoyé sur n'importe quel champ, si ce champ est répertorié.
   - Vous pouvez trier le résultat sur plus d'un champ.
   - Vous pouvez utiliser le mot-clé ASC ou DESC pour obtenir le résultat dans l'ordre croissant ou décroissant. Par défaut, c'est l'ordre ascendant.
   - Vous pouvez utiliser la clause WHERE...LIKE de la manière habituelle pour poser une condition.

## Using ORDER BY clause at the Command Prompt

Cette opération utilise la commande SQL **SELECT** avec la clause **ORDER BY** pour récupérer les données de la
table MySQL - tutorials_tbl.

### Exemple

Essayez l'exemple suivant, qui renvoie le résultat dans un ordre croissant.

``` sql
root@host# mysql -u root -p password;
Enter password:*******
mysql> use TUTORIALS;
Database changed
mysql> SELECT * from tutorials_tbl ORDER BY tutorial_author ASC
+-------------+----------------+-----------------+-----------------+
| tutorial_id | tutorial_title | tutorial_author | submission_date |
+-------------+----------------+-----------------+-----------------+
|      2      |  Learn MySQL   |     Abdul S     |    2007-05-24   |   
|      1      |   Learn PHP    |    John Poul    |    2007-05-24   |   
|      3      | JAVA Tutorial  |     Sanjay      |    2007-05-06   |   
+-------------+----------------+-----------------+-----------------+
3 rows in set (0.42 sec)

mysql>
```

Vérifiez tous les noms d'auteurs qui sont énumérés dans l'ordre croissant.

## Using ORDER BY clause inside a PHP Script

PHP utilise la fonction **mysqli query()** ou **mysql_query()** pour obtenir des enregistrements triés à partir d'une 
table MySQL. Cette fonction prend deux paramètres et renvoie TRUE en cas de succès ou FALSE en cas d'échec.

### Syntaxe

``` bash
$mysqli->query($sql,$resultmode)
```

  - $sql - Requis - Requête SQL pour obtenir des enregistrements triés d'une table.
  - $resultmode - Facultatif - Soit la constante MYSQLI_USE_RESULT ou MYSQLI_STORE_RESULT selon le comportement souhaité. Par défaut, MYSQLI_STORE_RESULT est utilisé.

#### Exemple

Essayez l'exemple suivant pour obtenir des enregistrements triés à partir d'une table.
Copiez et collez l'exemple suivant dans le fichier mysql_example.php.

``` html
<html>
   <head>
      <title>Sorting MySQL Table records</title>
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
   
         $sql = "SELECT tutorial_id, tutorial_title, tutorial_author, submission_date FROM tutorials_tbl order by tutorial_title asc";
		 
         $result = $mysqli->query($sql);
           
         if ($result->num_rows > 0) {
            while($row = $result->fetch_assoc()) {
               printf(
                  "Id: %s, Title: %s, Author: %s, Date: %d <br />", 
                  $row["tutorial_id"], 
                  $row["tutorial_title"], 
                  $row["tutorial_author"],
                  $row["submission_date"]
               );               
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

Accédez au fichier mysql_example.php déployé sur le serveur web apache et vérifiez la sortie.

``` sql
Connected successfully.
Id: 5, Title: Apache Tutorial, Author: Suresh, Date: 2021
Id: 2, Title: HTML Tutorial, Author: Mahesh, Date: 2021
Id: 1, Title: MySQL Tutorial, Author: Mahesh, Date: 2021
Id: 3, Title: PHP Tutorial, Author: Mahesh, Date: 2021
```