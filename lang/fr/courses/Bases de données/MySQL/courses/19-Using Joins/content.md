## Introduction
Dans les chapitres précédents, nous avons obtenu des données d'une seule table à la fois. C'est suffisant pour les 
prises simples, mais dans la plupart des utilisations réelles de MySQL, vous aurez souvent besoin d'obtenir des données
de plusieurs tables dans une seule requête.

Vous pouvez utiliser plusieurs tables dans une seule requête SQL. L'acte de joindre dans MySQL fait référence à la
fusion de deux ou plusieurs tables en une seule.

Vous pouvez utiliser des JOINS dans les instructions SELECT, UPDATE et DELETE pour joindre les tables MySQL. Nous 
allons voir un exemple de LEFT JOIN qui est également différent du simple JOIN MySQL.

## Using Joins at the Command Prompt

Supposons que nous ayons deux tables tcount_tbl et tutorials_tbl, dans TUTORIALS. Maintenant, regardez les exemples 
donnés ci-dessous.

### Exemple

Les exemples suivants :

``` sql
root@host# mysql -u root -p password;
Enter password:*******
mysql> use TUTORIALS;
Database changed
mysql> SELECT * FROM tcount_tbl;
+-----------------+----------------+
| tutorial_author | tutorial_count |
+-----------------+----------------+
|      mahran     |       20       |     
|      mahnaz     |      NULL      |        
|       Jen       |      NULL      |          
|      Gill       |       20       |          
|    John Poul    |        1       |      
|     Sanjay      |        1       |        
+-----------------+----------------+
6 rows in set (0.01 sec)
mysql> SELECT * from tutorials_tbl;
+-------------+----------------+-----------------+-----------------+
| tutorial_id | tutorial_title | tutorial_author | submission_date |
+-------------+----------------+-----------------+-----------------+
|      1      |  Learn PHP     |     John Poul   |    2007-05-24   |   
|      2      |  Learn MySQL   |      Abdul S    |    2007-05-24   |   
|      3      | JAVA Tutorial  |      Sanjay     |    2007-05-06   |   
+-------------+----------------+-----------------+-----------------+
3 rows in set (0.00 sec)
mysql>
```

Maintenant nous pouvons écrire une requête SQL pour joindre ces deux tables. Cette requête sélectionnera tous les
auteurs de la table tutorials_tbl et récupérera le nombre correspondant de tutoriels de la table tcount_tbl.

``` sql
mysql> SELECT a.tutorial_id, a.tutorial_author, b.tutorial_count
   -> FROM tutorials_tbl a, tcount_tbl b
   -> WHERE a.tutorial_author = b.tutorial_author;
+-------------+-----------------+----------------+
| tutorial_id | tutorial_author | tutorial_count |
+-------------+-----------------+----------------+
|      1      |    John Poul    |        1       |
|      3      |     Sanjay      |        1       |
+-------------+-----------------+----------------+
2 rows in set (0.01 sec)
mysql>
```

## Using Joins in a PHP Script

PHP utilise la fonction **mysqli query()** ou **mysql_query()** pour récupérer les enregistrements d'une table MySQL en
utilisant des jointures. Cette fonction prend deux paramètres et renvoie TRUE en cas de succès ou FALSE en cas d'échec.

### Syntaxe

``` bash
$mysqli->query($sql,$resultmode)
```

Paramètre et description :

  - $sql - Requis - Requête SQL pour obtenir des enregistrements de plusieurs tables en utilisant la jointure.
  - $resultmode - Facultatif - Soit la constante MYSQLI_USE_RESULT ou MYSQLI_STORE_RESULT selon le comportement souhaité. Par défaut, MYSQLI_STORE_RESULT est utilisé.

Tout d'abord, créez une table dans MySQL en utilisant le script suivant et insérez deux enregistrements.

``` sql
create table tcount_tbl(
   tutorial_author VARCHAR(40) NOT NULL,
   tutorial_count int
);

insert into tcount_tbl values('Mahesh', 3);
insert into tcount_tbl values('Suresh', 1);
```

### Exemple

Essayez l'exemple suivant pour obtenir des enregistrements de deux tables en utilisant la fonction Join. -
Copiez et collez l'exemple suivant dans le fichier mysql_example.php :

``` html
<html>
   <head>
      <title>Using joins on MySQL Tables</title>
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
   
         $sql = 'SELECT a.tutorial_id, a.tutorial_author, b.tutorial_count
            FROM tutorials_tbl a, tcount_tbl b WHERE a.tutorial_author = b.tutorial_author';
		 
         $result = $mysqli->query($sql);
           
         if ($result->num_rows > 0) {
            while($row = $result->fetch_assoc()) {
               printf("Id: %s, Author: %s, Count: %d <br />", 
                  $row["tutorial_id"], 
                  $row["tutorial_author"], 
                  $row["tutorial_count"]);               
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
Id: 1, Author: Mahesh, Count: 3
Id: 2, Author: Mahesh, Count: 3
Id: 3, Author: Mahesh, Count: 3
Id: 5, Author: Suresh, Count: 1
```

## MySQL LEFT JOIN

Une jointure gauche MySQL est différente d'une jointure simple. Un LEFT JOIN MySQL donne une considération supplémentaire
à la table qui se trouve à gauche.

Si je fais un **LEFT JOIN**, j'obtiens tous les enregistrements qui correspondent de la même manière et EN PLUS, 
j'obtiens un enregistrement supplémentaire pour chaque enregistrement non correspondant dans la table de gauche de la jointure : ainsi, je m'assure (dans mon exemple) que chaque AUTEUR est mentionné.

### Exemple

Essayez l'exemple suivant pour comprendre le LEFT JOIN.

``` sql
root@host# mysql -u root -p password;
Enter password:*******
mysql> use TUTORIALS;
Database changed
mysql> SELECT a.tutorial_id, a.tutorial_author, b.tutorial_count
   -> FROM tutorials_tbl a LEFT JOIN tcount_tbl b
   -> ON a.tutorial_author = b.tutorial_author;
+-------------+-----------------+----------------+
| tutorial_id | tutorial_author | tutorial_count |
+-------------+-----------------+----------------+
|      1      |    John Poul    |       1        |
|      2      |     Abdul S     |      NULL      |
|      3      |     Sanjay      |       1        |
+-------------+-----------------+----------------+
3 rows in set (0.02 sec)
```

Vous devez vous exercer davantage pour vous familiariser avec les JOINS. Il s'agit d'un concept un peu complexe dans
MySQL/SQL et il deviendra plus clair en faisant des exemples réels.