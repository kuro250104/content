Dans ce chapitre, nous allons apprendre à limiter les enregistrements en utilisant MongoDB.

## La méthode Limit()

Pour limiter les enregistrements dans MongoDB, vous devez utiliser la méthode ```limit()```. Cette méthode accepte un argument de type nombre, qui est le nombre de documents que vous souhaitez afficher.

### Syntaxe

La syntaxe de base de la méthode ```limit()``` est la suivante -

```
>db.COLLECTION_NAME.find().limit(NUMBER)
```

### Exemple

Considérons la collection myycol qui possède les données suivantes.

```
{_id : ObjectId("507f191e810c19729de860e1"), title: "MongoDB Overview"},
{_id : ObjectId("507f191e810c19729de860e2"), title: "NoSQL Overview"},
{_id : ObjectId("507f191e810c19729de860e3"), title: "Microlead Overview"}
```

L'exemple suivant n'affichera que deux documents lors de l'interrogation du document.

```
>db.mycol.find({},{"title":1,_id:0}).limit(2)
{"title":"MongoDB Overview"}
{"title":"NoSQL Overview"}
>
```

Si vous ne spécifiez pas l'argument du nombre dans la méthode ```limit()```, celle-ci affichera tous les documents de la collection.

## La méthode Skip()

Outre la méthode ```limit()```, il existe une autre méthode ```skip()``` qui accepte également un argument de type nombre et qui est utilisée pour sauter le nombre de documents.

### Syntaxe

La syntaxe de base de la méthode ```skip()``` est la suivante -

```
>db.COLLECTION_NAME.find().limit(NUMBER).skip(NUMBER)
```

### Exemple

L'exemple suivant n'affichera que le deuxième document.

```
>db.mycol.find({},{"title":1,_id:0}).limit(1).skip(1)
{"title":"NoSQL Overview"}
>
```

Veuillez noter que la valeur par défaut de la méthode ```skip()``` est 0.