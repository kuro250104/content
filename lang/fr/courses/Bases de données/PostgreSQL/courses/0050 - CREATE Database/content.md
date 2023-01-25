Ce chapitre traite de la manière de créer une nouvelle base de données dans votre PostgreSQL. PostgreSQL propose deux façons de créer une nouvelle base de données :

- En utilisant CREATE DATABASE, une commande SQL.
- Utilisation de createdb un exécutable en ligne de commande.

## En utilisant CREATE DATABASE

Cette commande va créer une base de données à partir de l'invite du shell PostgreSQL, mais vous devez avoir les privilèges appropriés pour créer une base de données. Par défaut, la nouvelle base de données sera créée en clonant le modèle de base de données standard du système1.

### Syntaxe

La syntaxe de base de l'instruction CREATE DATABASE est la suivante :

```sql
CREATE DATABASE dbname;
```

où **dbname** est le nom de la base de données à créer.

### Exemple

Voici un exemple simple, qui créera testdb dans votre schéma PostgreSQL :

```sql
postgres=# CREATE DATABASE testdb;
postgres-#
```

## En utilisant la commande createdb

L'exécutable de ligne de commande de PostgreSQL, createdb, est une enveloppe autour de la commande SQL CREATE DATABASE. La seule différence entre cette commande et la commande SQL CREATE DATABASE est que la première peut être exécutée directement depuis la ligne de commande et qu'elle permet d'ajouter un commentaire dans la base de données, le tout en une seule commande.

### Syntaxe

La syntaxe de createdb est indiquée ci-dessous :

```sql
createdb [option...] [dbname [description]]
```

### Paramètres

La liste ci-dessous répertorie les paramètres avec leur description.

**Paramètre et description**

- **dbname** - Le nom de la base de données à créer.
- **description** - Spécifie un commentaire à associer à la base de données nouvellement créée.
- **options** - Arguments de ligne de commande, que createdb accepte.

### Options

La liste suivante liste les arguments de ligne de commande que createdb accepte :

**Option et description**

- **-D tablespace** - Spécifie le tablespace par défaut pour la base de données.
- **-e** - Faites écho aux commandes que createdb génère et envoie au serveur.
- **-E encoding** - Spécifie le schéma de codage des caractères à utiliser dans cette base de données.
- **-l locale** - Spécifie la locale à utiliser dans cette base de données.
- **-T template** - Spécifie la base de données modèle à partir de laquelle construire cette base de données.
- **--help** - Afficher l'aide sur les arguments de la ligne de commande de createdb, et quitter.
- **-h host** - Spécifie le nom d'hôte de la machine sur laquelle le serveur est exécuté.
- **-p port** - Spécifie le port TCP ou l'extension de fichier socket du domaine Unix local sur lequel le serveur écoute les connexions.
- **-U username** - Nom d'utilisateur pour la connexion.
- **-w** - Ne jamais demander de mot de passe.
- **-W** - Force createdb à demander un mot de passe avant de se connecter à une base de données.

Ouvrez l'invite de commande et allez dans le répertoire où PostgreSQL est installé. Allez dans le répertoire bin et exécutez la commande suivante pour créer une base de données.

```bash
createdb -h localhost -p 5432 -U postgres testdb
password ******
```

La commande ci-dessus vous demandera le mot de passe de l'utilisateur admin de PostgreSQL, qui est postgres, par défaut. Par conséquent, fournissez un mot de passe et procédez à la création de votre nouvelle base de données.

Une fois qu'une base de données est créée à l'aide de l'une ou l'autre des méthodes mentionnées ci-dessus, vous pouvez la vérifier dans la liste des bases de données en utilisant la commande \l, c'est-à-dire, backslash el comme suit :

```bash
postgres-# \l
                             List of databases
   Name    |  Owner   | Encoding | Collate | Ctype |   Access privileges   
-----------+----------+----------+---------+-------+-----------------------
 postgres  | postgres | UTF8     | C       | C     | 
 template0 | postgres | UTF8     | C       | C     | =c/postgres          +
           |          |          |         |       | postgres=CTc/postgres
 template1 | postgres | UTF8     | C       | C     | =c/postgres          +
           |          |          |         |       | postgres=CTc/postgres
 testdb    | postgres | UTF8     | C       | C     | 
(4 rows)

postgres-#
```
