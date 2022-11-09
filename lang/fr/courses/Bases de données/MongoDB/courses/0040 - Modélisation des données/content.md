Les données dans MongoDB ont un schéma flexible.documents dans la même collection. Il n'est pas nécessaire qu'ils aient le même ensemble de champs ou la même structure. Les champs communs des documents d'une collection peuvent contenir différents types de données.

## Data Model Design

MongoDB propose deux types de modèles de données : - le modèle de données intégré et le modèle de données normalisé. En fonction de vos besoins, vous pouvez utiliser l'un ou l'autre de ces modèles pour préparer votre document.

### Modèle de données embarqué

Dans ce modèle, vous pouvez avoir (intégrer) toutes les données liées dans un seul document, il est également connu sous le nom de modèle de données dé-normalisées.

Par exemple, supposons que nous obtenions les détails des employés dans trois documents différents, à savoir Personal_details, Contact et Address, vous pouvez intégrer ces trois documents dans un seul, comme indiqué ci-dessous.

```
{
	_id: ,
	Emp_ID: "10025AE336"
	Personal_details:{
		First_Name: "Radhika",
		Last_Name: "Sharma",
		Date_Of_Birth: "1995-09-26"
	},
	Contact: {
		e-mail: "radhika_sharma.123@gmail.com",
		phone: "9848022338"
	},
	Address: {
		city: "Hyderabad",
		Area: "Madapur",
		State: "Telangana"
	}
}
```

### Modèle de données normalisé

Dans ce modèle, vous pouvez faire référence aux sous-documents dans le document original, en utilisant des références. Par exemple, vous pouvez réécrire le document ci-dessus dans le modèle normalisé comme suit :

**Employé :**

```
{
	_id: <ObjectId101>,
	Emp_ID: "10025AE336"
}
```

**Détails personnels :**

```
{
	_id: <ObjectId102>,
	empDocID: " ObjectId101",
	First_Name: "Radhika",
	Last_Name: "Sharma",
	Date_Of_Birth: "1995-09-26"
}
```

**Contact :**

```
{
	_id: <ObjectId103>,
	empDocID: " ObjectId101",
	e-mail: "radhika_sharma.123@gmail.com",
	phone: "9848022338"
}
```

**Adresse :**

```
{
	_id: <ObjectId104>,
	empDocID: " ObjectId101",
	city: "Hyderabad",
	Area: "Madapur",
	State: "Telangana"
}
```

## Considérations lors de la conception de schémas dans MongoDB

- Concevez votre schéma en fonction des besoins des utilisateurs.
- Combinez les objets dans un seul document si vous comptez les utiliser ensemble. Sinon, séparez-les (mais assurez-vous qu'il n'est pas nécessaire de les joindre).
- Dupliquer les données (mais de façon limitée) car l'espace disque est bon marché par rapport au temps de calcul.
- Faites des jointures en écriture, pas en lecture.
- Optimisez votre schéma pour les cas d'utilisation les plus fréquents.
- Faire une agrégation complexe dans le schéma.

## Exemple

Supposons qu'un client ait besoin d'une conception de base de données pour son blog/site web et voyons les différences entre la conception de schémas RDBMS et MongoDB. Le site Web a les exigences suivantes.

- Chaque article a un titre, une description et une URL uniques.
- Chaque article peut avoir une ou plusieurs étiquettes.
- Chaque message comporte le nom de son éditeur et le nombre total de likes.
- Chaque message comporte des commentaires donnés par les utilisateurs, ainsi que leur nom, leur message, leurs données et leurs préférences.
- Sur chaque article, il peut y avoir zéro ou plusieurs commentaires.

Dans le schéma d'un RDBMS , la conception pour les exigences ci-dessus aura au minimum trois tables. Alors que dans le schéma de MongoDB, la conception aura un poste de collection et la structure suivante -

```
{
    _id: POST_ID
    title: TITLE_OF_POST, 
    description: POST_DESCRIPTION,
    by: POST_BY,
    url: URL_OF_POST,
    tags: [TAG1, TAG2, TAG3],
    likes: TOTAL_LIKES, 
    comments: [	
        {
            user:'COMMENT_BY',
            message: TEXT,
            dateCreated: DATE_TIME,
            like: LIKES 
        },
        {
            user:'COMMENT_BY',
            message: TEXT,
            dateCreated: DATE_TIME,
            like: LIKES
        }
    ]
}
```

Ainsi, lors de l'affichage des données, dans le SGBDR, vous devez joindre trois tables et dans MongoDB, les données seront affichées à partir d'une seule collection.