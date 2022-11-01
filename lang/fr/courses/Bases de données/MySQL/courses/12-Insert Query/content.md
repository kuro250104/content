## Introduction

Pour insérer des données dans une table MySQL, vous devez utiliser la commande SQL **INSERT INTO**. Vous
pouvez insérer des données dans la table MySQL en utilisant l'invite mysql> ou en utilisant un script comme PHP.

### Syntaxe

Voici une syntaxe SQL générique de la commande INSERT INTO permettant d'insérer des données dans la table MySQL :

``` sql
INSERT INTO table_name ( field1, field2,...fieldN )
   VALUES
   ( value1, value2,...valueN );
```

Pour insérer des types de données de type chaîne, il est nécessaire de placer toutes les valeurs entre guillemets 
doubles ou simples. Par exemple "**valeur**".

## Inserting Data from the Command Prompt

Pour insérer des données à partir de l'invite de commande, nous allons utiliser la commande SQL INSERT INTO pour 
insérer des données dans la table MySQL tutorials_tbl.

### Exemple

L'exemple suivant créera 3 enregistrements dans la table **tutoriels_tbl** :

``` sql
root@host# mysql -u root -p password;
Enter password:*******
mysql> use TUTORIALS;
Database changed

mysql> INSERT INTO tutorials_tbl 
   ->(tutorial_title, tutorial_author, submission_date)
   ->VALUES
   ->("Learn PHP", "John Poul", NOW());
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO tutorials_tbl
   ->(tutorial_title, tutorial_author, submission_date)
   ->VALUES
   ->("Learn MySQL", "Abdul S", NOW());
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO tutorials_tbl
   ->(tutorial_title, tutorial_author, submission_date)
   ->VALUES
   ->("JAVA Tutorial", "Sanjay", '2007-05-06');
Query OK, 1 row affected (0.01 sec)
mysql>
```

**NOTE** − Veuillez noter que tous les signes de flèche (->) ne font pas partie de la commande SQL. Ils indiquent 
une nouvelle ligne et sont créés automatiquement par l'invite MySQL en appuyant sur la touche entrée sans donner 
un point-virgule à la fin de chaque ligne de la commande.

Dans l'exemple ci-dessus, nous n'avons pas fourni de tutorial_id car au moment de la création de la table, nous avions
donné l'option AUTO_INCREMENT pour ce champ. MySQL se charge donc d'insérer automatiquement ces ID. Ici, **NOW()** est une
fonction MySQL, qui renvoie la date et l'heure actuelles.

## Inserting Data Using a PHP Script

PHP utilise la fonction **mysqli query()** ou **mysql_query()** pour insérer un enregistrement dans une table MySQL.
Cette fonction prend deux paramètres et renvoie TRUE en cas de succès ou FALSE en cas d'échec.

### Syntaxe

``` bash
$mysqli->query($sql,$resultmode)
```

Paramètre et description :

  - **$sql** - Requis - Requête SQL pour insérer un enregistrement dans une table.
  - **$resultmode** - Facultatif - Soit la constante MYSQLI_USE_RESULT ou MYSQLI_STORE_RESULT selon le comportement souhaité. Par défaut, MYSQLI_STORE_RESULT est utilisé.

### Exemple

Cet exemple va prendre trois paramètres de l'utilisateur et les insérer dans la table MySQL.
Copiez et collez l'exemple suivant en tant que mysql_example.php :

``` html
<html>
   <head><title>Add New Record in MySQL Database</title></head>
   <body>
      <?php
         if(isset($_POST['add'])) {
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

            if(! get_magic_quotes_gpc() ) {
               $tutorial_title = addslashes ($_POST['tutorial_title']);
               $tutorial_author = addslashes ($_POST['tutorial_author']);
            } else {
               $tutorial_title = $_POST['tutorial_title'];
               $tutorial_author = $_POST['tutorial_author'];
            }

            $submission_date = $_POST['submission_date'];
            $sql = "INSERT INTO tutorials_tbl ".
               "(tutorial_title,tutorial_author, submission_date) "."VALUES ".
               "('$tutorial_title','$tutorial_author','$submission_date')";
           
            if ($mysqli->query($sql)) {
               printf("Record inserted successfully.<br />");
            }
            if ($mysqli->errno) {
               printf("Could not insert record into table: %s<br />", $mysqli->error);
            }
            $mysqli->close();
         } else {
      ?>  
      <form method = "post" action = "<?php $_PHP_SELF ?>">
         <table width = "600" border = "0" cellspacing = "1" cellpadding = "2">
            <tr>
               <td width = "250">Tutorial Title</td>
               <td><input name = "tutorial_title" type = "text" id = "tutorial_title"></td>
            </tr>         
            <tr>
               <td width = "250">Tutorial Author</td>
               <td><input name = "tutorial_author" type = "text" id = "tutorial_author"></td>
            </tr>         
            <tr>
               <td width = "250">Submission Date [   yyyy-mm-dd ]</td>
               <td><input name = "submission_date" type = "text" id = "submission_date"></td>
            </tr>      
            <tr>
               <td width = "250"> </td>
               <td></td>
            </tr>         
            <tr>
               <td width = "250"> </td>
               <td><input name = "add" type = "submit" id = "add"  value = "Add Tutorial"></td>
            </tr>
         </table>
      </form>
   <?php
      }
   ?>
   </body>
</html>
```

### Sortie

Accédez au fichier mysql_example.php déployé sur le serveur web apache, entrez les détails et vérifiez la sortie
en soumettant le formulaire.

``` bash
Record inserted successfully.
```

Lors d'une insertion de données, il est préférable d'utiliser la fonction get_magic_quotes_gpc() pour vérifier si la
configuration actuelle de la citation magique est définie ou non. Si cette fonction renvoie false, utilisez alors la
fonction addslashes() pour ajouter des barres obliques avant les guillemets.

Vous pouvez mettre de nombreuses validations pour vérifier si les données saisies sont correctes ou non et prendre les
mesures appropriées.
