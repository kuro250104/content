La réplication est le processus de synchronisation des données sur plusieurs serveurs. La réplication fournit une redondance et augmente la disponibilité des données grâce à des copies multiples des données sur différents serveurs de base de données. La réplication protège une base de données contre la perte d'un seul serveur. La réplication vous permet également de récupérer après une panne matérielle et des interruptions de service. Avec des copies supplémentaires des données, vous pouvez en dédier une à la reprise après sinistre, au reporting ou à la sauvegarde.

## Pourquoi la réplication ?

- Pour assurer la sécurité de vos données
- Haute disponibilité (24*7) des données
- Reprise après sinistre
- Pas de temps d'arrêt pour la maintenance (comme les sauvegardes, les reconstructions d'index, la compaction).
- Mise à l'échelle de la lecture (copies supplémentaires à lire)
- Le jeu de répliques est transparent pour l'application

## Comment fonctionne la réplication dans MongoDB

MongoDB réalise la réplication par l'utilisation de replica set. Un ensemble de répliques est un groupe d'instances MongoDB qui hébergent le même ensemble de données. Dans une réplique, un nœud est le nœud primaire qui reçoit toutes les opérations d'écriture. Toutes les autres instances, telles que les secondaires, appliquent les opérations du primaire afin de disposer du même ensemble de données. Un ensemble de répliques ne peut avoir qu'un seul nœud primaire.

- Un ensemble de répliques est un groupe de deux nœuds ou plus (généralement, un minimum de trois nœuds est requis).
- Dans un ensemble de répliques, un nœud est le nœud principal et les autres nœuds sont secondaires.
- Toutes les données sont répliquées du nœud primaire au nœud secondaire.
- Au moment du basculement automatique ou de la maintenance, l'élection s'établit pour le primaire et un nouveau nœud primaire est élu.
- Après la récupération du nœud défaillant, il rejoint à nouveau l'ensemble de répliques et fonctionne comme un nœud secondaire.

## Caractéristiques du jeu de répliques

- Un cluster de N nœuds
- Un seul nœud peut être primaire
- Toutes les opérations d'écriture vont au primaire
- Basculement automatique
- Récupération automatique
- Élection consensuelle des primaires

## Configurer un ensemble de répliques

Dans ce tutoriel, nous allons convertir une instance autonome de MongoDB en un ensemble de répliques. Pour convertir une instance en un ensemble de répliques, voici les étapes à suivre.

- Arrêtez le serveur MongoDB en cours d'exécution.
- Démarrez le serveur MongoDB en spécifiant l'option -- replSet. La syntaxe de base de l'option --replSet - est la suivante

```
mongod --port "PORT" --dbpath "YOUR_DB_DATA_PATH" --replSet "REPLICA_SET_INSTANCE_NAME"
```

### Exemple

```
mongod --port 27017 --dbpath "D:\set up\mongodb\data" --replSet rs0
```

- Il va démarrer une instance mongod avec le nom rs0, sur le port 27017.
- Maintenant, lancez l'invite de commande et connectez-vous à cette instance mongod.
- Dans le client Mongo, lancez la commande ```rs.initiate()``` pour initier un nouveau jeu de répliques.
- Pour vérifier la configuration de l'ensemble de répliques, lancez la commande ```rs.conf()```. Pour vérifier l'état du jeu de répliques, lancez la commande ```rs.status()```.

## Ajouter des membres au jeu de répliques

Pour ajouter des membres à l'ensemble de répliques, démarrez des instances mongod sur plusieurs machines. Démarrez maintenant un client mongo et lancez la commande ```rs.add()```.

### Syntaxe

La syntaxe de base de la commande ```rs.add()``` est la suivante -

```
>rs.add(HOST_NAME:PORT)
```

### Exemple

Supposons que le nom de votre instance mongod soit mongod1.net et qu'elle fonctionne sur le port 27017. Pour ajouter cette instance au jeu de répliques, lancez la commande ```rs.add()``` dans le client Mongo.

```
>rs.add("mongod1.net:27017")
>
```

Vous ne pouvez ajouter l'instance mongod à l'ensemble de répliques que si vous êtes connecté au nœud primaire. Pour vérifier si vous êtes connecté au nœud primaire ou non, lancez la commande ```db.isMaster()``` dans le client mongo.