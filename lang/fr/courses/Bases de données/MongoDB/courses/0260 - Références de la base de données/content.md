Comme nous l'avons vu dans le dernier chapitre sur les relations dans MongoDB, pour mettre en œuvre une structure de base de données normalisée dans MongoDB, nous utilisons le concept de relations référencées, également appelé références manuelles, dans lequel nous stockons manuellement l'identifiant du document référencé dans l'autre document. Cependant, dans les cas où un document contient des références provenant de différentes collections, nous pouvons utiliser les DBRefs de MongoDB.

## DBRefs et références manuelles

Comme exemple de scénario où nous utiliserions DBRefs au lieu de références manuelles, considérons une base de données où nous stockons différents types d'adresses (domicile, bureau, courrier, etc.) dans différentes collections (address_home, address_office, address_mailing, etc.). Maintenant, lorsqu'un document de la collection d'un utilisateur fait référence à une adresse, il doit également spécifier la collection à consulter en fonction du type d'adresse. Dans de tels scénarios où un document fait référence à des documents de plusieurs collections, nous devrions utiliser DBRefs.

## Utilisation de DBRefs

Il y a trois champs dans DBRefs -

- ```$ref``` − Ce champ spécifie la collection du document référencé
- ```$id``` − Ce champ spécifie le champ _id du document référencé
- ```$db``` − Il s'agit d'un champ facultatif qui contient le nom de la base de données dans laquelle se trouve le document référencé.

Prenons un exemple de document utilisateur comportant une adresse de champ DBRef comme indiqué dans l'extrait de code suivant -

```
{
    "_id":ObjectId("53402597d852426020000002"),
    "address": {
    "$ref": "address_home",
    "$id": ObjectId("534009e4d852427820000002"),
    "$db": "tutorialspoint"},
    "contact": "987654321",
    "dob": "01-01-1991",
    "name": "Tom Benzamin"
}
```

Le champ DBRef **adresse** indique ici que le document d'adresse référencé se trouve dans la collection **address_home** de la base de données **Microlead** et a un identifiant de 534009e4d852427820000002.

Le code suivant recherche dynamiquement dans la collection spécifiée par le paramètre ```$ref``` (address_home dans notre cas) un document dont l'id est spécifié par le paramètre ```$id``` dans DBRef.

```
>var user = db.users.findOne({"name":"Tom Benzamin"})
>var dbRef = user.address
>db[dbRef.$ref].findOne({"_id":(dbRef.$id)})
```

Le code ci-dessus renvoie le document d'adresse suivant, présent dans la collection **address_home**.

```
{
    "_id" : ObjectId("534009e4d852427820000002"),
    "building" : "22 A, Indiana Apt",
    "pincode" : 123456,
    "city" : "Los Angeles",
    "state" : "California"
}
```