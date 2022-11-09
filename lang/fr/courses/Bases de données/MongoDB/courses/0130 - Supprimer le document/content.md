Dans ce chapitre, nous allons apprendre à supprimer un document à l'aide de MongoDB.

## La méthode remove()

La méthode ```remove()``` de MongoDB est utilisée pour supprimer un document de la collection. La méthode ```remove()``` accepte deux paramètres. Le premier est le critère de suppression et le second est l'indicateur justOne.

- **deletion criteria** − (Facultatif) critères de suppression selon les documents qui seront supprimés.
- **justOne** − (Facultatif) si la valeur est true ou 1, ne supprimer qu'un seul document.

### Syntaxe

La syntaxe de base de la méthode remove() est la suivante -

```
>db.COLLECTION_NAME.remove(DELLETION_CRITTERIA)
```

### Exemple

Considérons que la collection mycol a les données suivantes.

```
{_id : ObjectId("507f191e810c19729de860e1"), title: "MongoDB Overview"},
{_id : ObjectId("507f191e810c19729de860e2"), title: "NoSQL Overview"},
{_id : ObjectId("507f191e810c19729de860e3"), title: "Microlead Overview"}
```

L'exemple suivant supprimera tous les documents dont le titre est 'MongoDB Overview'.

```
>db.mycol.remove({'title':'MongoDB Overview'})
WriteResult({"nRemoved" : 1})
> db.mycol.find()
{"_id" : ObjectId("507f191e810c19729de860e2"), "title" : "NoSQL Overview" }
{"_id" : ObjectId("507f191e810c19729de860e3"), "title" : "Microlead Overview" }
```

## Enlever seulement un

S'il existe plusieurs enregistrements et que vous souhaitez supprimer uniquement le premier, définissez le paramètre **justOne** dans la méthode ```remove()```.

```
>db.COLLECTION_NAME.remove(DELETION_CRITERIA,1)
```

## Supprimer tous les documents

Si vous ne spécifiez pas de critères de suppression, MongoDB supprimera des documents entiers de la collection. C'est l'équivalent de la commande truncate de SQL.

```
> db.mycol.remove({})
WriteResult({ "nRemoved" : 2 })
> db.mycol.find()
>
```