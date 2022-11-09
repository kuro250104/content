Les index permettent de résoudre efficacement les requêtes. Sans index, MongoDB doit parcourir chaque document d'une collection pour sélectionner ceux qui correspondent à l'énoncé de la requête. Ce balayage est très inefficace et demande à MongoDB de traiter un grand volume de données.

Les index sont des structures de données spéciales, qui stockent une petite partie de l'ensemble des données sous une forme facile à parcourir. L'index stocke la valeur d'un champ ou d'un ensemble de champs spécifiques, classés par la valeur du champ spécifié dans l'index.

## La méthode createIndex()

Pour créer un index, vous devez utiliser la méthode ```createIndex()``` de MongoDB.

### Syntaxe

La syntaxe de base de la méthode ```createIndex()``` est la suivante.

```
>db.COLLECTION_NAME.createIndex({KEY:1})
```

Ici, key est le nom du champ sur lequel vous voulez créer l'index et 1 est pour l'ordre ascendant. Pour créer un index dans l'ordre décroissant, vous devez utiliser -1.

### Exemple

```
>db.mycol.createIndex({"title":1})
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 1,
	"numIndexesAfter" : 2,
	"ok" : 1
}
>
```

Dans la méthode ```createIndex()``` vous pouvez passer plusieurs champs, pour créer un index sur plusieurs champs.

```
>db.mycol.createIndex({"title":1,"description":-1})
>
```

Cette méthode accepte également une liste d'options (qui sont facultatives). Voici la liste -

| **Paramètre** | **Type** | **Description** |
| --- | --- | --- |
| background | Boolean | Construit l'index en arrière-plan afin que la construction d'un index ne bloque pas les autres activités de la base de données. Spécifiez true pour construire en arrière-plan. La valeur par défaut est false. |
| unique | Boolean | Crée un index unique afin que la collection n'accepte pas l'insertion de documents dont la ou les clés d'indexation correspondent à une valeur existante dans l'index. Spécifiez true pour créer un index unique. La valeur par défaut est false. |
| name | String | Le nom de l'index. Si rien n'est spécifié, MongoDB génère un nom d'index en concaténant les noms des champs indexés et l'ordre de tri. |
| sparse | Boolean | Si c'est vrai, l'index ne référence que les documents ayant le champ spécifié. Ces index utilisent moins d'espace mais se comportent différemment dans certaines situations (notamment les tris). La valeur par défaut est false. |
| expireAfterSeconds | integer | Spécifie une valeur, en secondes, comme TTL pour contrôler la durée pendant laquelle MongoDB conserve les documents dans cette collection. |
| weights | document | Le poids est un nombre allant de 1 à 99 999 et indique l'importance du champ par rapport aux autres champs indexés en termes de score. |
| default_language | String | Pour un index de texte, la langue qui détermine la liste des mots d'arrêt et les règles pour le stemmer et le tokenizer. La valeur par défaut est l'anglais. |
| language_override | String | Pour un index de texte, indiquez le nom du champ dans le document qui contient, la langue pour remplacer la langue par défaut. La valeur par défaut est la langue. |

## La méthode dropIndex()

Vous pouvez supprimer un index particulier en utilisant la méthode dropIndex() de MongoDB.

### Syntaxe

La syntaxe de base de la méthode ```DropIndex()``` est la suivante.

```
>db.COLLECTION_NAME.dropIndex({KEY:1})
```

Ici, key est le nom du fichier sur lequel vous voulez créer l'index et 1 est pour l'ordre ascendant. Pour créer un index dans l'ordre décroissant, vous devez utiliser -1.

### Exemple

```
> db.mycol.dropIndex({"title":1})
{
	"ok" : 0,
	"errmsg" : "can't find index with key: { title: 1.0 }",
	"code" : 27,
	"codeName" : "IndexNotFound"
}
```

## La méthode dropIndexes()

Cette méthode supprime plusieurs index (spécifiés) sur une collection.

### Syntaxe

La syntaxe de base de la méthode ```DropIndexes()``` est la suivante

```
>db.COLLECTION_NAME.dropIndexes()
```

### Exemple

Supposons que nous ayons créé 2 index dans la collection mycol nommée, comme indiqué ci-dessous.

```
> db.mycol.createIndex({"title":1,"description":-1})
```

L'exemple suivant supprime les index de mycol - créés ci-dessus.

```
>db.mycol.dropIndexes({"title":1,"description":-1})
{ "nIndexesWas" : 2, "ok" : 1 }
>
```

## La méthode getIndexes()

Cette méthode retourne la description de tous les index de la collection.

### Syntaxe

Voici la syntaxe de base de la méthode ```getIndexes()``` -

```
db.COLLECTION_NAME.getIndexes()
```

### Exemple

Supposons que nous ayons créé 2 index dans la collection mycol nommée, comme indiqué ci-dessous.

```
> db.mycol.createIndex({"title":1,"description":-1})
```

L'exemple suivant récupère tous les index de la collection mycol -.

```
> db.mycol.getIndexes()
[
	{
		"v" : 2,
		"key" : {
			"_id" : 1
		},
		"name" : "_id_",
		"ns" : "test.mycol"
	},
	{
		"v" : 2,
		"key" : {
			"title" : 1,
			"description" : -1
		},
		"name" : "title_1_description_-1",
		"ns" : "test.mycol"
	}
]
>
```