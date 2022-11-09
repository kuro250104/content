Dans ce chapitre, nous allons voir comment déposer une base de données en utilisant la commande MongoDB.

## La méthode dropDatabase()

La commande MongoDB ```db.dropDatabase()``` est utilisée pour supprimer une base de données existante.

### Syntaxe

La syntaxe de base de la commande dropDatabase() est la suivante -

```
db.dropDatabase()
```

Cela supprimera la base de données sélectionnée. Si vous n'avez pas sélectionné de base de données, la base de données par défaut "test" sera supprimée.

### Exemple

Tout d'abord, vérifiez la liste des bases de données disponibles en utilisant la commande ```show dbs```.

```
>show dbs
local      0.78125GB
mydb       0.23012GB
test       0.23012GB
>
```

Si vous voulez supprimer la nouvelle base de données ```<mydb>```, alors la commande ```dropDatabase()``` sera la suivante -

```
>use mydb
switched to db mydb
>db.dropDatabase()
>{ "dropped" : "mydb", "ok" : 1 }
>
```

Maintenant, vérifiez la liste des bases de données.

```
>show dbs
local      0.78125GB
test       0.23012GB
>
```