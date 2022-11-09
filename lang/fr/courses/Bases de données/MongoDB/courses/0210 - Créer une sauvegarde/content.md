Dans ce chapitre, nous allons voir comment créer une sauvegarde dans MongoDB.

## Dump MongoDB Data

Pour créer une sauvegarde de la base de données dans MongoDB, vous devez utiliser la commande mongodump. Cette commande déchargera l'ensemble des données de votre serveur dans le répertoire dump. Il existe de nombreuses options permettant de limiter la quantité de données ou de créer une sauvegarde de votre serveur distant.

### Syntaxe

La syntaxe de base de la commande mongodump est la suivante : -.

```
>mongodump
```

### Exemple

Démarrez votre serveur mongod. En supposant que votre serveur mongod fonctionne sur le localhost et le port 27017, ouvrez une invite de commande et allez dans le répertoire bin de votre instance mongodb et tapez la commande mongodump

Considérons que la collection mycol a les données suivantes.

```
>mongodump
```

La commande se connectera au serveur fonctionnant sur **127.0.0.1** et le port **27017** et sauvegardera toutes les données du serveur dans le répertoire ```/bin/dump/```. Le résultat de la commande est le suivant.

Voici une liste des options disponibles qui peuvent être utilisées avec la commande **mongodump**.

| **Syntaxe** | **Description** | **Exemple** |
| --- | --- | --- |
| ```mongodump --host HOST_NAME --port PORT_NUMBER``` | Cette commande va sauvegarder toutes les bases de données de l'instance mongod spécifiée. | ```mongodump --host tutorialspoint.com --port 27017``` |
| ```mongodump --dbpath DB_PATH --out BACKUP_DIRECTORY``` | Cette commande sauvegardera seulement la base de données spécifiée au chemin spécifié. | ```mongodump --dbpath /data/db/ --out /data/backup/``` |
| ```mongodump --collection COLLECTION --db DB_NAME``` | Cette commande sauvegardera seulement la collection spécifiée de la base de données spécifiée. | ```mongodump --collection mycol --db test``` |

## Restore data

Pour restaurer les données sauvegardées, on utilise la commande mongorestore de MongoDB. Cette commande restaure toutes les données du répertoire de sauvegarde.

### Syntaxe

La syntaxe de base de la commande ```mongorestore``` est -

```
>mongorestore
```