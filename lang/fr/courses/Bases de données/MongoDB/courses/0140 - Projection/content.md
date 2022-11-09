Dans MongoDB, la projection consiste à sélectionner uniquement les données nécessaires plutôt que de sélectionner l'ensemble des données d'un document. Si un document comporte 5 champs et que vous souhaitez n'en afficher que 3, ne sélectionnez que 3 de ces champs.

## La méthode find()

La méthode ```find()``` de MongoDB, expliquée dans MongoDB Query Document, accepte un deuxième paramètre facultatif qui est la liste des champs que vous souhaitez récupérer. Dans MongoDB, lorsque vous exécutez la méthode ```find()```, elle affiche tous les champs d'un document. Pour limiter cela, vous devez définir une liste de champs avec la valeur 1 ou 0. 1 est utilisé pour afficher le champ tandis que 0 est utilisé pour cacher les champs.

### Syntaxe

La syntaxe de base de la méthode find() avec projection est la suivante -

```
>db.COLLECTION_NAME.find({},{KEY:1})
```

### Exemple

Considérons que la collection mycol a les données suivantes -

```
{_id : ObjectId("507f191e810c19729de860e1"), title: "MongoDB Overview"},
{_id : ObjectId("507f191e810c19729de860e2"), title: "NoSQL Overview"},
{_id : ObjectId("507f191e810c19729de860e3"), title: "Microlead Overview"}
```

L'exemple suivant affichera le titre du document lors de l'interrogation du document.

```
>db.mycol.find({},{"title":1,_id:0})
{"title":"MongoDB Overview"}
{"title":"NoSQL Overview"}
{"title":"Microlead Overview"}
>
```

Veuillez noter que le champ ```_id``` est toujours affiché lors de l'exécution de la méthode ```find()```, si vous ne voulez pas de ce champ, vous devez le mettre à 0.