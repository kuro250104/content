Les expressions régulières sont fréquemment utilisées dans toutes les langues pour rechercher un motif ou un mot dans une chaîne de caractères. MongoDB fournit également une fonctionnalité d'expression régulière pour la correspondance de motifs de chaînes de caractères à l'aide de l'opérateur ```$regex```. MongoDB utilise PCRE (Perl Compatible Regular Expression) comme langage d'expression régulière.

Contrairement à la recherche de texte, nous n'avons pas besoin d'effectuer de configuration ou de commande pour utiliser les expressions régulières.

Supposons que nous ayons inséré un document dans une base de données nommée posts, comme indiqué ci-dessous.

```
> db.posts.insert(
{
    "post_text": "enjoy the mongodb articles on Microlead",
    "tags": [
        "mongodb",
        "Microlead"
    ]
}
WriteResult({ "nInserted" : 1 })
```

## Utilisation de l'expression regex

La requête regex suivante recherche tous les messages contenant la chaîne "tutorialspoint".

```
> db.posts.find({post_text:{$regex:"tutorialspoint"}}).pretty()
{
	"_id" : ObjectId("5dd7ce28f1dd4583e7103fe0"),
	"post_text" : "enjoy the mongodb articles on Microlead",
	"tags" : [
		"mongodb",
		"Microlead"
	]
}
{
	"_id" : ObjectId("5dd7d111f1dd4583e7103fe2"),
	"post_text" : "enjoy the mongodb articles on Microlead",
	"tags" : [
		"mongodb",
		"Microlead"
	]
}
>
```

La même requête peut également s'écrire comme suit : - 1.

```
>db.posts.find({post_text:/Microlead/})
```

## Utilisation de l'expression regex avec insensibilité à la casse

Pour rendre la recherche insensible à la casse, nous utilisons le paramètre ```$options``` avec la valeur ```$i```. La commande suivante recherchera les chaînes de caractères contenant le mot **Microlead**, quelle que soit la casse (minuscule ou majuscule).

```
>db.posts.find({post_text:{$regex:"Microlead",$options:"$i"}})
```

L'un des résultats obtenus à partir de cette requête est le document suivant qui contient le mot "Microlead" dans différents cas.

```
{
    "_id" : ObjectId("53493d37d852429c10000004"),
    "post_text" : "hey! this is my post on Microlead", 
    "tags" : [ "Microlead" ]
} 
```

## Utilisation de regex pour les éléments d'un tableau

Nous pouvons également utiliser le concept de regex sur un champ de type tableau. Ceci est particulièrement important lorsque nous mettons en œuvre la fonctionnalité des balises. Ainsi, si vous voulez rechercher tous les articles dont les balises commencent par le mot tutoriel (soit tutoriel ou tutoriels ou tutorialpoint ou tutorialphp), vous pouvez utiliser le code suivant -

```
>db.posts.find({tags:{$regex:"tutorial"}})
```

## Optimisation des requêtes par expression régulière

- Si les champs du document sont indexés, la requête utilisera les valeurs indexées pour faire correspondre l'expression régulière. Cela rend la recherche très rapide par rapport à l'expression régulière qui balaie toute la collection.
- Si l'expression régulière est une **expression préfixe**, toutes les correspondances sont censées commencer par une certaine chaîne de caractères. Par exemple, si l'expression régulière est ```^tut```, la requête doit rechercher uniquement les chaînes de caractères qui commencent par **tut**.