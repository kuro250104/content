## Introduction

Tous les téléchargements pour MySQL se trouvent sur le site MySQL Downloads. Choisissez le numéro de version de **MySQL
Community Server** dont vous avez besoin, ainsi que la plate-forme sur laquelle vous l'exécuterez.

## Installation de MySQL sur Linux/UNIX

La manière recommandée d'installer MySQL sur un système Linux est via un RPM. MySQL AB met les RPM suivants à 
disposition pour téléchargement sur son site web :

  - **MySQL** − Le serveur de base de données MySQL gère les bases de données et les tables, contrôle l'accès des utilisateurs et traite les requêtes SQL.
  - **MySQL-client** − Les programmes clients MySQL, qui permettent de se connecter et d'interagir avec le serveur.
  - **MySQL-devel** − Bibliothèques et fichiers d'en-tête qui s'avèrent utiles lors de la compilation d'autres programmes utilisant MySQL.
  - **MySQL-shared** − Bibliothèques partagées pour le client MySQL.
  - **MySQL-bench** − Outils de benchmarking et de test de performance pour le serveur de base de données MySQL.

Les RPMs MySQL listés ici sont tous construits sur un système **SuSE Linux**, mais ils fonctionnent généralement sur 
d'autres variantes de Linux sans difficulté.

Vous devez maintenant suivre les étapes indiquées ci-dessous pour procéder à l'installation.

  - Connectez-vous au système en utilisant l'utilisateur root.
  - Passez dans le répertoire contenant les RPM.
  - Installez le serveur de base de données MySQL en exécutant la commande suivante. 

N'oubliez pas de remplacer le nom de fichier en italique par le nom de fichier de votre RPM.

``` bash
[root@host]# rpm -i MySQL-5.0.9-0.i386.rpm
```

La commande ci-dessus se charge d'installer le serveur MySQL, de créer un utilisateur de MySQL, de créer la configuration
nécessaire et de démarrer le serveur MySQL automatiquement.

Vous pouvez trouver tous les binaires relatifs à MySQL dans /usr/bin et /usr/sbin. Toutes les tables et bases de
données seront créées dans le répertoire /var/lib/mysql.

La boîte de code suivante comporte une étape facultative mais recommandée pour installer les autres RPMs de la 
même manière : 

``` bash
[root@host]# rpm -i MySQL-client-5.0.9-0.i386.rpm
[root@host]# rpm -i MySQL-devel-5.0.9-0.i386.rpm
[root@host]# rpm -i MySQL-shared-5.0.9-0.i386.rpm
[root@host]# rpm -i MySQL-bench-5.0.9-0.i386.rpm
```

## Installation de MySQL sous Windows

L'installation par défaut sur n'importe quelle version de Windows est désormais beaucoup plus simple qu'auparavant, 
car MySQL est désormais fourni avec un installateur. Il suffit de télécharger le package d'installation, de le 
décompresser n'importe où et d'exécuter le fichier setup.exe.

Le programme d'installation par défaut setup.exe vous guidera tout au long de ce processus trivial et, par défaut, 
installera tout sous C:\mysql.

Testez le serveur en le lançant à l'invite de commande la première fois. Allez à l'emplacement du **serveur mysqld** qui 
est probablement C:\mysql\bin, et tapez

``` bash
mysqld.exe --console
```

**NOTE** - Si vous êtes sous NT, vous devez utiliser mysqld-nt.exe au lieu de mysqld.exe.

Si tout s'est bien passé, vous verrez quelques messages concernant le démarrage et **InnoDB**. Si ce n'est pas le cas,
vous avez peut-être un problème de permissions. Assurez-vous que le répertoire qui contient vos données est accessible
à l'utilisateur (probablement MySQL) sous lequel les processus de base de données sont exécutés.

MySQL ne s'ajoute pas au menu de démarrage, et il n'existe pas non plus d'interface graphique particulièrement
agréable pour arrêter le serveur. Par conséquent, si vous avez tendance à démarrer le serveur en double-cliquant sur
l'exécutable mysqld, vous devez vous souvenir d'arrêter le processus manuellement en utilisant mysqladmin, Task List, 
Task Manager, ou tout autre moyen spécifique à Windows.

## Vérification de l'installation de MySQL

Une fois que MySQL a été installé avec succès, que les tables de base ont été initialisées et que le serveur a 
été démarré, vous pouvez vérifier que tout fonctionne comme il se doit grâce à quelques tests simples.

### Utiliser l'utilitaire mysqladmin pour obtenir l'état du serveur

Utilisez le binaire **mysqladmin** pour vérifier la version du serveur. Ce binaire est disponible dans /usr/bin sous 
linux et dans C:\mysql\bin sous windows.

``` bash
[root@host]# mysqladmin --version
```

Il produira le résultat suivant sous Linux. Il peut varier en fonction de votre installation

``` bash
mysqladmin  Ver 8.23 Distrib 5.0.9-0, for redhat-linux-gnu on i386
```

Si vous n'obtenez pas un tel message, il se peut qu'il y ait un problème dans votre installation et vous aurez 
besoin d'aide pour le résoudre.

### Exécuter des commandes SQL simples à l'aide du client MySQL

Vous pouvez vous connecter à votre serveur MySQL via le client MySQL et en utilisant la commande **mysql**. Pour l'instant,
vous n'avez pas besoin de donner de mot de passe car il est défini par défaut comme vide.

Vous pouvez simplement utiliser la commande suivante :

``` bash
[root@host]# mysql
```

Il devrait être récompensé par une invite mysql>. Maintenant, vous êtes connecté au serveur MySQL et vous pouvez
exécuter toutes les commandes SQL à l'invite mysql>, comme suit :

``` bash
mysql> SHOW DATABASES;
+----------+
| Database |
+----------+
|   mysql  | 
|   test   |  
+----------+
2 rows in set (0.13 sec)
```

## Étapes de la post-installation

MySQL est livré avec un mot de passe vide pour l'utilisateur root de MySQL. Dès que vous avez installé avec succès la 
base de données et le client, vous devez définir un mot de passe root, comme indiqué dans le bloc de code suivant :

``` bash 
[root@host]# mysqladmin -u root password "new_password";
```

Maintenant, pour établir une connexion à votre serveur MySQL, vous devez utiliser la commande suivante :

``` bash
[root@host]# mysql -u root -p
Enter password:*******
```

Les utilisateurs UNIX voudront également placer le répertoire MySQL dans leur PATH, afin de ne pas avoir à taper le
chemin complet à chaque fois que vous voulez utiliser le client en ligne de commande.

Pour bash, ce serait quelque chose comme :

``` bash
export PATH = $PATH:/usr/bin:/usr/sbin
```

## Exécution de MySQL au démarrage

Si vous voulez exécuter le serveur MySQL au démarrage, assurez-vous d'avoir l'entrée suivante dans le fichier
/etc/rc.local.

``` bash
/etc/init.d/mysqld start
```

De plus, vous devriez avoir le binaire mysqld dans le répertoire /etc/init.d/.
