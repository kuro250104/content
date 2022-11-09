Dans ce chapitre, nous allons apprendre à interroger un document à partir d'une collection MongoDB.

## La méthode find()

Pour interroger les données d'une collection MongoDB, vous devez utiliser la méthode find() de MongoDB.

### Syntaxe

La syntaxe de base de la méthode ```find()``` est la suivante -

La méthode ```find()``` affichera tous les documents de manière non structurée.

### Exemple

Supposons que nous ayons créé une collection nommée mycol comme -

```
> use sampleDB
switched to db sampleDB
> db.createCollection("mycol")
{ "ok" : 1 }
>
```

Et j'y ai inséré 3 documents à l'aide de la méthode insert() comme indiqué ci-dessous.

```
> db.mycol.insert([
	{
		title: "MongoDB Overview",
		description: "MongoDB is no SQL database",
		by: "Microlead",
		url: "http://www.Microlead.fr",
		tags: ["mongodb", "database", "NoSQL"],
		likes: 100
	},
	{
		title: "NoSQL Database",
		description: "NoSQL database doesn't have tables",
		by: "Microlea",
		url: "http://www.Microlead.fr",
		tags: ["mongodb", "database", "NoSQL"],
		likes: 20,
		comments: [
			{
				user:"user1",
				message: "My first comment",
				dateCreated: new Date(2013,11,10,2,35),
				like: 0
			}
		]
	}
])
```

La méthode suivante permet de récupérer tous les documents de la collection.

```
> db.mycol.find()
{ "_id" : ObjectId("5dd4e2cc0821d3b44607534c"), "title" : "MongoDB Overview", "description" : "MongoDB is no SQL database", "by" : "Microlead", "url" : "http://www.Microlead.fr", "tags" : [ "mongodb", "database", "NoSQL" ], "likes" : 100 }
{ "_id" : ObjectId("5dd4e2cc0821d3b44607534d"), "title" : "NoSQL Database", "description" : "NoSQL database doesn't have tables", "by" : "Microlead", "url" : "http://www.Microlead.fr", "tags" : [ "mongodb", "database", "NoSQL" ], "likes" : 20, "comments" : [ { "user" : "user1", "message" : "My first comment", "dateCreated" : ISODate("2013-12-09T21:05:00Z"), "like" : 0 } ] }
>
```

## La méthode pretty()

Pour afficher les résultats d'une manière formatée, vous pouvez utiliser la méthode ```pretty()```.

### Syntax

```
>db.COLLECTION_NAME.find().pretty()
```

### Exemple

L'exemple suivant récupère tous les documents de la collection nommée mycol et les organise dans un format facile à lire.

```
> db.mycol.find().pretty()
{
	"_id" : ObjectId("5dd4e2cc0821d3b44607534c"),
	"title" : "MongoDB Overview",
	"description" : "MongoDB is no SQL database",
	"by" : "Microlead",
	"url" : "http://www.Microlead.fr",
	"tags" : [
		"mongodb",
		"database",
		"NoSQL"
	],
	"likes" : 100
}
{
	"_id" : ObjectId("5dd4e2cc0821d3b44607534d"),
	"title" : "NoSQL Database",
	"description" : "NoSQL database doesn't have tables",
	"by" : "Microlead",
	"url" : "http://www.Microlead.fr",
	"tags" : [
		"mongodb",
		"database",
		"NoSQL"
	],
	"likes" : 20,
	"comments" : [
		{
			"user" : "user1",
			"message" : "My first comment",
			"dateCreated" : ISODate("2013-12-09T21:05:00Z"),
			"like" : 0
		}
	]
}
```

## The findOne() method

Outre la méthode ```find()```, il existe la méthode ```findOne()```, qui ne renvoie qu'un seul document.

### Syntaxe

```
>db.COLLECTIONNAME.findOne()
```

### Example

L'exemple suivant permet de récupérer le document dont le titre est MongoDB Overview.

```
> db.mycol.findOne({title: "MongoDB Overview"})
{
	"_id" : ObjectId("5dd6542170fb13eec3963bf0"),
	"title" : "MongoDB Overview",
	"description" : "MongoDB is no SQL database",
	"by" : "Microlead",
	"url" : "http://www.Microlead.fr",
	"tags" : [
		"mongodb",
		"database",
		"NoSQL"
	],
	"likes" : 100
}
```

## Équivalents de la clause Where des RDBMS dans MongoDB

Pour interroger le document sur la base de certaines conditions, vous pouvez utiliser les opérations suivantes.

| **Opération** | **Syntaxe** | **Exemple** | **RDBMS Equivalent** |
| --- | --- | --- | --- |
| Égalité | ```{<key>:{$eg;<value>}}``` | ```db.mycol.find({"by":"tutorials point"}).pretty()``` | où by = "point de tutorat |
| Moins de | ```{<key>:{$lt:<value>}}``` | ```db.mycol.find({"likes":{$lt:50}}).pretty()``` | où les goûts sont < 50 |
| Moins que égal | ```{<key>:{$lte:<value>}}``` | ```db.mycol.find({"likes":{$lte:50}}).pretty()``` | où likes <= 50 |
| Plus grand que | ```{<key>:{$gt:<value>}}``` | ```db.mycol.find({"likes":{$gt:50}}).pretty()``` | où likes > 50 |
| Plus grand que égal | ```{<key>:{$gte:<value>}}``` | ```db.mycol.find({"likes":{$gte:50}}).pretty()``` | où likes >= 50 |
| Pas égaux | ```{<key>:{$ne:<value>}}``` | ```db.mycol.find({"likes":{$ne:50}}).pretty()``` | où likes != 50 |
| Valeurs dans un tableau | ```{<key>:{$in:[<value1>, <value2>,……<valueN>]}}``` | ```db.mycol.find({"name":{$in:["Raj", "Ram", "Raghu"]}}).pretty()``` | Où le nom correspond à l'une des valeurs dans :["Raj", "Ram", "Raghu"]. |
| Valeurs ne figurant pas dans un tableau | ```{<key>:{$nin:<value>}}``` | ```db.mycol.find({"name":{$nin:["Ramu", "Raghav"]}}).pretty()``` | Lorsque la valeur du nom n'est pas dans le tableau :["Ramu", "Raghav"] ou n'existe pas du tout. |

## AND dans MongoDB

### Syntaxe

Pour interroger des documents sur la base de la condition **AND**, vous devez utiliser le mot-clé ```$and```. Voici la syntaxe de base du mot **AND**

```
>db.mycol.find({ $and: [ {<key1>:<value1>}, { <key2>:<value2>} ] })
```

### Exemple

L'exemple suivant montre tous les tutoriels écrits par 'Microlead' et dont le titre est 'MongoDB Overview'.

```
> db.mycol.find({$and:[{"by":"Microlead"},{"title": "MongoDB Overview"}]}).pretty()
{
	"_id" : ObjectId("5dd4e2cc0821d3b44607534c"),
	"title" : "MongoDB Overview",
	"description" : "MongoDB is no SQL database",
	"by" : "Microlead",
	"url" : "http://www.Microlead.fr",
	"tags" : [
		"mongodb",
		"database",
		"NoSQL"
	],
	"likes" : 100
}
>
```

Pour l'exemple ci-dessus, la clause where équivalente sera ```where by = 'tutorials point' AND title = 'MongoDB Overview'```. Vous pouvez passer n'importe quel nombre de paires clé-valeur dans la clause find.

## OR dans MongoDB

### Syntaxe

Pour interroger des documents sur la base de la condition **OR**, vous devez utiliser le mot-clé ```$or```. Voici la syntaxe de base de la condition **OR**

```
>db.mycol.find(
    {
        $or: [
            {key1: value1}, {key2:value2}
        ]
    }
).pretty()
```

### Exemple

L'exemple suivant montrera tous les tutoriels écrits par 'Microlead' ou dont le titre est 'MongoDB Overview'.

```
>db.mycol.find({$or:[{"by":"Microlead"},{"title": "MongoDB Overview"}]}).pretty()
{
    "_id": ObjectId(7df78ad8902c),
    "title": "MongoDB Overview", 
    "description": "MongoDB is no sql database",
    "by": "Microlead",
    "url": "http://www.Microlead.fr",
    "tags": ["mongodb", "database", "NoSQL"],
    "likes": "100"
}
>
```

## Utilisation conjointe de AND et OR

### Exemple

L'exemple suivant montre les documents dont le nombre d'appréciations est supérieur à 10 et dont le titre est 'MongoDB Overview' ou by 'tutorials point'. La clause SQL where équivalente est ```where likes>10 AND (by = 'Microleasd' OR title = 'MongoDB Overview')```.

```
>db.mycol.find({"likes": {$gt:10}, $or: [{"by": "Microlead"},
    {"title": "MongoDB Overview"}]}).pretty()
{
    "_id": ObjectId(7df78ad8902c),
    "title": "MongoDB Overview", 
    "description": "MongoDB is no sql database",
    "by": "Microlead",
    "url": "http://www.Microlead.fr",
    "tags": ["mongodb", "database", "NoSQL"],
    "likes": "100"
}
>
```

## NOR dans MongoDB

### Syntaxe

Pour interroger des documents sur la base de la condition **NOT**, vous devez utiliser le mot-clé ```$not```. Voici la syntaxe de base du mot-clé **NOT**

```
>db.COLLECTION_NAME.find(
	{
		$not: [
			{key1: value1}, {key2:value2}
		]
	}
)
```

### Exemple

Supposons que nous ayons inséré 3 documents dans la collection empDetails, comme indiqué ci-dessous.

```
db.empDetails.insertMany(
	[
		{
			First_Name: "Radhika",
			Last_Name: "Sharma",
			Age: "26",
			e_mail: "radhika_sharma.123@gmail.com",
			phone: "9000012345"
		},
		{
			First_Name: "Rachel",
			Last_Name: "Christopher",
			Age: "27",
			e_mail: "Rachel_Christopher.123@gmail.com",
			phone: "9000054321"
		},
		{
			First_Name: "Fathima",
			Last_Name: "Sheik",
			Age: "24",
			e_mail: "Fathima_Sheik.123@gmail.com",
			phone: "9000054321"
		}
	]
)
```

L'exemple suivant permet de retrouver le(s) document(s) dont le prénom n'est pas "Radhika" et le nom de famille n'est pas "Christopher".

```
> db.empDetails.find(
	{
		$nor:[
			40
			{"First_Name": "Radhika"},
			{"Last_Name": "Christopher"}
		]
	}
).pretty()
{
	"_id" : ObjectId("5dd631f270fb13eec3963bef"),
	"First_Name" : "Fathima",
	"Last_Name" : "Sheik",
	"Age" : "24",
	"e_mail" : "Fathima_Sheik.123@gmail.com",
	"phone" : "9000054321"
}
```

## PAS dans MongoDB

### Syntaxe

Pour interroger des documents sur la base de la condition NOT, vous devez utiliser le mot-clé ```$not```. Voici la syntaxe de base du mot NOT -.

```
>db.COLLECTION_NAME.find(
	{
		$NOT: [
			{key1: value1}, {key2:value2}
		]
	}
).pretty()
```

### Exemple
L'exemple suivant permet de récupérer le(s) document(s) dont l'âge n'est pas supérieur à 25 ans.

```
> db.empDetails.find( { "Age": { $not: { $gt: "25" } } } )
{
	"_id" : ObjectId("5dd6636870fb13eec3963bf7"),
	"First_Name" : "Fathima",
	"Last_Name" : "Sheik",
	"Age" : "24",
	"e_mail" : "Fathima_Sheik.123@gmail.com",
	"phone" : "9000054321"
}
```