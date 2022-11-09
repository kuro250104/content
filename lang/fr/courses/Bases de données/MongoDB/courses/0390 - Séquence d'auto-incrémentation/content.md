MongoDB ne dispose pas d'une fonctionnalité d'auto-incrémentation prête à l'emploi, comme les bases de données SQL. Par défaut, il utilise l'ObjectId de 12 octets du champ _id comme clé primaire pour identifier les documents de manière unique. Cependant, il peut y avoir des scénarios où nous souhaitons que le champ _id ait une valeur auto-incrémentée autre que l'ObjectId.

Comme il ne s'agit pas d'une fonctionnalité par défaut dans MongoDB, nous allons réaliser cette fonctionnalité de manière programmatique en utilisant une collection de compteurs comme le suggère la documentation de MongoDB.

## Utilisation de la collection de compteurs

Considérons le document de produits suivant. Nous voulons que le champ _id soit une séquence d'entiers auto-incrémentés commençant par 1,2,3,4 jusqu'à n.

```
{
    "_id":1,
    "product_name": "Apple iPhone",
    "category": "mobiles"
}
```

Pour cela, créez une collection de compteurs, qui conservera la trace de la dernière valeur de séquence pour tous les champs de séquence.

```
>db.createCollection("counters")
```

Maintenant, nous allons insérer le document suivant dans la collection de compteurs avec productid comme sa clé -

```
> db.counters.insert({
	"_id":"productid",
	"sequence_value": 0
})
WriteResult({ "nInserted" : 1 })
>
```

Le champ sequence_value garde la trace de la dernière valeur de la séquence.

Utilisez le code suivant pour insérer ce document de séquence dans la collection de compteurs -.

```
>db.counters.insert({_id:"productid",sequence_value:0})
```

## Créer une fonction Javascript

Maintenant, nous allons créer une fonction getNextSequenceValue qui prendra le nom de la séquence en entrée, incrémentera le numéro de séquence de 1 et renverra le numéro de séquence mis à jour. Dans notre cas, le nom de la séquence est productid.

```js
>function getNextSequenceValue(sequenceName){
    var sequenceDocument = db.counters.findAndModify({
        query:{_id: sequenceName },
        update: {$inc:{sequence_value:1}},
        new:true
    });
    return sequenceDocument.sequence_value;
}
```

## Utilisation de la fonction Javascript

Nous allons maintenant utiliser la fonction getNextSequenceValue en créant un nouveau document et en affectant la valeur de la séquence renvoyée au champ _id du document.

Insérez deux documents types en utilisant le code suivant -

```
>db.products.insert({
    "_id":getNextSequenceValue("productid"),
    "product_name":"Apple iPhone",
    "category":"mobiles"
})
>db.products.insert({
    "_id":getNextSequenceValue("productid"),
    "product_name":"Samsung S3",
    "category":"mobiles"
})
```

Comme vous pouvez le constater, nous avons utilisé la fonction getNextSequenceValue pour définir la valeur du champ _id.

Pour vérifier la fonctionnalité, allons chercher les documents en utilisant la commande find -.

```
>db.products.find()
```

La requête ci-dessus a retourné les documents suivants ayant le champ _id auto-incrémenté -.

```
{ "_id" : 1, "product_name" : "Apple iPhone", "category" : "mobiles"}
{ "_id" : 2, "product_name" : "Samsung S3", "category" : "mobiles" }
```