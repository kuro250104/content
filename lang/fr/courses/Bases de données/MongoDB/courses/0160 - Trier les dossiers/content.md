Dans ce chapitre, nous allons apprendre à trier les enregistrements dans MongoDB.

## The sort() Method

Pour trier des documents dans MongoDB, vous devez utiliser la méthode ```sort()```. Cette méthode accepte un document contenant une liste de champs ainsi que leur ordre de tri. Pour spécifier l'ordre de tri, on utilise 1 et -1. Le chiffre 1 est utilisé pour l'ordre croissant, tandis que le chiffre -1 est utilisé pour l'ordre décroissant.

### Syntaxe

La syntaxe de base de la méthode ```sort()``` est la suivante -

```
>db.COLLECTION_NAME.find().sort({KEY:1})
```

### Exemple

Considérons la collection myycol qui possède les données suivantes.

```
{_id : ObjectId("507f191e810c19729de860e1"), title: "MongoDB Overview"}
{_id : ObjectId("507f191e810c19729de860e2"), title: "NoSQL Overview"}
{_id : ObjectId("507f191e810c19729de860e3"), title: "Microlead Overview"}
```

L'exemple suivant affichera les documents triés par titre dans l'ordre décroissant.

```
>db.mycol.find({},{"title":1,_id:0}).sort({"title":-1})
{"title":"Microlead Overview"}
{"title":"NoSQL Overview"}
{"title":"MongoDB Overview"}
>
```

Veuillez noter que si vous ne spécifiez pas la préférence de tri, la méthode ```sort()``` affichera les documents dans l'ordre croissant.