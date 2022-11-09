Nous avons inséré le document suivant dans la collection nommée "users" comme indiqué ci-dessous.

```
db.users.insert(
	{
		"address": {
			"city": "Los Angeles",
			"state": "California",
			"pincode": "123"
		},
		"tags": [
			"music",
			"cricket",
			"blogs"
		],
		"name": "Tom Benzamin"
	}
)
```

Le document ci-dessus contient un sous-document d'adresse et un tableau de balises.

## Indexation des champs d'un tableau

Supposons que nous voulions rechercher des documents d'utilisateurs en fonction des balises de l'utilisateur. Pour cela, nous allons créer un index sur le tableau des tags dans la collection.

La création d'un index sur un tableau crée à son tour des entrées d'index distinctes pour chacun de ses champs. Ainsi, dans notre cas, lorsque nous créons un index sur le tableau des tags, des index séparés seront créés pour les valeurs musique, cricket et blogs.

Pour créer un index sur un tableau de balises, utilisez le code suivant -

```
>db.users.createIndex({"tags":1})
{
"createdCollectionAutomatically" : false,
"numIndexesBefore" : 2,
"numIndexesAfter" : 3,
"ok" : 1
}
>
```

Après avoir créé l'index, nous pouvons effectuer une recherche sur le champ des tags de la collection comme ceci -

```
> db.users.find({tags:"cricket"}).pretty()
{
	"_id" : ObjectId("5dd7c927f1dd4583e7103fdf"),
	"address" : {
		"city" : "Los Angeles",
		"state" : "California",
		"pincode" : "123"
	},
	"tags" : [
		"music",
		"cricket",
		"blogs"
	],
	"name" : "Tom Benzamin"
}
>
```

Pour vérifier que l'indexation correcte est utilisée, utilisez la commande explain suivante : -.

```
>db.users.find({tags:"cricket"}).explain()
```

Cela vous donne le résultat suivant -

```
{
	"queryPlanner" : {
		"plannerVersion" : 1,
		"namespace" : "mydb.users",
		"indexFilterSet" : false,
		"parsedQuery" : {
			"tags" : {
				"$eq" : "cricket"
			}
		},
		"queryHash" : "9D3B61A7",
		"planCacheKey" : "04C9997B",
		"winningPlan" : {
			"stage" : "FETCH",
			"inputStage" : {
				"stage" : "IXSCAN",
				"keyPattern" : {
					"tags" : 1
				},
				"indexName" : "tags_1",
				"isMultiKey" : false,
				"multiKeyPaths" : {
					"tags" : [ ]
				},
				"isUnique" : false,
				"isSparse" : false,
				"isPartial" : false,
				"indexVersion" : 2,
				"direction" : "forward",
				"indexBounds" : {
					"tags" : [
						"[\"cricket\", \"cricket\"]"
					]
				}
			}
		},
		"rejectedPlans" : [ ]
	},
	"serverInfo" : {
		"host" : "Krishna",
		"port" : 27017,
		"version" : "4.2.1",
		"gitVersion" : "edf6d45851c0b9ee15548f0f847df141764a317e"
	},
	"ok" : 1
}
>
```

La commande ci-dessus a donné comme résultat "cursor" : "BtreeCursor tags_1" ce qui confirme que l'indexation correcte est utilisée.

## Indexation des champs de sous-documents

Supposons que nous voulions rechercher des documents sur la base des champs ville, état et code postal. Comme tous ces champs font partie du champ du sous-document adresse, nous allons créer un index sur tous les champs du sous-document.

Pour créer un index sur les trois champs du sous-document, utilisez le code suivant -

```
>db.users.createIndex({"address.city":1,"address.state":1,"address.pincode":1})
{
	"numIndexesBefore" : 4,
	"numIndexesAfter" : 4,
	"note" : "all indexes already exist",
	"ok" : 1
}
>
```

Une fois que l'index est créé, nous pouvons rechercher n'importe quel champ de sous-document en utilisant cet index comme suit : -

```
> db.users.find({"address.city":"Los Angeles"}).pretty()
{
	"_id" : ObjectId("5dd7c927f1dd4583e7103fdf"),
	"address" : {
		"city" : "Los Angeles",
		"state" : "California",
		"pincode" : "123"
	},
	"tags" : [
		"music",
		"cricket",
		"blogs"
	],
	"name" : "Tom Benzamin"
} 
```

N'oubliez pas que l'expression de la requête doit suivre l'ordre de l'index spécifié. Ainsi, l'index créé ci-dessus prendrait en charge les requêtes suivantes : - 1.

```
>db.users.find({"address.city":"Los Angeles","address.state":"California"}).pretty()
{
	"_id" : ObjectId("5dd7c927f1dd4583e7103fdf"),
	"address" : {
		"city" : "Los Angeles",
		"state" : "California",
		"pincode" : "123"
	},
	"tags" : [
		"music",
		"cricket",
		"blogs"
	],
	"name" : "Tom Benzamin"
}
>
```