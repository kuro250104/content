Les relations dans MongoDB représentent la façon dont divers documents sont logiquement liés les uns aux autres. Les relations peuvent être modélisées via les approches **Embedded** et **Referenced**. Ces relations peuvent être de type 1:1, 1:N, N:1 ou N:N.

Considérons le cas du stockage des adresses des utilisateurs. Ainsi, un utilisateur peut avoir plusieurs adresses, ce qui en fait une relation 1:N.

Voici un exemple de la structure d'un document **utilisateur**.

```
{
    "_id":ObjectId("52ffc33cd85242f436000001"),
    "name": "Tom Hanks",
    "contact": "987654321",
    "dob": "01-01-1991"
}
```

Voici un exemple de structure d'un document d'adresse.

```
{
    "_id":ObjectId("52ffc4a5d85242602e000000"),
    "building": "22 A, Indiana Apt",
    "pincode": 123456,
    "city": "Los Angeles",
    "state": "California"
}
```

## Modélisation des relations incorporées

Dans l'approche intégrée, nous incorporons le document d'adresse dans le document de l'utilisateur.

```
> db.users.insert({
	{
		"_id":ObjectId("52ffc33cd85242f436000001"),
		"contact": "987654321",
		"dob": "01-01-1991",
		"name": "Tom Benzamin",
		"address": [
			{
				"building": "22 A, Indiana Apt",
				"pincode": 123456,
				"city": "Los Angeles",
				"state": "California"
			},
			{
				"building": "170 A, Acropolis Apt",
				"pincode": 456789,
				"city": "Chicago",
				"state": "Illinois"
			}
		]
	}
})
```

Cette approche permet de conserver toutes les données connexes dans un seul document, ce qui en facilite l'extraction et la maintenance. L'ensemble du document peut être récupéré en une seule requête comme -

```
>db.users.findOne({"name":"Tom Benzamin"},{"address":1})
```

Notez que dans la requête ci-dessus, **db** et **users** sont respectivement la base de données et la collection.

L'inconvénient est que si la taille du document intégré continue de croître de manière excessive, cela peut avoir un impact sur les performances de lecture/écriture.

## Modélisation des relations référencées

Il s'agit de l'approche consistant à concevoir une relation normalisée. Dans cette approche, les documents d'utilisateur et d'adresse seront gérés séparément mais le document d'utilisateur contiendra un champ qui fera référence au champ id du document d'adresse.

```
{
    "_id":ObjectId("52ffc33cd85242f436000001"),
    "contact": "987654321",
    "dob": "01-01-1991",
    "name": "Tom Benzamin",
    "address_ids": [
        ObjectId("52ffc4a5d85242602e000000"),
        ObjectId("52ffc4a5d85242602e000001")
    ]
}
```

Comme indiqué ci-dessus, le document utilisateur contient le champ address_ids du tableau qui contient les ObjectIds des adresses correspondantes. En utilisant ces ObjectIds, nous pouvons interroger les documents d'adresse et obtenir les détails de l'adresse. Avec cette approche, nous aurons besoin de deux requêtes : la première pour récupérer les champs address_ids du document utilisateur et la seconde pour récupérer ces adresses dans la collection d'adresses.

```
>var result = db.users.findOne({"name":"Tom Benzamin"},{"address_ids":1})
>var addresses = db.address.find({"_id":{"$in":result["address_ids"]}})
```