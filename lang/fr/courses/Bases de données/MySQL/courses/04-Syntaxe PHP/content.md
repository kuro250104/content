## Introduction

MySQL fonctionne très bien en combinaison avec divers langages de programmation comme PERL, C, C++, JAVA et PHP. Parmi
ces langages, PHP est le plus populaire en raison de ses capacités de développement d'applications Web.

Ce tutoriel se concentre principalement sur l'utilisation de MySQL dans un environnement PHP. Si vous êtes intéressé
par MySQL avec PERL, vous pouvez envisager de lire le tutoriel PERL.

PHP fournit diverses fonctions pour accéder à la base de données MySQL et pour manipuler les enregistrements de
données dans la base de données MySQL. Vous devez appeler les fonctions PHP de la même manière que vous appelez 
toute autre fonction PHP.

Les fonctions PHP utilisées avec MySQL ont le format général suivant

``` bash
mysqli function(value,value,...);
```

La deuxième partie du nom de la fonction est spécifique à la fonction, généralement un mot qui décrit ce que fait la
fonction. Voici deux des fonctions que nous utiliserons dans notre tutoriel.

``` bash
$mysqli = new mysqli($dbhost, $dbuser, $dbpass, $dbname);
mysqli->query(,"SQL statement");
```

L'exemple suivant montre une syntaxe générique de PHP pour appeler n'importe quelle fonction MySQL.

``` html
<html>
   <head>
      <title>PHP with MySQL</title>
   </head>
   
   <body>
      <?php
         $retval = mysqli - > function(value, [value,...]);
         if( !$retval ) {
            die ( "Error: a related error message" );
         }
         // Otherwise MySQL  or PHP Statements
      ?>
   </body>
</html>
```

À partir du prochain chapitre, nous verrons toutes les fonctionnalités importantes de MySQL avec PHP.