Dans ce chapitre, nous allons voir comment déposer une collection en utilisant MongoDB.

## La méthode drop()

La fonction ```db.collection.drop()``` de MongoDB est utilisée pour supprimer une collection de la base de données.

### Syntaxe

La syntaxe de base de la commande ```drop()``` est la suivante -

```
db.COLLECTION_NAME.drop()
```

### Exemple

Tout d'abord, vérifiez les collections disponibles dans votre base de données **mydb**.

```
>use mydb
switched to db mydb
>show collections
mycol
mycollection
system.indexes
Microlead
>
```

Maintenant, déposez la collection avec le nom **mycollection**.

```
>db.mycollection.drop()
true
>
```

Vérifiez à nouveau la liste des collections dans la base de données.

```
>show collections
mycol
system.indexes
Microlead
>
```

La méthode ```drop()``` renvoie true, si la collection sélectionnée a été déposée avec succès, sinon elle renvoie false.