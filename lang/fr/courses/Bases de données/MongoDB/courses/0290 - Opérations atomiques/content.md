## Données du modèle pour les opérations atomiques

L'approche recommandée pour maintenir l'atomicité serait de conserver toutes les informations liées, qui sont fréquemment mises à jour, dans un seul document en utilisant des documents intégrés. Cela permet de s'assurer que toutes les mises à jour d'un même document sont atomiques.

Supposons que nous ayons créé une collection portant le nom de productDetails et que nous y ayons inséré un document comme indiqué ci-dessous.

```
>db.createCollection("products")
{ "ok" : 1 }
> db.productDetails.insert(
	{
		"_id":1,
		"product_name": "Samsung S3",
		"category": "mobiles",
		"product_total": 5,
		"product_available": 3,
		"product_bought_by": [
			{
				"customer": "john",
				"date": "7-Jan-2014"
			},
			{
				"customer": "mark",
				"date": "8-Jan-2014"
			}
		]
	}
)
WriteResult({ "nInserted" : 1 })
>
```

Dans ce document, nous avons intégré les informations du client qui achète le produit dans le champ product_bought_by. Maintenant, chaque fois qu'un nouveau client achète le produit, nous allons d'abord vérifier si le produit est encore disponible en utilisant le champ product_available. S'il est disponible, nous réduirons la valeur du champ product_available et nous insérerons le document incorporé du nouveau client dans le champ product_bought_by. Nous utiliserons la commande findAndModify pour cette fonctionnalité car elle recherche et met à jour le document en une seule fois.

```
>db.products.findAndModify({ 
    query:{_id:2,product_available:{$gt:0}}, 
    update:{ 
        $inc:{product_available:-1}, 
        $push:{product_bought_by:{customer:"rob",date:"9-Jan-2014"}} 
    }    
})
```

Notre approche du document incorporé et de l'utilisation de la requête findAndModify garantit que les informations relatives à l'achat du produit ne sont mises à jour que si le produit est disponible. Et l'ensemble de cette transaction étant dans la même requête, elle est atomique.
A l'inverse, considérons le scénario dans lequel nous pouvons avoir gardé séparément la disponibilité du produit et l'information sur qui a acheté le produit. Dans ce cas, nous allons d'abord vérifier si le produit est disponible en utilisant la première requête. Puis, dans la deuxième requête, nous mettrons à jour les informations sur l'achat. Cependant, il est possible qu'entre les exécutions de ces deux requêtes, un autre utilisateur ait acheté le produit et qu'il ne soit plus disponible. Sans le savoir, notre deuxième requête mettra à jour les informations d'achat sur la base du résultat de notre première requête. Cela rendra la base de données incohérente car nous avons vendu un produit qui n'est pas disponible.