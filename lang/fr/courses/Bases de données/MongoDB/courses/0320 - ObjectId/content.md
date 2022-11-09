Nous avons utilisé MongoDB Object Id dans tous les chapitres précédents. Dans ce chapitre, nous allons comprendre la structure de l'ObjectId.

Un ObjectId est un type BSON de 12 octets ayant la structure suivante -

- Les 4 premiers octets représentant les secondes depuis l'époque unix.
- Les 3 octets suivants sont l'identifiant de la machine
- Les 2 octets suivants sont constitués de l'identifiant du processus
- Les 3 derniers octets sont une valeur de compteur aléatoire.

MongoDB utilise les ObjectId comme valeur par défaut du champ _id de chaque document, qui est généré lors de la création de tout document. La combinaison complexe d'ObjectId rend tous les champs _id uniques.

## Création d'un nouvel ObjectId

Pour générer un nouvel ObjectId, utilisez le code suivant -

```
>newObjectId = ObjectId()
```

L'instruction ci-dessus renvoie l'identifiant généré de manière unique suivant -

```
ObjectId("5349b4ddd2781d08c09890f3")
```

Au lieu que MongoDB génère l'ObjectId, vous pouvez également fournir un identifiant de 12 octets.

```
>myObjectId = ObjectId("5349b4ddd2781d08c09890f4")
```

## Création de l'horodatage d'un document

Étant donné que l'ObjectId _id stocke par défaut l'horodatage sur 4 octets, dans la plupart des cas, vous n'avez pas besoin de stocker l'heure de création d'un document. Vous pouvez récupérer l'heure de création d'un document à l'aide de la méthode getTimestamp.

```
>ObjectId("5349b4ddd2781d08c09890f4").getTimestamp()
```

Ceci renverra l'heure de création de ce document au format de date ISO.

```
ISODate("2014-04-12T21:49:17Z")
```

## Conversion d'ObjectId en String

Dans certains cas, vous pouvez avoir besoin de la valeur d'ObjectId dans un format de chaîne. Pour convertir l'ObjectId en string, utilisez le code suivant -

```
>newObjectId.str
```

Le code ci-dessus renverra le format de chaîne de caractères du Guid -.

```
5349b4ddd2781d08c09890f3
```