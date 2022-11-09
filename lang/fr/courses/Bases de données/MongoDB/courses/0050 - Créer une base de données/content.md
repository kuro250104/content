Dans ce chapitre, nous allons voir comment créer une base de données dans MongoDB.

## La commande USE

MongoDB **USE DATABASE_NAME** est utilisé pour créer une base de données. La commande créera une nouvelle base de données si elle n'existe pas, sinon elle retournera la base de données existante.

### Syntaxe

La syntaxe de base de l'instruction **USE DATABASE** est la suivante : -.

```sql
USE DATABASE_NAME
```

### Exemple

Si vous voulez utiliser une base de données avec le nom ```<mydb>```, alors l'instruction use DATABASE serait la suivante : -.

```bash
>use mydb
switched to db mydb
```

Pour vérifier la base de données actuellement sélectionnée, utilisez la commande db

```bash
>db
mydb
```

Si vous voulez vérifier la liste de vos bases de données, utilisez la commande show dbs.

```bash
>show dbs
local     0.78125GB
test      0.23012GB
```

La base de données que vous avez créée (mydb) n'est pas présente dans la liste. Pour afficher la base de données, vous devez y insérer au moins un document.

```bash
>db.movie.insert({"name":"Microlead"})
>show dbs
local      0.78125GB
mydb       0.23012GB
test       0.23012GB
```

Dans MongoDB, la base de données par défaut est test. Si vous n'avez pas créé de base de données, les collections seront stockées dans la base de données test.