Dans ce chapitre, nous allons voir comment créer une collection en utilisant MongoDB.

## La méthode createCollection()

MongoDB ```db.createCollection(name, options)``` est utilisé pour créer une collection.

### Syntaxe

La syntaxe de base de la commande ```createCollection()``` est la suivante : -

```
db.createCollection(name, options)
```

Dans la commande, **name** est le nom de la collection à créer. **Options** est un document et est utilisé pour spécifier la configuration de la collection.

| **Paramètre** | **Type** | **Description** |
| --- | --- | --- |
| Name | String | Nom de la collection à créer |
| Options | Document | (Facultatif) Spécifiez les options concernant la taille de la mémoire et l'indexation. |

Le paramètre Options est facultatif, vous devez donc indiquer uniquement le nom de la collection. Vous trouverez ci-dessous la liste des options que vous pouvez utiliser.

| **Champs** | **Type** | **Description** |
| --- | --- | --- |
| capped | Boolean | (Facultatif) Si true, active une collection plafonnée. Une collection plafonnée est une collection de taille fixe qui écrase automatiquement ses entrées les plus anciennes lorsqu'elle atteint sa taille maximale. Si vous spécifiez true, vous devez également spécifier le paramètre size. |
| autoIndexId | Boolean | (Facultatif) Si true, crée automatiquement un index sur le champ _id.s La valeur par défaut est false. |
| size | number | (Facultatif) Spécifie une taille maximale en octets pour une collection plafonnée. Si capped est true, vous devez également spécifier ce champ. |
| max | number | (Facultatif) Spécifie le nombre maximum de documents autorisés dans la collection plafonnée. |

Lors de l'insertion du document, MongoDB vérifie d'abord le champ size de la collection plafonnée, puis le champ max.

### Exemples

La syntaxe de base de la méthode ```createCollection()``` sans options est la suivante -

```
>use test
switched to db test
>db.createCollection("mycollection")
{ "ok" : 1 }
>
```

Vous pouvez vérifier la collection créée en utilisant la commande ```show collections```.

```
>show collections
mycollection
system.indexes
```

L'exemple suivant montre la syntaxe de la méthode ```createCollection()``` avec quelques options importantes -

```
> db.createCollection("mycol", { capped : true, autoIndexID : true, size : 6142800, max : 10000 } ){
"ok" : 0,
"errmsg" : "BSON field 'create.autoIndexID' is an unknown field.",
"code" : 40415,
"codeName" : "Location40415"
}
>
```

Dans MongoDB, vous n'avez pas besoin de créer une collection. MongoDB crée une collection automatiquement, lorsque vous insérez un document.

```
>db.Microlead.insert({"name" : "Microlead"}),
WriteResult({ "nInserted" : 1 })
>show collections
mycol
mycollection
system.indexes
Microlead
>
```