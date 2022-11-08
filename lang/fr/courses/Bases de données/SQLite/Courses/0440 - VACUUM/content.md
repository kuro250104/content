La commande VACUUM nettoie la base de données principale en copiant son contenu dans un fichier de base de données temporaire et en rechargeant le fichier de base de données original à partir de la copie. Cela élimine les pages libres, aligne les données des tables pour qu'elles soient contiguës et nettoie la structure du fichier de la base de données.

La commande VACUUM peut modifier le ROWID des entrées des tables qui n'ont pas de CLÉ PRIMAIRE INTEGRALE explicite. La commande VACUUM ne fonctionne que sur la base de données principale. Il n'est pas possible d'effectuer un VACUUM sur un fichier de base de données joint.

La commande VACUUM échouera si une transaction est en cours. La commande VACUUM ne fonctionne pas pour les bases de données en mémoire. Comme la commande VACUUM reconstruit le fichier de la base de données à partir de zéro, VACUUM peut également être utilisé pour modifier de nombreux paramètres de configuration spécifiques à la base de données.

## Manual VACUUM

Voici une syntaxe simple pour lancer une commande VACUUM pour l'ensemble de la base de données à partir de l'invite de commande.

```sql
$sqlite3 database_name "VACUUM;"
```

Vous pouvez également exécuter VACUUM à partir de l'invite SQLite comme suit -.

```sql
sqlite> VACUUM;
```

Vous pouvez également exécuter VACUUM sur une table particulière comme suit -

```sql
sqlite> VACUUM table_name;
```

## Auto-VACCUM

SQLite Auto-VACUUM ne fait pas la même chose que VACUUM, il déplace seulement les pages libres à la fin de la base de données, réduisant ainsi la taille de la base de données. Ce faisant, il peut fragmenter significativement la base de données alors que VACUUM assure la défragmentation. Par conséquent, Auto-VACUUM ne fait que garder la base de données petite.

Vous pouvez activer/désactiver l'aspiration automatique de SQLite par les pragmes suivants exécutés à l'invite de SQLite -

```sql
sqlite> PRAGMA auto_vacuum = NONE; -- 0 means disable auto vacuum
sqlite> PRAGMA auto_vacuum = FULL; -- 1 means enable full auto vacuum
sqlite> PRAGMA auto_vacuum = INCREMENTAL; -- 2 means enable incremental vacuum
```

Vous pouvez exécuter la commande suivante à partir de l'invite de commande pour vérifier le réglage de l'aspiration automatique.

```sql
$sqlite3 database_name "PRAGMA auto_vacuum;"
```