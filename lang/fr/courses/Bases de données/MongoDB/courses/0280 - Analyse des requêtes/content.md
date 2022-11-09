L'analyse des requêtes est un aspect très important pour mesurer l'efficacité de la conception de la base de données et de l'indexation. Nous allons découvrir les requêtes ```$explain``` et ```$hint```, fréquemment utilisées.

## Utilisation de $explain

L'opérateur $explain fournit des informations sur la requête, les index utilisés dans une requête et d'autres statistiques. Il est très utile pour analyser le degré d'optimisation de vos index.

Dans le dernier chapitre, nous avions déjà créé un index pour la collection users sur les champs gender et user_name en utilisant la requête suivante -

```
>db.users.createIndex({gender:1,user_name:1})
{
	"numIndexesBefore" : 2,
	"numIndexesAfter" : 2,
	"note" : "all indexes already exist",
	"ok" : 1
}
```

Nous allons maintenant utiliser ```$explain``` sur la requête suivante -

```
>db.users.find({gender : "M"},{user_name:1,_id:0}).explain()
```

La requête ```explain()``` ci-dessus renvoie le résultat analysé suivant -

```
{
	"queryPlanner" : {
		"plannerVersion" : 1,
		"namespace" : "mydb.users",
		"indexFilterSet" : false,
		"parsedQuery" : {
			"gender" : {
				"$eq" : "M"
			}
		},
		"queryHash" : "B4037D3C",
		"planCacheKey" : "DEAAE17C",
		"winningPlan" : {
			"stage" : "PROJECTION_COVERED",
			"transformBy" : {
				"user_name" : 1,
				"_id" : 0
			},
			"inputStage" : {
				"stage" : "IXSCAN",
				"keyPattern" : {
					"gender" : 1,
					"user_name" : 1
				},
				"indexName" : "gender_1_user_name_1",
				"isMultiKey" : false,
				"multiKeyPaths" : {
					"gender" : [ ],
					"user_name" : [ ]
				},
				"isUnique" : false,
				"isSparse" : false,
				"isPartial" : false,
				"indexVersion" : 2,
				"direction" : "forward",
				"indexBounds" : {
					"gender" : [
						"[\"M\", \"M\"]"
					],
					"user_name" : [
						"[MinKey, MaxKey]"
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
```

Nous allons à présent examiner les champs de cet ensemble de résultats.

- La valeur vraie de **indexOnly** indique que cette requête a utilisé l'indexation.
- Le champ **curseur** spécifie le type de curseur utilisé. Le type BTreeCursor indique qu'un index a été utilisé et donne également le nom de l'index utilisé. BasicCursor indique qu'un balayage complet a été effectué sans utiliser d'index.
- **n** indique le nombre de documents correspondants retournés.
- **nscannedObjects** indique le nombre total de documents numérisés.
- **nscanned** indique le nombre total de documents ou d'entrées d'index numérisés.

## Utilisation de $hint

L'opérateur ```$hint``` force l'optimiseur de requêtes à utiliser l'index spécifié pour exécuter une requête. Ceci est particulièrement utile lorsque vous souhaitez tester les performances d'une requête avec différents index. Par exemple, la requête suivante spécifie l'index sur les champs gender et user_name qui doit être utilisé pour cette requête -

```
>db.users.find({gender:"M"},{user_name:1,_id:0}).hint({gender:1,user_name:1})
{ "user_name" : "tombenzamin" }
```

Pour analyser la requête ci-dessus à l'aide de $explain -

```
>db.users.find({gender:"M"},{user_name:1,_id:0}).hint({gender:1,user_name:1}).explain()
```

Ce qui vous donne le résultat suivant -

```
{
	"queryPlanner" : {
		"plannerVersion" : 1,
		"namespace" : "mydb.users",
		"indexFilterSet" : false,
		"parsedQuery" : {
			"gender" : {
				"$eq" : "M"
			}
		},
		"queryHash" : "B4037D3C",
		"planCacheKey" : "DEAAE17C",
		"winningPlan" : {
			"stage" : "PROJECTION_COVERED",
			"transformBy" : {
				"user_name" : 1,
				"_id" : 0
			},
			"inputStage" : {
				"stage" : "IXSCAN",
				"keyPattern" : {
					"gender" : 1,
					"user_name" : 1
				},
				"indexName" : "gender_1_user_name_1",
				"isMultiKey" : false,
				"multiKeyPaths" : {
					"gender" : [ ],
					"user_name" : [ ]
				},
				"isUnique" : false,
				"isSparse" : false,
				"isPartial" : false,
				"indexVersion" : 2,
				"direction" : "forward",
				"indexBounds" : {
					"gender" : [
						"[\"M\", \"M\"]"
					],
					"user_name" : [
						"[MinKey, MaxKey]"
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
		109
		"gitVersion" : "edf6d45851c0b9ee15548f0f847df141764a317e"
	},
	"ok" : 1
}
```