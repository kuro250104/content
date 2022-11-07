## Introduction

SQLite est célèbre pour sa grande fonctionnalité zéro-configuration, ce qui signifie qu'aucune configuration ou administration complexe n'est nécessaire. Ce chapitre vous guidera dans le processus de configuration de SQLite sur Windows, Linux et Mac OS X.

## Installer SQLite sous Windows

- **Étape 1** - Allez à la page de téléchargement de SQLite, et téléchargez les binaires précompilés de la section Windows.
- **Étape 2** - Téléchargez les fichiers zippés sqlite-shell-win32-*.zip et sqlite-dll-win32-*.zip.
- **Étape 3** - Créez un dossier C:\>sqlite et décompressez les deux fichiers zippés ci-dessus dans ce dossier, ce qui vous donnera les fichiers sqlite3.def, sqlite3.dll et sqlite3.exe.
- **Étape 4** - Ajoutez C:\>sqlite dans votre variable d'environnement PATH et enfin allez à l'invite de commande et lancez la commande sqlite3, qui devrait afficher le résultat suivant.

```bash
C:\>sqlite3
SQLite version 3.7.15.2 2013-01-09 11:53:05
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite>
```

## Installer SQLite sur Linux

Aujourd'hui, presque toutes les versions du système d'exploitation Linux sont livrées avec SQLite. Il vous suffit donc de lancer la commande suivante pour vérifier si SQLite est déjà installé sur votre machine.

```bash
$sqlite3
SQLite version 3.7.15.2 2013-01-09 11:53:05
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite>
```

Si vous ne voyez pas le résultat ci-dessus, cela signifie que SQLite n'est pas installé sur votre machine Linux. Vous trouverez ci-dessous les étapes à suivre pour installer SQLite.

- **Étape 1** - Allez à la page de téléchargement de SQLite et téléchargez sqlite-autoconf-*.tar.gz depuis la section du code source.
- **Étape 2** - Exécutez la commande suivante -

```bash
$tar xvfz sqlite-autoconf-3071502.tar.gz
$cd sqlite-autoconf-3071502
$./configure --prefix=/usr/local
$make
$make install
```

La commande ci-dessus se terminera par l'installation de SQLite sur votre machine Linux. Que vous pouvez vérifier comme expliqué ci-dessus.

## Installer SQLite sur Mac OS X

Bien que la dernière version de Mac OS X soit préinstallée avec SQLite, si vous n'avez pas d'installation disponible, il suffit de suivre les étapes suivantes.

- **Étape 1** - Allez à la page de téléchargement de SQLite, et téléchargez sqlite-autoconf-*.tar.gz depuis la section du code source.
- **Étape 2** - Exécutez la commande suivante −

```bash
$tar xvfz sqlite-autoconf-3071502.tar.gz
$cd sqlite-autoconf-3071502
$./configure --prefix=/usr/local
$make
$make install
```

La procédure ci-dessus se terminera par l'installation de SQLite sur votre machine Mac OS X. Ce que vous pouvez vérifier en lançant la commande suivante -

```bash
$sqlite3
SQLite version 3.7.15.2 2013-01-09 11:53:05
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite>
```

Enfin, vous avez l'invite de commande SQLite où vous pouvez lancer des commandes SQLite pour vos exercices.