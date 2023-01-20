## Introduction

Dans SQLite, la commande sqlite3 est utilisée pour créer une nouvelle base de données SQLite. Il n'est pas nécessaire de disposer de privilèges particuliers pour créer une base de données.

## Syntaxe

Voici la syntaxe de base de la commande sqlite3 pour créer une base de données :

```bash
$sqlite3 DatabaseName.db
```

Le nom de la base de données doit toujours être unique au sein du SGBDR.

## Exemple

Si vous voulez créer une nouvelle base de données ```<testDB.db>```, alors la déclaration SQLITE3 serait la suivante :

```bash
$sqlite3 testDB.db
SQLite version 3.7.15.2 2013-01-09 11:53:05
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite>
```

La commande ci-dessus va créer un fichier ```testDB.db``` dans le répertoire courant. Ce fichier sera utilisé comme base de données par le moteur SQLite. Si vous avez remarqué lors de la création de la base de données, la commande ```sqlite3``` fournira une invite ```sqlite>``` après avoir créé avec succès un fichier de base de données.
Une fois qu'une base de données est créée, vous pouvez la vérifier dans la liste des bases de données en utilisant la commande SQLite ```.databases``` suivante.

```bash
sqlite>.databases
seq  name             file
---  ---------------  ----------------------
0    main             /home/sqlite/testDB.db
```

Vous utiliserez la commande SQLite ```.quit``` pour sortir de l'invite sqlite comme suit -

```bash
sqlite>.quit
$
```

## La commande .dump

Vous pouvez utiliser la commande ```.dump``` dot pour exporter une base de données complète dans un fichier texte en utilisant la commande SQLite suivante à l'invite de commande.

```bash
$sqlite3 testDB.db .dump > testDB.sql
```

La commande ci-dessus convertira tout le contenu de la base de données ```testDB.db``` en instructions SQLite et le déposera dans le fichier texte ASCII ```testDB.sql```. Vous pouvez effectuer une restauration à partir du fichier ```testDB.sql``` généré d'une manière simple, comme suit :

```bash
$sqlite3 testDB.db < testDB.sql
```

Pour le moment, votre base de données est vide, vous pouvez donc essayer les deux procédures ci-dessus une fois que vous aurez quelques tables et données dans votre base de données. Pour l'instant, passons au chapitre suivant.
