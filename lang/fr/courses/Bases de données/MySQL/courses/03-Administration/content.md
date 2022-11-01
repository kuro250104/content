## Introduction

### Exécution et arrêt du serveur MySQL

Vérifiez d'abord si votre serveur MySQL fonctionne ou non. Vous pouvez utiliser la commande suivante pour le faire :

``` bash
ps -ef | grep mysqld
```

Si votre MySql est en cours d'exécution, vous verrez le processus mysqld listé dans votre résultat. Si le serveur n'est 
pas en cours d'exécution, vous pouvez le démarrer à l'aide de la commande suivante :

``` bash
root@host# cd /usr/bin
./safe_mysqld &
```

Maintenant, si vous voulez arrêter un serveur MySQL en cours d'exécution, vous pouvez le faire en utilisant la 
commande suivante :

``` bash
root@host# cd /usr/bin
./mysqladmin -u root -p shutdown
Enter password: ******
```

## Configuration d'un compte utilisateur MySQL

Pour ajouter un nouvel utilisateur à MySQL, il suffit d'ajouter une nouvelle entrée dans la table des **utilisateurs**
de la base de données **mysql**.

Le programme suivant est un exemple d'ajout d'un nouvel utilisateur guest avec des privilèges SELECT, INSERT et UPDATE 
avec le mot de passe guest123 ; la requête SQL est :

``` bash
root@host# mysql -u root -p
Enter password:*******
mysql> use mysql;
Database changed

mysql> INSERT INTO user 
   (host, user, password, 
   select_priv, insert_priv, update_priv) 
   VALUES ('localhost', 'guest', 
   PASSWORD('guest123'), 'Y', 'Y', 'Y');
Query OK, 1 row affected (0.20 sec)

mysql> FLUSH PRIVILEGES;
Query OK, 1 row affected (0.01 sec)

mysql> SELECT host, user, password FROM user WHERE user = 'guest';
+-----------+---------+------------------+
|    host   |   user  |     password     |    
+-----------+---------+------------------+
| localhost |  guest  | 6f8c114b58f2ce9e |
+-----------+---------+------------------+
1 row in set (0.00 sec)
```

Lorsque vous ajoutez un nouvel utilisateur, n'oubliez pas de crypter le nouveau mot de passe à l'aide de la fonction 
PASSWORD() fournie par MySQL. Comme vous pouvez le voir dans l'exemple ci-dessus, le mot de passe mypass est crypté en
6f8c114b58f2ce9e.

Remarquez l'instruction FLUSH PRIVILEGES. Elle indique au serveur de recharger les tables d'attribution. Si vous ne 
l'utilisez pas, vous ne pourrez pas vous connecter à MySQL à l'aide du nouveau compte utilisateur, au moins jusqu'au 
redémarrage du serveur.

Vous pouvez également spécifier d'autres privilèges à un nouvel utilisateur en définissant les valeurs des colonnes
suivantes dans la table des utilisateurs à 'Y' lors de l'exécution de la requête INSERT ou vous pouvez les mettre à
jour plus tard en utilisant la requête UPDATE.

  - Select_priv
  - Insert_priv
  - Update_priv
  - Delete_priv
  - Create_priv
  - Drop_priv
  - Reload_priv
  - Shutdown_priv
  - Process_priv
  - File_priv
  - Grant_priv
  - References_priv
  - Index_priv
  - Alter_priv

Une autre façon d'ajouter un compte utilisateur est d'utiliser la commande GRANT SQL. L'exemple suivant ajoutera 
l'utilisateur zara avec le mot de passe zara123 pour une base de données particulière, qui est nommée TUTORIALS.

``` bash
root@host# mysql -u root -p password;
Enter password:*******
mysql> use mysql;
Database changed

mysql> GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP
   -> ON TUTORIALS.*
   -> TO 'zara'@'localhost'
   -> IDENTIFIED BY 'zara123';
```

Cela créera également une entrée dans la table de la base de données MySQL appelée "**user**".

**NOTE** − MySQL ne termine pas une commande tant que vous ne donnez pas un point-virgule ( ;) à la fin de la 
commande SQL.

### La configuration du fichier /etc/my.cnf

Dans la plupart des cas, vous ne devez pas toucher à ce fichier. Par défaut, il aura les entrées suivantes :

``` bash
[mysqld]
datadir = /var/lib/mysql
socket = /var/lib/mysql/mysql.sock

[mysql.server]
user = mysql
basedir = /var/lib

[safe_mysqld]
err-log = /var/log/mysqld.log
pid-file = /var/run/mysqld/mysqld.pid
```

Ici, vous pouvez spécifier un répertoire différent pour le journal des erreurs, sinon vous ne devez modifier
aucune entrée dans cette table.

## Commande administrative MySQL

Voici la liste des commandes MySQL importantes, que vous utiliserez de temps en temps pour travailler avec la 
base de données MySQL.

  - **USE Databasename** − Ceci sera utilisé pour sélectionner une base de données dans la zone de travail MySQL.
  - **SHOW DATABASES** − Liste les bases de données qui sont accessibles par le SGBD MySQL.
  - **SHOW TABLES** − Affiche les tables de la base de données une fois qu'une base de données a été sélectionnée avec la commande use.
  - **SHOW COLUMNS FROM tablename** - Affiche les attributs, les types d'attributs, les informations sur les clés, si NULL est autorisé, les valeurs par défaut et d'autres informations pour une table.
  - **SHOW INDEX FROM tablename** − Présente les détails de tous les index de la table, y compris la PRIMARY KEY.
  - **SHOW TABLE STATUS LIKE tablename\G** − Rapporte les détails des performances et des statistiques du SGBD MySQL.

Dans le chapitre suivant, nous verrons comment la syntaxe PHP est utilisée dans MySQL.