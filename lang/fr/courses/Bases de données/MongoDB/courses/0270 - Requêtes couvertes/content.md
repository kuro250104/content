Dans ce chapitre, nous allons apprendre les requêtes couvertes.

## Qu'est-ce qu'une requête couverte ?

Selon la documentation officielle de MongoDB, une requête couverte est une requête dans laquelle -

- Tous les champs de la requête font partie d'un index.
- Tous les champs retournés dans la requête sont dans le même index.

Étant donné que tous les champs présents dans la requête font partie d'un index, MongoDB fait correspondre les conditions de la requête et renvoie le résultat en utilisant le même index sans avoir à chercher dans les documents. Comme les index sont présents dans la mémoire vive, l'extraction de données à partir des index est beaucoup plus rapide que l'extraction de données par balayage des documents.

## Utilisation des requêtes couvertes

Pour tester les requêtes couvertes, considérez le document suivant dans la collection d'utilisateurs -

```
{
    "_id": ObjectId("53402597d852426020000003"),
    "contact": "987654321",
    "dob": "01-01-1991",
    "gender": "M",
    "name": "Tom Benzamin",
    "user_name": "tombenzamin"
}
```

Nous allons d'abord créer un index composé pour la collection users sur les champs **gender** et **user_name** à l'aide de la requête suivante : -.

```
>db.users.createIndex({gender:1,user_name:1})
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 1,
	"numIndexesAfter" : 2,
	"ok" : 1
}
```

Maintenant, cet index couvrira la requête suivante -

```
>db.users.find({gender:"M"},{user_name:1,_id:0})
{ "user_name" : "tombenzamin" }
```

En d'autres termes, pour la requête ci-dessus, MongoDB ne va pas chercher dans les documents de la base de données. Au lieu de cela, il va chercher les données requises dans les données indexées, ce qui est très rapide.

Puisque notre index ne comprend pas le champ **_id**, nous l'avons explicitement exclu du jeu de résultats de notre requête, car MongoDB retourne par défaut le champ **_id** dans chaque requête. Ainsi, la requête suivante n'aurait pas été couverte par l'index créé ci-dessus.

```
>db.users.find({gender:"M"},{user_name:1})
{ "_id" : ObjectId("53402597d852426020000003"), "user_name" : "tombenzamin" }
```

Enfin, n'oubliez pas qu'un index ne peut pas couvrir une requête si -

- L'un des champs indexés est un tableau
- N'importe lequel des champs indexés est un sous-document