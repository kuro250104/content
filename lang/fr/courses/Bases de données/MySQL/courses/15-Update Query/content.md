## Introduction

Il peut arriver que les données existantes dans une table MySQL soient modifiées. Vous pouvez le faire en 
utilisant la commande SQL **UPDATE**. Celle-ci modifiera la valeur de n'importe quel champ de n'importe quelle table MySQL.

### Syntaxe

Le bloc de code suivant présente une syntaxe SQL générique de la commande UPDATE pour modifier les données de la table MySQL :

``` sql
UPDATE table_name SET field1 = new-value1, field2 = new-value2
[WHERE Clause]
```

  - Vous pouvez mettre à jour un ou plusieurs champs à la fois.
  - Vous pouvez spécifier n'importe quelle condition en utilisant la clause WHERE.
  - Vous pouvez mettre à jour les valeurs d'une seule table à la fois.

La clause WHERE est très utile lorsque vous souhaitez mettre à jour les lignes sélectionnées dans une table.

## Updating Data from the Command Prompt

Cette opération utilise la commande SQL UPDATE avec la clause WHERE pour mettre à jour les données sélectionnées 
dans la table MySQL **tutorials_tbl**.

### Exemple

L'exemple suivant met à jour le champ **tutorial_title** pour un enregistrement dont l'identifiant tutorial_id est 3.

``` sql
root@host# mysql -u root -p password;
Enter password:*******

mysql> use TUTORIALS;
Database changed

mysql> UPDATE tutorials_tbl 
   -> SET tutorial_title = 'Learning JAVA' 
   -> WHERE tutorial_id = 3;
Query OK, 1 row affected (0.04 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql>
```

## Updating Data Using a PHP Script

PHP utilise la fonction **mysqli query()** ou **mysql_query()** pour mettre à jour les enregistrements d'une table MySQL.
Cette fonction prend deux paramètres et renvoie TRUE en cas de succès ou FALSE en cas d'échec.

### Syntaxe

``` bash
$mysqli->query($sql,$resultmode)
```

Paramètre et description :

  - **$sql** - Requis - Requête SQL pour mettre à jour les enregistrements dans une table MySQL.
  - **$resultmode** - Facultatif - Soit la constante MYSQLI_USE_RESULT ou MYSQLI_STORE_RESULT selon le comportement souhaité. Par défaut, MYSQLI_STORE_RESULT est utilisé.

### Exemple

Essayez l'exemple suivant pour mettre à jour un enregistrement dans un tableau -
Copiez et collez l'exemple suivant dans le fichier mysql_example.php.

``` html
<html>
   <head>
      <title>Updating MySQL Table</title>
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
		 
         if ($mysqli->query('UPDATE tutorials_tbl set tutorial_title = "Learning Java" where tutorial_id = 4')) {
            printf("Table tutorials_tbl updated successfully.<br />");
         }
         if ($mysqli->errno) {
            printf("Could not update table: %s<br />", $mysqli->error);
         }
   
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

Accédez au fichier mysql_example.php déployé sur le serveur web apache et vérifiez la sortie. 
Ici, nous avons saisi plusieurs enregistrements dans la table avant d'exécuter le script de sélection.

``` sql
Connected successfully.
Table tutorials_tbl updated successfully.
Id: 1, Title: MySQL Tutorial, Author: Mahesh, Date: 2021
Id: 2, Title: HTML Tutorial, Author: Mahesh, Date: 2021
Id: 3, Title: PHP Tutorial, Author: Mahesh, Date: 2021
Id: 4, Title: Learning Java, Author: Mahesh, Date: 2021
Id: 5, Title: Apache Tutorial, Author: Suresh, Date: 2021
```
