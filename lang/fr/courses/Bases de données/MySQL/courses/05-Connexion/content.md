## Connexion à MySQL en utilisant le binaire MySQL

Vous pouvez établir la base de données MySQL en utilisant le binaire mysql à l'invite de commande.

### Exemple

Voici un exemple simple pour se connecter au serveur MySQL à partir de l'invite de commande : 

``` bash
[root@host]# mysql -u root -p
Enter password:******
```

Cela vous donnera l'invite de commande mysql> où vous pourrez exécuter n'importe quelle commande SQL.
Le résultat de la commande ci-dessus est le suivant :

Le bloc de code suivant montre le résultat de la commande ci-dessus.

``` bash
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2854760 to server version: 5.0.9

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.
```

Dans l'exemple ci-dessus, nous avons utilisé **root** comme utilisateur mais vous pouvez également utiliser n'importe quel 
autre utilisateur. Tout utilisateur sera en mesure d'effectuer toutes les opérations SQL qui lui sont autorisées.

Vous pouvez vous déconnecter de la base de données MySQL à tout moment en utilisant la
commande **exit** à l'invite mysql>prompt.

``` bash
mysql> exit
Bye
```

## MySQL Connection Using PHP Script

PHP fournit la contruction **mysqli** ou la fonction **mysqli_connect()** pour ouvrir une connexion à une base de données.
Cette fonction prend six paramètres et renvoie un identifiant de lien MySQL en cas de succès ou FALSE en cas d'échec.

``` bash
$mysqli = new mysqli($host, $username, $passwd, $dbName, $port, $socket);
```

Paramètre et description :

  - **$host** - ( Facultatif ) - Le nom d'hôte exécutant le serveur de la base de données. S'il n'est pas spécifié, la valeur par défaut sera localhost:3306.
  - **$username** - ( Facultatif )- Le nom d'utilisateur accédant à la base de données. S'il n'est pas spécifié, la valeur par défaut sera le nom de l'utilisateur qui possède le processus du serveur.
  - **$passwd** - ( Facultatif )- Le mot de passe de l'utilisateur qui accède à la base de données. S'il n'est pas spécifié, la valeur par défaut sera un mot de passe vide.
  - **$dbName** - ( Facultatif )- nom de la base de données sur laquelle la requête doit être effectuée.
  - **$port** - ( Facultatif )- le numéro de port pour tenter de se connecter au serveur MySQL.
  - **$socket** - ( Facultatif )- douille ou tuyau nommé qui doit être utilisé.

Vous pouvez vous déconnecter de la base de données MySQL à tout moment en utilisant une autre fonction PHP close().

### Syntax 

``` bash
$mysqli->close();
```

### Exemple

Essayez l'exemple suivant pour vous connecter à un serveur MySQL.

Copiez et collez l'exemple suivant sous le nom de mysql_example.php.

``` html
<html>
   <head>
      <title>Connecting MySQL Server</title>
   </head>
   <body>
      <?php
         $dbhost = 'localhost';
         $dbuser = 'root';
         $dbpass = 'root@123';
         $mysqli = new mysqli($dbhost, $dbuser, $dbpass);
         
         if($mysqli->connect_errno ) {
            printf("Connect failed: %s<br />", $mysqli->connect_error);
            exit();
         }
         printf('Connected successfully.<br />');
         $mysqli->close();
      ?>
   </body>
</html>
```

### Sortie

Accédez au fichier mysql_example.php déployé sur le serveur web apache et vérifiez la sortie.

``` bash
Connected successfully.
```

