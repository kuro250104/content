Pour commencer à comprendre les bases de PostgreSQL, il faut d'abord installer PostgreSQL. Ce chapitre explique comment installer PostgreSQL sur les plateformes Linux, Windows et Mac OS.

## Installation de PostgreSQL sur Linux/Unix

Suivez les étapes indiquées pour installer PostgreSQL sur votre machine Linux. Assurez-vous d'être connecté en tant que root avant de procéder à l'installation.

- Choisissez le numéro de la version de PostgreSQL que vous voulez et, aussi exactement que possible, la plateforme que vous voulez d'EnterpriseDB
- J'ai téléchargé postgresql-9.2.4-1-linux-x64.run pour ma machine CentOS-6 64 bits. 

Maintenant, exécutons-le de la manière suivante :

```bash
[root@host]# chmod +x postgresql-9.2.4-1-linux-x64.run
[root@host]# ./postgresql-9.2.4-1-linux-x64.run
------------------------------------------------------------------------
Welcome to the PostgreSQL Setup Wizard.

------------------------------------------------------------------------
Please specify the directory where PostgreSQL will be installed.

Installation Directory [/opt/PostgreSQL/9.2]:
```

- Lorsque vous lancez le programme d'installation, il vous pose quelques questions de base comme l'emplacement de l'installation, le mot de passe de l'utilisateur qui utilisera la base de données, le numéro de port, etc. Conservez toutes les valeurs par défaut, sauf le mot de passe, que vous pouvez fournir selon votre choix. Il installera PostgreSQL sur votre machine Linux et affichera le message suivant :

```
Please wait while Setup installs PostgreSQL on your computer.

 Installing
 0% ______________ 50% ______________ 100%
 #########################################

-----------------------------------------------------------------------
Setup has finished installing PostgreSQL on your computer.
```

- Suivez les étapes suivantes après l'installation pour créer votre base de données :

```
[root@host]# su - postgres
Password:
bash-4.1$ createdb testdb
bash-4.1$ psql testdb
psql (8.4.13, server 9.2.4)

test=#
```

- Vous pouvez démarrer/redémarrer le serveur postgres s'il n'est pas en cours d'exécution à l'aide de la commande suivante :

```
[root@host]# service postgresql restart
Stopping postgresql service:                               [  OK  ]
Starting postgresql service:                               [  OK  ]
```

Si votre installation est correcte, PotsgreSQL vous demandera test=# comme indiqué ci-dessus.

## Installation de PostgreSQL sur Windows

Suivez les étapes données pour installer PostgreSQL sur votre machine Windows. Assurez-vous que vous avez désactivé l'antivirus tiers pendant l'installation.

- Choisissez le numéro de version de PostgreSQL que vous voulez et, aussi exactement que possible, la plate-forme que vous voulez chez EnterpriseDB.
- J'ai téléchargé postgresql-9.2.4-1-windows.exe pour mon PC Windows fonctionnant en mode 32bit, alors exécutons postgresql-9.2.4-1-windows.exe en tant qu'administrateur pour installer PostgreSQL. Sélectionnez l'emplacement où vous souhaitez l'installer. Par défaut, il est installé dans le dossier Program Files.
- L'étape suivante du processus d'installation consiste à sélectionner le répertoire dans lequel vos données seront stockées. Par défaut, elles sont stockées dans le répertoire "data".
- Ensuite, le programme d'installation demande un mot de passe, vous pouvez donc utiliser votre mot de passe préféré.
- L'étape suivante est de garder le port par défaut.
- À l'étape suivante, lorsqu'on m'a demandé de choisir le "Locale", j'ai sélectionné "English, United States".
- L'installation de PostgreSQL sur votre système prend un certain temps. A la fin du processus d'installation, vous obtiendrez l'écran suivant. Décochez la case et cliquez sur le bouton "Finish".

Une fois le processus d'installation terminé, vous pouvez accéder à pgAdmin III, StackBuilder et au shell PostgreSQL à partir du menu des programmes sous PostgreSQL 9.2.

## Installation de PostgreSQL sur Mac

Suivez les étapes indiquées pour installer PostgreSQL sur votre machine Mac. Assurez-vous d'être connecté en tant qu'administrateur avant de procéder à l'installation.

- Choisissez le dernier numéro de version de PostgreSQL pour Mac OS disponible sur EnterpriseDB.
- J'ai téléchargé postgresql-9.2.4-1-osx.dmg pour mon Mac OS fonctionnant avec OS X version 10.8.3. Maintenant, ouvrons l'image dmg dans le finder et double-cliquez dessus, ce qui vous donnera le programme d'installation de PostgreSQL dans la fenêtre suivante.
- Ensuite, cliquez sur l'icône postgres-9.2.4-1-osx, qui affichera un message d'avertissement. Acceptez l'avertissement et poursuivez l'installation. Il vous sera demandé le mot de passe de l'administrateur.
- Lorsque vous lancez le programme d'installation, il vous pose quelques questions de base comme l'emplacement de l'installation, le mot de passe de l'utilisateur qui utilisera la base de données, le numéro de port, etc. Par conséquent, gardez toutes les valeurs par défaut, sauf le mot de passe, que vous pouvez fournir selon votre choix. PostgreSQL sera installé sur votre machine Mac dans le dossier Application que vous pouvez vérifier.
- Maintenant, vous pouvez lancer n'importe quel programme pour commencer. Commençons par SQL Shell. Lorsque vous lancez SQL Shell, utilisez simplement toutes les valeurs par défaut qu'il affiche, à l'exception de votre mot de passe, que vous avez choisi au moment de l'installation. Si tout se passe bien, vous serez dans la base de données postgres et une invite postgress# s'affichera.

Félicitations ! Vous avez maintenant votre environnement prêt à commencer la programmation de la base de données PostgreSQL.
