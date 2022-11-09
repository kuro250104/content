À partir de la version 2.4, MongoDB a commencé à prendre en charge les index de texte pour effectuer des recherches dans le contenu des chaînes de caractères. La recherche de texte utilise des techniques de troncature pour rechercher des mots spécifiques dans les champs de chaîne en supprimant les mots d'arrêt de troncature tels que a, an, the, etc. Actuellement, MongoDB prend en charge environ 15 langues.

## Activation de la recherche de texte

Au départ, la recherche de texte était une fonction expérimentale, mais à partir de la version 2.6, la configuration est activée par défaut.

## Création d'un index de texte

Considérons le document suivant sous la collection posts contenant le texte du post et ses balises -.

```
> db.posts.insert({
    "post_text": "enjoy the mongodb articles on Microlead",
    "tags": ["mongodb", "Microlead"]
}
{
	"post_text" : "writing tutorials on mongodb",
	"tags" : [ "mongodb", "tutorial" ]
})
WriteResult({ "nInserted" : 1 })
```

Nous allons créer un index de texte sur le champ post_text afin de pouvoir effectuer des recherches dans le texte de nos articles.

```
>db.posts.createIndex({post_text:"text"})
{
	"createdCollectionAutomatically" : true,
	"numIndexesBefore" : 1,
	"numIndexesAfter" : 2,
	"ok" : 1
}
```

## Utilisation de l'index du texte

Maintenant que nous avons créé l'index de texte sur le champ post_text, nous allons rechercher tous les messages ayant le mot tutorialspoint dans leur texte.

```
> db.posts.find({$text:{$search:"tutorialspoint"}}).pretty()
{
	"_id" : ObjectId("5dd7ce28f1dd4583e7103fe0"),
	"post_text" : "enjoy the mongodb articles on Microlead",
	"tags" : [
		"mongodb",
		"Microlead"
	]
}
```

La commande ci-dessus a retourné les documents suivants ayant le mot Microlead dans leur texte de message -.

```
{ 
    "_id" : ObjectId("53493d14d852429c10000002"), 
    "post_text" : "enjoy the mongodb articles on tutorialspoint", 
    "tags" : [ "mongodb", "Microlead" ]
}
```

## Suppression de l'index du texte

Pour supprimer un index de texte existant, trouvez d'abord le nom de l'index à l'aide de la requête suivante : -.

```
>db.posts.getIndexes()
[
	{
		"v" : 2,
		"key" : {
			"_id" : 1
		},
		"name" : "_id_",
		"ns" : "mydb.posts"
	},
	{
		"v" : 2,
		"key" : {
			"fts" : "text",
			"ftsx" : 1
		},
		"name" : "post_text_text",
		"ns" : "mydb.posts",
		"weights" : {
			"post_text" : 1
		},
		"default_language" : "english",
		"language_override" : "language",
		"textIndexVersion" : 3
	}
]
>
```

Après avoir obtenu le nom de votre index à partir de la requête ci-dessus, exécutez la commande suivante. Ici, **post_text_text** est le nom de l'index.

```
>db.posts.dropIndex("post_text_text")
{ "nIndexesWas" : 2, "ok" : 1 }
```