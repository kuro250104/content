## Introduction

Nous avons vu la commande SQL **SELECT** pour extraire des données d'une table MySQL. Nous pouvons utiliser une clause 
conditionnelle appelée clause WHERE pour filtrer les résultats. À l'aide de cette **WHERE Clause**, nous pouvons
spécifier un critère de sélection pour sélectionner les enregistrements requis dans une table.

### Syntaxe

Le bloc de code suivant présente une syntaxe SQL générique de la commande SELECT avec la clause WHERE pour extraire
des données de la table MySQL.

``` sql
SELECT field1, field2,...fieldN table_name1, table_name2...
[WHERE condition1 [AND [OR]] condition2.....
```

  - Vous pouvez utiliser un ou plusieurs tableaux séparés par une virgule pour inclure diverses conditions à l'aide d'une clause WHERE, mais cette dernière est une partie facultative de la commande SELECT.
  - Vous pouvez spécifier n'importe quelle condition à l'aide de la clause WHERE.
  - Vous pouvez spécifier plus d'une condition en utilisant les opérateurs AND ou OR.
  - Une clause WHERE peut être utilisée avec la commande SQL DELETE ou UPDATE pour spécifier une condition.

La clause WHERE fonctionne comme une if condition dans n'importe quel langage de programmation. Cette clause est
utilisée pour comparer la valeur donnée avec la valeur du champ disponible dans une table MySQL. Si la valeur donnée 
de l'extérieur est égale à la valeur du champ disponible dans la table MySQL, alors cette ligne est retournée.

Voici la liste des opérateurs, qui peuvent être utilisés avec la clause WHERE.

Supposons que le champ A contient 10 et le champ B contient 20, alors.

| Operateur | Description                                                                                                                                         | Exemple |
|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------|-----|
| =         | Vérifie si les valeurs des deux opérandes sont égales ou non, si oui, alors la condition devient vraie.                                             | (A = B) n'est pas vrai.|
| !=        | Vérifie si les valeurs des deux opérandes sont égales ou non, si les valeurs ne sont pas égales alors la condition devient vraie.                   | (A != B) est vrai. |
| >         | Vérifie si la valeur de l'opérande de gauche est supérieure à la valeur de l'opérande de droite, si oui, alors la condition devient vraie.          | (A > B) n'est pas vrai. |
| <         | Vérifie si la valeur de l'opérande de gauche est inférieure à la valeur de l'opérande de droite, si oui, la condition devient vraie.                | (A < B) est vrai. |
| >=        | Vérifie si la valeur de l'opérande de gauche est supérieure ou égale à la valeur de l'opérande de droite, si oui, la condition devient vraie.       | (A >= B) n'est pas vrai. |
| <=        | Vérifie si la valeur de l'opérande de gauche est inférieure ou égale à la valeur de l'opérande de droite, si oui, alors la condition devient vraie. | (A <= B) est vrai. |


La clause WHERE est très utile lorsque vous souhaitez récupérer les lignes sélectionnées dans une table,
notamment lorsque vous utilisez **MySQL Join**. Les jointures sont abordées dans un autre chapitre.

Il est courant de rechercher des enregistrements en utilisant la **Primary Key** pour accélérer la recherche.

Si la condition donnée ne correspond à aucun enregistrement de la table, la requête ne renvoie aucune ligne.

## Fetching Data from the Command Prompt

Cette opération utilise la commande SQL SELECT avec la clause WHERE pour récupérer les données sélectionnées dans la table MySQL - tutorials_tbl.

### Exemple

L'exemple suivant renvoie tous les enregistrements de la table tutoriels_tbl pour lesquels le nom de l'auteur est Sanjay.

``` sql
root@host# mysql -u root -p password;
Enter password:*******
mysql> use TUTORIALS;
Database changed
mysql> SELECT * from tutorials_tbl WHERE tutorial_author = 'Sanjay';
+-------------+----------------+-----------------+-----------------+
| tutorial_id | tutorial_title | tutorial_author | submission_date |
+-------------+----------------+-----------------+-----------------+
|      3      | JAVA Tutorial  |      Sanjay     |    2007-05-21   |      
+-------------+----------------+-----------------+-----------------+
1 rows in set (0.01 sec)

mysql>
```

À moins d'effectuer une comparaison **LIKE** sur une chaîne de caractères, la comparaison n'est pas sensible à la casse.
Vous pouvez rendre votre recherche sensible à la casse en utilisant le mot-clé **BINARY**, comme suit : 

``` sql
root@host# mysql -u root -p password;
Enter password:*******
mysql> use TUTORIALS;
Database changed
mysql> SELECT * from tutorials_tbl \
   WHERE BINARY tutorial_author = 'sanjay';
Empty set (0.02 sec)

mysql>
```

## Fetching Data Using a PHP Script

PHP utilise la fonction **mysqli query()** ou **mysql_query()** pour sélectionner des enregistrements dans une table
MySQL en utilisant la clause where. Cette fonction prend deux paramètres et renvoie TRUE en cas de succès ou FALSE en cas d'échec.

## Syntaxe

``` bash
$mysqli->query($sql,$resultmode)
```

Paramètre et description :

  - **$sql** - Requis - Requête SQL pour sélectionner des enregistrements dans une table MySQL en utilisant la clause Where.
  - **$resultmode** - Facultatif - Soit la constante MYSQLI_USE_RESULT ou MYSQLI_STORE_RESULT selon le comportement souhaité. Par défaut, MYSQLI_STORE_RESULT est utilisé.

### Exemple

Essayez l'exemple suivant pour sélectionner un enregistrement à l'aide de la clause where d'une table.

Copiez et collez l'exemple suivant dans le fichier mysql_example.php.

``` html
<html>
   <head>
      <title>Using Where Clause</title>
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
            FROM tutorials_tbl where tutorial_author = "Mahesh"';
		 
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
```
