MongoDB est une base de données orientée documents, multiplateforme, qui offre de hautes performances, une grande disponibilité et une évolutivité facile. MongoDB fonctionne sur le concept de collection et de document.

## Base de données

La base de données est un conteneur physique pour les collections. Chaque base de données reçoit son propre ensemble de fichiers sur le système de fichiers. Un seul serveur MongoDB possède généralement plusieurs bases de données.

## Collection

Une collection est un groupe de documents MongoDB. C'est l'équivalent d'une table de SGBDR. Une collection existe au sein d'une seule base de données. Les collections n'imposent pas de schéma. Les documents d'une collection peuvent avoir des champs différents. En général, tous les documents d'une collection ont un objectif similaire ou connexe.

## Document

Un document est un ensemble de paires clé-valeur. Les documents ont un schéma dynamique. Le schéma dynamique signifie que les documents d'une même collection ne doivent pas nécessairement avoir le même ensemble de champs ou la même structure, et que les champs communs des documents d'une collection peuvent contenir différents types de données.

Le tableau suivant montre la relation entre la terminologie des RDBMS et MongoDB.

| **RDBMS** | **MongoDB** |
| --- | --- |
| Base de données | Base de données |
| Tableau | Collection |
| Tuple/Row | Document |
| colonne | Champ |
| Table Join | Documents intégrés |
| Clé primaire | Clé primaire (clé par défaut _id fournie par MongoDB lui-même) |
| **Serveur de BDD & client** | **Serveur de BDD & client** |
| mysqld/Oracle | mongod |
| mysql/sqlplus | mongo |

## Sample Document

L'exemple suivant montre la structure du document d'un site de blog, qui est simplement une paire clé-valeur séparée par des virgules.

```
{
    _id: ObjectId(7df78ad8902c)
    title: 'MongoDB Overview', 
    description: 'MongoDB is no sql database',
    by: 'tutorials point',
    url: 'http://www.tutorialspoint.com',
    tags: ['mongodb', 'database', 'NoSQL'],
    likes: 100, 
    comments: [	
        {
            user:'user1',
            message: 'My first comment',
            dateCreated: new Date(2011,1,20,2,15),
            like: 0 
        },
        {
            user:'user2',
            message: 'My second comments',
            dateCreated: new Date(2011,1,25,7,45),
            like: 5
        }
    ]
}
```

_id est un numéro hexadécimal de 12 octets qui garantit l'unicité de chaque document. Vous pouvez fournir _id lors de l'insertion du document. Si vous ne le fournissez pas, MongoDB fournit un identifiant unique pour chaque document. Ces 12 octets sont les 4 premiers octets pour l'horodatage actuel, les 3 octets suivants pour l'identification de la machine, les 2 octets suivants pour l'identification du processus du serveur MongoDB et les 3 octets restants sont de simples VALEURS incrémentales.