Dans ce chapitre, nous allons voir comment supprimer une base de données dans PostgreSQL. Il existe deux options pour supprimer une base de données :

- Utilisation de **DROP DATABASE**, une commande SQL.
- Utilisation de dropdb, un exécutable en ligne de commande.

Soyez prudent avant d'utiliser cette opération car la suppression d'une base de données existante entraînerait la perte de toutes les informations stockées dans la base de données.

## En utilisant DROP DATABASE

Cette commande supprime une base de données. Elle supprime les entrées du catalogue pour la base de données et supprime le répertoire contenant les données. Elle ne peut être exécutée que par le propriétaire de la base de données. Cette commande ne peut pas être exécutée lorsque vous ou quelqu'un d'autre est connecté à la base de données cible (connectez-vous à postgres ou à toute autre base de données pour lancer cette commande).

### Syntaxe

La syntaxe de DROP DATABASE est donnée ci-dessous :

```sql
DROP DATABASE [ IF EXISTS ] name
```

### Paramètres

La liste suivante énumère les paramètres avec leur description.

**Paramètre et description**

- **IF EXISTS** - Ne pas lancer une erreur si la base de données n'existe pas. Un avis est émis dans ce cas.
- **name** - Le nom de la base de données à supprimer.

__Remarque__ : Nous ne pouvons pas supprimer une base de données qui a des connexions ouvertes, y compris notre propre connexion depuis ```psql``` ou ```pgAdmin III```. Nous devons passer à une autre base de données ou à un autre modèle1 si nous voulons supprimer la base de données à laquelle nous sommes actuellement connectés. Ainsi, il peut être plus pratique d'utiliser le programme ```dropdb``` à la place, qui est une enveloppe autour de cette commande.

### Exemple

L'exemple suivant est un exemple simple qui supprimera ```testdb``` de votre schéma PostgreSQL.

```sql
postgres=# DROP DATABASE testdb;
postgres-#
```

## En utilisant dropdb Command

L'exécutable de ligne de commande PostgresSQL ```dropdb``` est une enveloppe de ligne de commande autour de la commande SQL **DROP DATABASE**. Il n'y a aucune différence effective entre l'abandon de bases de données via cet utilitaire et via d'autres méthodes d'accès au serveur. ```dropdb``` détruit une base de données PostgreSQL existante. L'utilisateur qui exécute cette commande doit être un super utilisateur de la base de données ou le propriétaire de la base de données.

### Syntaxe

La syntaxe de ```dropdb``` est indiquée ci-dessous :

```sql
dropdb  [option...] dbname
```

### Paramètres

La liste suivante énumère les paramètres avec leur description :

**Paramètre et description**

- **dbname** - Le nom d'une base de données à supprimer.
- **option** - Arguments de ligne de commande, que ```dropdb``` accepte.

### Options

La liste suivante énumère les options de ligne de commande que ```dropdb``` accepte :

**Option et description**

- **-e** - Montre les commandes envoyées au serveur.
- **-i** - Émets une demande de vérification avant de faire quoi que ce soit de destructif.
- **-V** - Affiche la version de ```dropdb``` et quitte.
- **--if-exists** - Ne pas lancer une erreur si la base de données n'existe pas. Un avis est émis dans ce cas.
- **--help** - Afficher l'aide sur les arguments de la ligne de commande de ```dropdb```, et quitter.
- **-h host** - Spécifie le nom d'hôte de la machine sur laquelle le serveur est exécuté.
- **-p port** - Spécifie le port TCP ou l'extension de fichier socket du domaine UNIX local sur lequel le serveur écoute les connexions.
- **-U username** - Nom d'utilisateur pour la connexion.
- **-w** - Ne jamais demander un mot de passe.
- **-W** - Force dropdb à demander un mot de passe avant de se connecter à une base de données.
- **--maintenance-db=dbname** - Spécifie le nom de la base de données à laquelle se connecter afin de déposer la base de données cible.

### Exemple

L'exemple suivant montre la suppression d'une base de données à partir de l'invite de commande du système d'exploitation :

```sql
dropdb -h localhost -p 5432 -U postgress testdb
Password for user postgress: ****
```

La commande ci-dessus supprime la base de données ```testdb```. Ici, j'ai utilisé le nom d'utilisateur postgres (trouvé sous ```pg_roles``` de template1) pour supprimer la base de données.
