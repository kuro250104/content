La commande SQLite **PRAGMA** est une commande spéciale utilisée pour contrôler diverses variables environnementales et drapeaux d'état dans l'environnement SQLite. Une valeur **PRAGMA** peut être lue et elle peut également être définie en fonction des besoins.

## Syntaxe

Pour demander la valeur actuelle de **PRAGMA**, il suffit de fournir le nom du pragma.

```sql
PRAGMA pragma_name;
```

Pour définir une nouvelle valeur pour **PRAGMA**, utilisez la syntaxe suivante.

```sql
PRAGMA pragma_name = value;
```

Le mode défini peut être soit le nom, soit l'équivalent en nombre entier, mais la valeur retournée sera toujours un nombre entier.

## auto_vacuum Pragma

Le pragma **auto_vacuum** permet d'obtenir ou de définir le mode d'auto-vacuum. Voici la syntaxe simple.

```sql
PRAGMA [database.]auto_vacuum;
PRAGMA [database.]auto_vacuum = mode;
```

Où le mode peut être l'un des suivants -

**Valeur et description du pragma**

- **0 or NONE** - L'aspiration automatique est désactivée. Il s'agit du mode par défaut, ce qui signifie que la taille d'un fichier de base de données ne diminuera jamais, sauf s'il est aspiré manuellement à l'aide de la commande VACUUM.
- **1 or FULL** - La fonction Auto-vacuum est activée et entièrement automatique, ce qui permet de réduire le fichier de la base de données au fur et à mesure que les données sont supprimées de la base.
- **2 or INCREMENTAL** - L'aspiration automatique est activée mais doit être activée manuellement. Dans ce mode, les données de référence sont maintenues, mais les pages libres sont simplement placées sur la liste libre. Ces pages peuvent être récupérées en utilisant le pragma incremental_vacuum à tout moment.

## cache_size Pragma

Le pragma **cache_size** permet d'obtenir ou de définir temporairement la taille maximale du cache de page en mémoire. Voici la syntaxe simple.

```sql
PRAGMA [database.]cache_size;
PRAGMA [database.]cache_size = pages;
```

La valeur pages représente le nombre de pages dans le cache. Le cache de pages intégré à une taille par défaut de 2 000 pages et une taille minimale de 10 pages.

## case_sensitive_like Pragma

Le pragma **case_sensitive_like** contrôle la sensibilité à la casse de l'expression LIKE intégrée. Par défaut, ce pragma est faux, ce qui signifie que l'opérateur LIKE intégré ignore la casse des lettres. Voici la syntaxe simple.

```sql
PRAGMA case_sensitive_like = [true|false];
```

Il n'y a aucun moyen de demander l'état actuel de ce pragma.

## count_changes Pragma

Le pragma **count_changes** permet d'obtenir ou de définir la valeur de retour des instructions de manipulation des données telles que INSERT, UPDATE et DELETE. Voici la syntaxe simple.

```sql
PRAGMA count_changes;
PRAGMA count_changes = [true|false];
```

Par défaut, ce pragma est faux et ces instructions ne renvoient rien. Si elle est définie sur true, chacune des déclarations mentionnées renverra un tableau d'une colonne et d'une ligne composé d'une seule valeur entière indiquant les lignes impactées par l'opération.

## database_list Pragma

Le pragma **database_list** sera utilisé pour lister toutes les bases de données attachées. Voici la syntaxe simple.

```sql
PRAGMA database_list;
```

Ce pragma retournera un tableau à trois colonnes avec une ligne par base de données ouverte ou attachée donnant le numéro de séquence de la base de données, son nom et le fichier associé.

## encoding Pragma

Le pragma **encoding** contrôle la façon dont les chaînes de caractères sont encodées et stockées dans un fichier de base de données. Voici la syntaxe simple.

```sql
PRAGMA encoding;
PRAGMA encoding = format;
```

La valeur du format peut être l'une des valeurs suivantes : UTF-8, UTF-16le ou UTF-16be.

## freelist_count Pragma

Le pragma **freelist_count** renvoie un entier unique indiquant combien de pages de la base de données sont actuellement marquées comme libres et disponibles. Voici la syntaxe simple.

```sql
PRAGMA [database.]freelist_count;
```

La valeur du format peut être l'une des valeurs suivantes : UTF-8, UTF-16le ou UTF-16be.

## index_info Pragma

Le pragma **index_info** renvoie des informations sur un index de base de données. Voici la syntaxe simple.

```sql
PRAGMA [database.]index_info( index_name );
```

Le jeu de résultats contient une ligne pour chaque colonne contenue dans l'index, avec la séquence de la colonne, l'index de la colonne dans la table et le nom de la colonne.

## index_list Pragma

Le pragma **index_list** liste tous les index associés à une table. Voici la syntaxe simple.

```sql
PRAGMA [database.]index_list( table_name );
```

Le jeu de résultats contient une ligne pour chaque index, avec la séquence de l'index, le nom de l'index et un drapeau indiquant si l'index est unique ou non.

## journal_mode Pragma

Le pragma **journal_mode** permet d'obtenir ou de définir le mode du journal qui contrôle la façon dont le fichier journal est stocké et traité. Voici la syntaxe simple.

```sql
PRAGMA journal_mode;
PRAGMA journal_mode = mode;
PRAGMA database.journal_mode;
PRAGMA database.journal_mode = mode;
```

Il existe cinq modes de journal pris en charge, comme indiqué dans le tableau suivant.

**Pragma Value & Description**

- **DELETE** - Il s'agit du mode par défaut. Ici, à la fin d'une transaction, le fichier journal est supprimé.
- **TRUNCATE** - Le fichier journal est tronqué à une longueur de zéro octet.
- **PERSIST** - Le fichier journal est laissé en place, mais l'en-tête est écrasé pour indiquer que le journal n'est plus valide.
- **MEMORY** - L'enregistrement du journal est conservé en mémoire, plutôt que sur disque.
- **OFF** - Aucun registre n'est tenu.

## max_page_count Pragma

Le pragma **max_page_count** permet d'obtenir ou de définir le nombre maximal de pages autorisé pour une base de données. Voici la syntaxe simple.

```sql
PRAGMA [database.]max_page_count;
PRAGMA [database.]max_page_count = max_page;
```

La valeur par défaut est de 1 073 741 823, soit un giga-page, ce qui signifie que si la taille de page par défaut est de 1 Ko, cela permet aux bases de données de croître jusqu'à un téraoctet.

## page_count Pragma

Le pragma **page_count** renvoie le nombre actuel de pages dans la base de données. Voici la syntaxe simple -

```sql
PRAGMA [database.]page_count;
```

La taille du fichier de la base de données devrait être de page_count * page_size.

## page_size Pragma

Le pragma **page_size** permet d'obtenir ou de définir la taille des pages de la base de données. Voici la syntaxe simple.

```sql
PRAGMA [database.]page_size;
PRAGMA [database.]page_size = bytes;
```

Par défaut, les tailles autorisées sont 512, 1024, 2048, 4096, 8192, 16384 et 32768 octets. La seule façon de modifier la taille de page d'une base de données existante est de définir la taille de page, puis de vider immédiatement la base de données.

## parser_trace Pragma

Le pragma **parser_trace** contrôle l'impression de l'état de débogage lors de l'analyse des commandes SQL. Voici la syntaxe simple.

```sql
PRAGMA parser_trace = [true|false];
```

Par défaut, il est défini à false mais lorsqu'il est activé en le définissant à true, l'analyseur SQL imprimera son état lorsqu'il analyse les commandes SQL.

## recursive_triggers Pragma

Le pragma **recursive_triggers** permet d'obtenir ou de définir la fonctionnalité de déclenchement récursif. Si les déclencheurs récursifs ne sont pas activés, une action de déclenchement ne déclenchera pas un autre déclencheur. Voici la syntaxe simple.

```sql
PRAGMA recursive_triggers;
PRAGMA recursive_triggers = [true|false];
```

## schema_version Pragma

Le pragma **schema_version** permet d'obtenir ou de définir la valeur de la version du schéma qui est stockée dans l'en-tête de la base de données. Voici la syntaxe simple.

```sql
PRAGMA [database.]schema_version;
PRAGMA [database.]schema_version = number;
```

Il s'agit d'une valeur entière signée de 32 bits qui garde la trace des modifications du schéma. Chaque fois qu'une commande modifiant le schéma est exécutée (comme CREATE... ou DROP...), cette valeur est incrémentée.

## secure_delete Pragma

Le pragma **secure_delete** est utilisé pour contrôler la manière dont le contenu est supprimé de la base de données. Voici la syntaxe simple.

```sql
PRAGMA secure_delete;
PRAGMA secure_delete = [true|false];
PRAGMA database.secure_delete;
PRAGMA database.secure_delete = [true|false];
```

La valeur par défaut de l'indicateur de suppression sécurisée est normalement désactivée, mais elle peut être modifiée avec l'option de construction SQLITE_SECURE_DELETE.

## sql_trace Pragma

Le pragma **sql_trace** est utilisé pour afficher les résultats de la trace SQL à l'écran. Voici la syntaxe simple.

```sql
PRAGMA sql_trace;
PRAGMA sql_trace = [true|false];
```

SQLite doit être compilé avec la directive SQLITE_DEBUG pour que ce pragma soit inclus.

## synchrone Pragma

Le pragma **synchrone** obtient ou définit le mode de synchronisation actuel du disque, qui contrôle l'agressivité avec laquelle SQLite écrira les données jusqu'au stockage physique. Voici la syntaxe simple.

```sql
PRAGMA [database.]synchronous;
PRAGMA [database.]synchronous = mode;
```

SQLite supporte les modes de synchronisation suivants, comme indiqué dans le tableau.

**Valeur et description du pragma**

- **0 or OFF** - Pas de synchronisation du tout
- **1 or NORMAL** - Synchronisation après chaque séquence d'opérations critiques sur le disque
- **2 or FULL** - Synchronisation après chaque opération critique sur le disque

## temp_store Pragma

Le pragma **temp_store** permet d'obtenir ou de définir le mode de stockage utilisé par les fichiers temporaires de la base de données. Voici la syntaxe simple.

```sql
PRAGMA temp_store;
PRAGMA temp_store = mode;
```

SQLite supports the following storage modes.

**Valeur et description du pragma**

- **0 or DEFAULT** - Utiliser la valeur par défaut de la compilation. Normalement FILE.
- **1 or FILE** - Utilisez un stockage basé sur des fichiers.
- **2 or MEMORY** - Utilisez le stockage en mémoire.

## temp_store_directory Pragma

Le pragma **temp_store_directory** permet d'obtenir ou de définir l'emplacement utilisé pour les fichiers temporaires de la base de données. Voici la syntaxe simple.

```sql
PRAGMA temp_store_directory;
PRAGMA temp_store_directory = 'directory_path';
```

## user_version Pragma

Le pragma **user_version** permet d'obtenir ou de définir la valeur de la version définie par l'utilisateur qui est stockée dans l'en-tête de la base de données. Voici la syntaxe simple.

```sql
PRAGMA [database.]user_version;
PRAGMA [database.]user_version = number;
```

Il s'agit d'une valeur entière signée de 32 bits, qui peut être définie par le développeur à des fins de suivi de version.

## writable_schema Pragma

Le pragma **writable_schema** permet d'obtenir ou de définir la possibilité de modifier les tables du système. Voici la syntaxe simple.

```sql
PRAGMA writable_schema;
PRAGMA writable_schema = [true|false];
```

Si ce pragma est défini, les tables qui commencent par sqlite_ peuvent être créées et modifiées, y compris la table sqlite_master. Soyez prudent lorsque vous utilisez ce pragma, car il peut entraîner une corruption complète de la base de données.