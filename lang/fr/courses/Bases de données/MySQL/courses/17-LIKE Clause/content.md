## Introduction

Nous avons vu la commande SQL **SELECT** pour extraire des données de la table MySQL. Nous pouvons également utiliser 
une clause conditionnelle appelée clause **WHERE** pour sélectionner les enregistrements requis.

Une clause WHERE avec le signe 'égal à' (=) fonctionne bien lorsque nous voulons faire une correspondance exacte. 
Par exemple, si "tutorial_author = 'Sanjay'". Mais il peut y avoir une exigence où nous voulons filtrer tous les
résultats où le nom tutorial_author doit contenir "jay". Ceci peut être traité en utilisant SQL **LIKE Clause**
avec la clause WHERE.

Si la clause SQL LIKE est utilisée avec le caractère %, elle fonctionnera comme un métacaractère (*) comme sous UNIX, 
en listant tous les fichiers ou répertoires à l'invite de commande. Sans le caractère %, la clause LIKE est très 
similaire au signe égal à avec la clause WHERE.

### Syntaxe

Le bloc de code suivant présente une syntaxe SQL générique de la commande SELECT avec la clause LIKE pour
extraire des données d'une table MySQL.

``` sql
SELECT field1, field2,...fieldN table_name1, table_name2...
WHERE field1 LIKE condition1 [AND [OR]] filed2 = 'somevalue'
```

  - Vous pouvez spécifier n'importe quelle condition à l'aide de la clause WHERE.
  - Vous pouvez utiliser la clause LIKE en même temps que la clause WHERE.
  - Vous pouvez utiliser la clause LIKE à la place du signe égal à.
  - Lorsque la clause LIKE est utilisée avec le signe %, elle fonctionne comme une recherche par métacaractères.
  - Vous pouvez spécifier plus d'une condition en utilisant les opérateurs AND ou OR.
  - Une clause WHERE...LIKE peut être utilisée avec la commande SQL DELETE ou UPDATE pour spécifier une condition.

## Using the LIKE clause at the Command Prompt

Cette opération utilise la commande SQL SELECT avec la clause WHERE...LIKE pour récupérer les données sélectionnées 
dans la table MySQL - **tutorials_tbl**.

### Exemple

L'exemple suivant renvoie tous les enregistrements de la table tutoriels_tbl pour lesquels le nom de l'auteur 
se termine par jay.

``` sql
root@host# mysql -u root -p password;
Enter password:*******
mysql> use TUTORIALS;
Database changed
mysql> SELECT * from tutorials_tbl 
   -> WHERE tutorial_author LIKE '%jay';
+-------------+----------------+-----------------+-----------------+
| tutorial_id | tutorial_title | tutorial_author | submission_date |
+-------------+----------------+-----------------+-----------------+
|      3      |  JAVA Tutorial |     Sanjay      |    2007-05-21   |   
+-------------+----------------+-----------------+-----------------+
1 rows in set (0.01 sec)

mysql>
```

## Using LIKE clause inside PHP Script

PHP utilise la fonction **mysqli query()** ou **mysql_query()** pour sélectionner des enregistrements dans une table
MySQL en utilisant la clause Like. Cette fonction prend deux paramètres et renvoie TRUE en cas de succès ou 
FALSE en cas d'échec.

### Syntaxe

``` bsah
$mysqli->query($sql,$resultmode)
```

Paramètre et description :

  - $sql - Requis - Requête SQL pour sélectionner des enregistrements dans une table MySQL en utilisant la clause Like.
  - $resultmode - Facultatif - Soit la constante MYSQLI_USE_RESULT ou MYSQLI_STORE_RESULT selon le comportement souhaité. Par défaut, MYSQLI_STORE_RESULT est utilisé.

### Exemple

Essayez l'exemple suivant pour sélectionner un enregistrement à l'aide de la clause like dans une table.
Copiez et collez l'exemple suivant dans le fichier mysql_example.php.

``` html
<html>
   <head>
      <title>Using Like Clause</title>
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
   
         $sql = 'SELECT tutorial_id, tutorial_title, tutorial_author, submission_date 
            FROM tutorials_tbl where tutorial_author like "Mah%"';
		 
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

Accédez au fichier mysql_example.php déployé sur le serveur web apache et vérifiez la sortie. Ici, nous avons 
saisi plusieurs enregistrements dans la table avant d'exécuter le script de sélection.

``` sql
Connected successfully.
Id: 1, Title: MySQL Tutorial, Author: Mahesh, Date: 2021
Id: 2, Title: HTML Tutorial, Author: Mahesh, Date: 2021
Id: 3, Title: PHP Tutorial, Author: Mahesh, Date: 2021
```