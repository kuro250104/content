Dans ce chapitre, nous allons apprendre à insérer un document dans une collection MongoDB.

## La méthode insert()

Pour insérer des données dans une collection MongoDB, vous devez utiliser la méthode ```insert()``` ou ```save()``` de MongoDB.

### Syntaxe

La syntaxe de base de la commande ```insert()``` est la suivante -

```
>db.COLLECTION_NAME.insert(document)
```

### Example

```
> db.users.insert({
... _id : ObjectId("507f191e810c19729de860ea"),
... title: "MongoDB Overview",
... description: "MongoDB is no sql database",
... by: "Microlead",
... url: "http://www.Microlead.fr",
... tags: ['mongodb', 'database', 'NoSQL'],
... likes: 100
... })
WriteResult({ "nInserted" : 1 })
>
```

Ici mycol est le nom de notre collection, telle que créée dans le chapitre précédent. Si la collection n'existe pas dans la base de données, alors MongoDB va créer cette collection et y insérer un document.

Dans le document inséré, si nous ne spécifions pas le paramètre _id, alors MongoDB attribue un ObjectId unique pour ce document.

_id est un numéro hexadécimal de 12 octets unique pour chaque document d'une collection. Les 12 octets sont divisés comme suit -

```
_id: ObjectId(4 bytes timestamp, 3 bytes machine id, 2 bytes process id, 3 bytes incrementer)
```

Vous pouvez également passer un tableau de documents dans la méthode insert() comme indiqué ci-dessous :.

```
> db.createCollection("post")
> db.post.insert([
	{
		title: "MongoDB Overview",
		description: "MongoDB is no SQL database",
		by: "Microlead",
		url: "http://www.Mçicrolead.fr",
		tags: ["mongodb", "database", "NoSQL"],
		likes: 100
	},
	{
	title: "NoSQL Database",
	description: "NoSQL database doesn't have tables",
	by: "Microlead",
	url: "http://www.Mçicrolead.fr",
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
BulkWriteResult({
	"writeErrors" : [ ],
	"writeConcernErrors" : [ ],
	"nInserted" : 2,
	"nUpserted" : 0,
	"nMatched" : 0,
	"nModified" : 0,
	"nRemoved" : 0,
	"upserted" : [ ]
})
>
```

Pour insérer le document, vous pouvez également utiliser ```db.post.save(document)```. Si vous ne spécifiez pas _id dans le document, la méthode ```save()``` fonctionnera comme la méthode ```insert()```. Si vous spécifiez _id alors il remplacera toutes les données du document contenant _id comme spécifié dans la méthode ```save()```.

## The insertOne() method

Si vous devez insérer un seul document dans une collection, vous pouvez utiliser cette méthode.

### Syntaxe

La syntaxe de base de la commande ```insert()``` est la suivante -

```
>db.COLLECTION_NAME.insertOne(document)
```

### Exemple

L'exemple suivant crée une nouvelle collection nommée empDetails et insère un document en utilisant la méthode ```insertOne()```.

```
> db.createCollection("empDetails")
{ "ok" : 1 }
> db.empDetails.insertOne(
	{
		First_Name: "Radhika",
		Last_Name: "Sharma",
		Date_Of_Birth: "1995-09-26",
		e_mail: "radhika_sharma.123@gmail.com",
		phone: "9848022338"
	})
{
	"acknowledged" : true,
	"insertedId" : ObjectId("5dd62b4070fb13eec3963bea")
}
>
```

## La méthode insertMany()

Vous pouvez insérer plusieurs documents en utilisant la méthode insertMany(). Pour cette méthode, vous devez passer un tableau de documents.

### Exemple

L'exemple suivant insère trois documents différents dans la collection empDetails à l'aide de la méthode ```insertMany()```.

```
> db.empDetails.insertMany(
	[
		{
			First_Name: "Radhika",
			Last_Name: "Sharma",
			Date_Of_Birth: "1995-09-26",
			e_mail: "radhika_sharma.123@gmail.com",
			phone: "9000012345"
		},
		{
			First_Name: "Rachel",
			Last_Name: "Christopher",
			Date_Of_Birth: "1990-02-16",
			e_mail: "Rachel_Christopher.123@gmail.com",
			phone: "9000054321"
		},
		{
			First_Name: "Fathima",
			Last_Name: "Sheik",
			Date_Of_Birth: "1990-02-16",
			e_mail: "Fathima_Sheik.123@gmail.com",
			phone: "9000054321"
		}
	]
)
{
	"acknowledged" : true,
	"insertedIds" : [
		ObjectId("5dd631f270fb13eec3963bed"),
		ObjectId("5dd631f270fb13eec3963bee"),
		ObjectId("5dd631f270fb13eec3963bef")
	]
}
>
```