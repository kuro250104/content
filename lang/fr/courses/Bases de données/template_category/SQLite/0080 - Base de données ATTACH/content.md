## Introduction

Prenons le cas où vous avez plusieurs bases de données disponibles et que vous voulez utiliser l'une d'entre elles à la fois. L'instruction SQLite ATTACH DATABASE est utilisée pour sélectionner une base de données particulière, et après cette commande, toutes les instructions SQLite seront exécutées sous la base de données attachée.

## Syntaxe

Following is the basic syntax of SQLite ATTACH DATABASE statement.

```sql
ATTACH DATABASE 'DatabaseName' As 'Alias-Name';
```

La commande ci-dessus créera également une base de données dans le cas où la base de données n'est pas encore créée, sinon elle attachera simplement le nom du fichier de la base de données avec la base de données logique 'Alias-Name'.

## Exemple

Si vous voulez attacher une base de données existante testDB.db, alors l'instruction ATTACH DATABASE sera la suivante : -.

```sql
sqlite> ATTACH DATABASE 'testDB.db' as 'TEST';
```

Utilisez la commande SQLite ```.database``` pour afficher la base de données jointe.

```bash
sqlite> .database
seq  name             file
---  ---------------  ----------------------
0    main             /home/sqlite/testDB.db
2    test             /home/sqlite/testDB.db
```

Les noms de base de données **main** et **temp** sont réservés à la base de données primaire et à la base de données destinée à contenir des tables temporaires et d'autres objets de données temporaires. Ces deux noms de base de données existent pour chaque connexion de base de données et ne doivent pas être utilisés pour le rattachement, sinon vous obtiendrez le message d'avertissement suivant.

```bash
sqlite> ATTACH DATABASE 'testDB.db' as 'TEMP';
Error: database TEMP is already in use
sqlite> ATTACH DATABASE 'testDB.db' as 'main';
Error: database TEMP is already in use
```