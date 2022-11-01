## Introduction

La façon la plus simple d'exporter les données d'une table dans un fichier texte est d'utiliser l'instruction 
**SELECT...INTO OUTFILE** qui exporte le résultat d'une requête directement dans un fichier sur l'hôte du serveur.

## Exporting Data with the SELECT ... INTO OUTFILE Statement

La syntaxe de cette instruction combine une commande **SELECT** ordinaire avec un nom de fichier **INTO OUTFILE**
à la fin. Le format de sortie par défaut est le même que pour la commande **LOAD DATA**. Ainsi, l'instruction suivante
exporte la table tutorials_tbl dans /tmp/tutorials.txt sous forme de fichier délimité par des tabulations
et terminé par des retours à la ligne.

``` sql
mysql> SELECT * FROM tutorials_tbl 
   -> INTO OUTFILE '/tmp/tutorials.txt';
```

Vous pouvez modifier le format de sortie en utilisant diverses options pour indiquer comment citer et délimiter les 
colonnes et les enregistrements. Pour exporter la table tutorial_tbl dans un format CSV avec des lignes terminées par 
CRLF, utilisez le code suivant.

``` sql
mysql> SELECT * FROM passwd INTO OUTFILE '/tmp/tutorials.txt'
   -> FIELDS TERMINATED BY ',' ENCLOSED BY '"'
   -> LINES TERMINATED BY '\r\n';
```

La commande SELECT ... INTO OUTFILE possède les propriétés suivantes :

  - Le fichier de sortie est créé directement par le serveur MySQL, le nom du fichier doit donc indiquer l'endroit où vous souhaitez que le fichier soit écrit sur l'hôte du serveur. Il n'existe pas de version LOCAL de l'instruction analogue à la version LOCAL de LOAD DATA.
  - Vous devez disposer du privilège MySQL FILE pour exécuter l'instruction SELECT ... INTO.
  - Le fichier de sortie ne doit pas déjà exister. Cela empêche MySQL de bloquer des fichiers qui pourraient être importants.
  - Vous devez disposer d'un compte de connexion sur l'hôte du serveur ou d'un moyen de récupérer le fichier à partir de cet hôte. Sinon, la commande SELECT ... INTO OUTFILE ne vous sera probablement d'aucune utilité.
  - Sous UNIX, le fichier est créé en lecture universelle et est la propriété du serveur MySQL. Cela signifie que, bien que vous puissiez lire le fichier, vous ne pourrez peut-être pas le supprimer.

## Exporting Tables as Raw Data

Le programme **mysqldump** est utilisé pour copier ou sauvegarder des tables et des bases de données. 
Il peut écrire la sortie de la table soit comme un **Raw Datafile**, soit comme un ensemble d'instructions **INSERT**
qui recréent les enregistrements de la table.

Pour vider une table sous forme de fichier de données, vous devez spécifier l'option **--tab** qui indique le répertoire 
dans lequel vous souhaitez que le serveur MySQL écrive le fichier.

Par exemple, pour vider la table tutorials_tbl de la base de données TUTORIALS dans un fichier du répertoire /tmp, 
utilisez une commande comme indiqué ci-dessous.

``` sql
$ mysqldump -u root -p --no-create-info \
   --tab=/tmp tutorials tutorials_tbl
password ******
```

## Exporting Table Contents or Definitions in SQL Format

Pour exporter une table au format SQL vers un fichier, utilisez la commande ci-dessous.

``` sql
$ mysqldump -u root -p TUTORIALS tutorials_tbl > dump.txt
password ******
```

Cela créera un fichier dont le contenu est indiqué ci-dessous.

``` sql
-- MySQL dump 8.23
--
-- Host: localhost    Database: TUTORIALS
---------------------------------------------------------
-- Server version       3.23.58

--
-- Table structure for table `tutorials_tbl`
--

CREATE TABLE tutorials_tbl (
   tutorial_id int(11) NOT NULL auto_increment,
   tutorial_title varchar(100) NOT NULL default '',
   tutorial_author varchar(40) NOT NULL default '',
   submission_date date default NULL,
   PRIMARY KEY  (tutorial_id),
   UNIQUE KEY AUTHOR_INDEX (tutorial_author)
) TYPE = MyISAM;

--
-- Dumping data for table `tutorials_tbl`
--

INSERT INTO tutorials_tbl 
   VALUES (1,'Learn PHP','John Poul','2007-05-24');
INSERT INTO tutorials_tbl 
   VALUES (2,'Learn MySQL','Abdul S','2007-05-24');
INSERT INTO tutorials_tbl 
   VALUES (3,'JAVA Tutorial','Sanjay','2007-05-06');
```

Pour vider plusieurs tables, nommez-les toutes suivies de l'argument du nom de la base de données. Pour vider une
base de données entière, ne nommez aucune table après la base de données, comme indiqué dans le bloc de code suivant.

``` sql
$ mysqldump -u root -p TUTORIALS > database_dump.txt
password ******
```

Pour sauvegarder toutes les bases de données disponibles sur votre hôte, utilisez le code suivant.

``` sql
$ mysqldump -u root -p --all-databases > database_dump.txt
password ******
```

L'option --all-databases est disponible dans la version 3.23.12 de MySQL. Cette méthode peut être utilisée pour 
mettre en place une stratégie de sauvegarde des bases de données.

## Copying Tables or Databases to Another Host

Si vous voulez copier des tables ou des bases de données d'un serveur MySQL à un autre, utilisez la commande **mysqldump** 
avec le nom de la base de données et le nom de la table.

Exécutez la commande suivante sur l'hôte source. Cela va vider la base de données complète dans le fichier **dump.txt**.

``` sql
$ mysqldump -u root -p database_name table_name > dump.txt
password *****
```

Vous pouvez copier une base de données complète sans utiliser un nom de table particulier comme expliqué ci-dessus.

Maintenant, ftp le fichier dump.txt sur un autre hôte et utilisez la commande suivante. Avant d'exécuter cette commande,
assurez-vous que vous avez créé nom_de_base_de_données sur le serveur de destination.

``` sql
$ mysql -u root -p database_name < dump.txt
password *****
```

Une autre façon d'y parvenir sans utiliser de fichier intermédiaire est d'envoyer la sortie de mysqldump directement 
par le réseau au serveur MySQL distant. Si vous pouvez vous connecter aux deux serveurs depuis l'hôte où réside la base
de données source, utilisez la commande suivante (assurez-vous d'avoir accès aux deux serveurs).

``` sql
$ mysqldump -u root -p database_name \
   | mysql -h other-host.com database_name
```

Dans mysqldump, la moitié de la commande se connecte au serveur local et écrit la sortie du dump dans le tube.
L'autre moitié de la commande se connecte au serveur MySQL distant sur l'autre-hôte.com. Elle lit le tuyau pour 
l'entrée et envoie chaque instruction au serveur de l'autre-hôte.com.