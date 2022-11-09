Les méthodes ```update()``` et ```save()``` de MongoDB sont utilisées pour mettre à jour un document dans une collection. La méthode ```update()``` met à jour les valeurs du document existant tandis que la méthode ```save()``` remplace le document existant par le document transmis par la méthode ```save()```.

## Méthode MongoDB Update()

La méthode ```update()``` met à jour les valeurs du document existant.

### Syntaxe

La syntaxe de base de la méthode ```update()``` est la suivante -

```
>db.COLLECTION_NAME.update(SELECTION_CRITERIA, UPDATED_DATA)
```

### Exemple

Considérons que la collection mycol a les données suivantes.

```
{ "_id" : ObjectId(5983548781331adf45ec5), "title":"MongoDB Overview"}
{ "_id" : ObjectId(5983548781331adf45ec6), "title":"NoSQL Overview"}
{ "_id" : ObjectId(5983548781331adf45ec7), "title":"Microlead Overview"}
```

L'exemple suivant définira le nouveau titre 'New MongoDB Tutorial' des documents dont le titre est 'MongoDB Overview'.

```
>db.mycol.update({'title':'MongoDB Overview'},{$set:{'title':'New MongoDB Tutorial'}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
>db.mycol.find()
{ "_id" : ObjectId(5983548781331adf45ec5), "title":"New MongoDB Tutorial"}
{ "_id" : ObjectId(5983548781331adf45ec6), "title":"NoSQL Overview"}
{ "_id" : ObjectId(5983548781331adf45ec7), "title":"Microlead Overview"}
>
```

Par défaut, MongoDB ne met à jour qu'un seul document. Pour mettre à jour plusieurs documents, vous devez définir le paramètre "multi" à true.

```
>db.mycol.update({'title':'MongoDB Overview'},
    {$set:{'title':'New MongoDB Tutorial'}},{multi:true})
```

## Méthode MongoDB Save()

La méthode ```save()``` remplace le document existant par le nouveau document transmis dans la méthode ```save()```.

### Syntaxe

La syntaxe de base de la méthode MongoDB ```save()``` est présentée ci-dessous -

```
>db.COLLECTION_NAME.save({_id:ObjectId(),NEW_DATA})
```

### Exemple

L'exemple suivant remplacera le document avec l'_id '5983548781331adf45ec5'.

```
>db.mycol.save(
    {
        "_id" : ObjectId("507f191e810c19729de860ea"), 
        "title":"Microlead New Topic",
        "by":"Microlead"
    }
)
WriteResult({
	"nMatched" : 0,
	"nUpserted" : 1,
	"nModified" : 0,
	"_id" : ObjectId("507f191e810c19729de860ea")
})
>db.mycol.find()
{ "_id" : ObjectId("507f191e810c19729de860e6"), "title":"Microlead New Topic",
    "by":"Microlead"}
{ "_id" : ObjectId("507f191e810c19729de860e6"), "title":"NoSQL Overview"}
{ "_id" : ObjectId("507f191e810c19729de860e6"), "title":"Microlead Overview"}
>
```

## Méthode MongoDB findOneAndUpdate()

La méthode ```findOneAndUpdate()``` met à jour les valeurs du document existant.

### Syntaxe

La syntaxe de base de la méthode ```findOneAndUpdate()``` est la suivante -

```
>db.COLLECTION_NAME.findOneAndUpdate(SELECTIOIN_CRITERIA, UPDATED_DATA)
```

### Exemple

Supposons que nous ayons créé une collection nommée empDetails et que nous y ayons inséré trois documents, comme indiqué ci-dessous.

```
> db.empDetails.insertMany(
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

L'exemple suivant met à jour les valeurs d'âge et d'email du document avec le nom 'Radhika'.

```
> db.empDetails.findOneAndUpdate(
	{First_Name: 'Radhika'},
	{ $set: { Age: '30',e_mail: 'radhika_newemail@gmail.com'}}
)
{
	"_id" : ObjectId("5dd6636870fb13eec3963bf5"),
	"First_Name" : "Radhika",
	"Last_Name" : "Sharma",
	"Age" : "30",
	"e_mail" : "radhika_newemail@gmail.com",
	"phone" : "9000012345"
}
```

## Méthode MongoDB updateOne()

Cette méthode met à jour un seul document qui correspond au filtre donné.

### Syntaxe

La syntaxe de base de la méthode ```updateOne()``` est la suivante -

```
>db.COLLECTION_NAME.updateOne(<filter>, <update>)
```

### Exemple

```
> db.empDetails.updateOne(
	{First_Name: 'Radhika'},
	{ $set: { Age: '30',e_mail: 'radhika_newemail@gmail.com'}}
)
{ "acknowledged" : true, "matchedCount" : 1, "modifiedCount" : 0 }
>
```

## Méthode MongoDB updateMany()

La méthode ```updateMany()``` met à jour tous les documents qui correspondent au filtre donné.

### Syntaxe

The basic syntax of ```updateMany()``` method is as follows −

```
>db.COLLECTION_NAME.update(<filter>, <update>)
```

### Exemple

```
> db.empDetails.updateMany(
	{Age:{ $gt: "25" }},
	{ $set: { Age: '00'}}
)
{ "acknowledged" : true, "matchedCount" : 2, "modifiedCount" : 2 }
```

Vous pouvez voir les valeurs mises à jour si vous récupérez le contenu du document à l'aide de la méthode find, comme indiqué ci-dessous.

```
> db.empDetails.find()
{ "_id" : ObjectId("5dd6636870fb13eec3963bf5"), "First_Name" : "Radhika", "Last_Name" : "Sharma", "Age" : "00", "e_mail" : "radhika_newemail@gmail.com", "phone" : "9000012345" }
{ "_id" : ObjectId("5dd6636870fb13eec3963bf6"), "First_Name" : "Rachel", "Last_Name" : "Christopher", "Age" : "00", "e_mail" : "Rachel_Christopher.123@gmail.com", "phone" : "9000054321" }
{ "_id" : ObjectId("5dd6636870fb13eec3963bf7"), "First_Name" : "Fathima", "Last_Name" : "Sheik", "Age" : "24", "e_mail" : "Fathima_Sheik.123@gmail.com", "phone" : "9000054321" }
>
```