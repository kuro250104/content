## Introduction

Si vous souhaitez supprimer un enregistrement d'une table MySQL, vous pouvez utiliser la commande
SQL **DELETE FROM**. Vous pouvez utiliser cette commande à l'invite mysql> ainsi que dans un script tel que PHP.

### Syntaxe

Le bloc de code suivant présente une syntaxe SQL générique de la commande DELETE pour supprimer des données d'une table MySQL.

``` sql
DELETE FROM table_name [WHERE Clause]
```

  - Si la clause WHERE n'est pas spécifiée, tous les enregistrements seront supprimés de la table MySQL donnée.
  - Vous pouvez spécifier n'importe quelle condition à l'aide de la clause WHERE.
  - Vous pouvez supprimer les enregistrements d'une seule table à la fois.

La clause WHERE est très utile lorsque vous souhaitez supprimer des lignes sélectionnées dans un tableau.

## Deleting Data from the Command Prompt

Cette opération utilise la commande SQL DELETE avec la clause WHERE pour supprimer les données sélectionnées 
dans la table MySQL - **tutorials_tbl**.

### Exemple

L'exemple suivant permet de supprimer un enregistrement de la **tutorial_tbl** dont le tutorial_id est 3.

``` sql
root@host# mysql -u root -p password;
Enter password:*******

mysql> use TUTORIALS;
Database changed

mysql> DELETE FROM tutorials_tbl WHERE tutorial_id=3;
Query OK, 1 row affected (0.23 sec)

mysql>
```

## Deleting Data Using a PHP Script

PHP utilise la fonction **mysqli query()** ou **mysql_query()** pour supprimer des enregistrements dans une table MySQL.
Cette fonction prend deux paramètres et renvoie TRUE en cas de succès ou FALSE en cas d'échec.

### Syntaxe

``` bash
$mysqli->query($sql,$resultmode)
```

Paramètre et description :

  - $sql - Requis - Requête SQL pour supprimer des enregistrements dans une table MySQL.
  - $resultmode - Facultatif - Soit la constante MYSQLI_USE_RESULT ou MYSQLI_STORE_RESULT selon le comportement souhaité. Par défaut, MYSQLI_STORE_RESULT est utilisé.

## Exemple

Essayez l'exemple suivant pour supprimer un enregistrement dans un tableau -
Copiez et collez l'exemple suivant dans le fichier mysql_example.php.

``` html
<html>
   <head>
      <title>Deleting MySQL Table record</title>
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
		 
         if ($mysqli->query('DELETE FROM tutorials_tbl where tutorial_id = 4')) {
            printf("Table tutorials_tbl record deleted successfully.<br />");
         }
         if ($mysqli->errno) {
            printf("Could not delete record from table: %s<br />", $mysqli->error);
         }
         $sql = "SELECT tutorial_id, tutorial_title, tutorial_author, submission_date 
            FROM tutorials_tbl";
		 
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

## Sortie

Accédez au fichier mysql_example.php déployé sur le serveur web apache et vérifiez la sortie. Ici, nous avons 
saisi plusieurs enregistrements dans la table avant d'exécuter le script de sélection.

``` sql
Connected successfully.
Table tutorials_tbl record deleted successfully.
Id: 1, Title: MySQL Tutorial, Author: Mahesh, Date: 2021
Id: 2, Title: HTML Tutorial, Author: Mahesh, Date: 2021
Id: 3, Title: PHP Tutorial, Author: Mahesh, Date: 2021
Id: 5, Title: Apache Tutorial, Author: Suresh, Date: 2021
```