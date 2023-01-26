Ce chapitre fournit une liste des commandes SQL de PostgreSQL, suivie des règles syntaxiques précises pour chacune de ces commandes. Cet ensemble de commandes est tiré de l'outil de ligne de commande psql. Maintenant que vous avez installé Postgres, ouvrez l'outil psql sous la forme :

```sql
Program Files → PostgreSQL 9.2 → SQL Shell(psql).
```

Avec psql, vous pouvez générer une liste complète des commandes en utilisant la commande ```\help```. Pour connaître la syntaxe d'une commande spécifique, utilisez la commande suivante :

```sql
postgres-# \help <command_name>
```

## The SQL Statement

Une instruction SQL est composée de jetons, chaque jeton pouvant représenter un mot-clé, un identifiant, un identifiant cité, une constante ou un symbole de caractère spécial. Le tableau ci-dessous utilise une simple instruction **SELECT** pour illustrer une instruction SQL de base, mais complète, et ses composants.

|  | **SELECT** | **id, name** | **FROM** | **states** |
| --- | --- | --- | --- | --- |
| Type de jeton | Mot clé | Identifiers | Mot clé | Identifier |
| Description | Commande | Colonnes Id et Nom | Clause | Nom de la table |

## PostgreSQL SQL commands

### ABORT

Abandonner la transaction en cours.

```sql
ABORT [ WORK | TRANSACTION ]
```

### ALTER AGGREGATE

Modifiez la définition d'une fonction agrégée.

```sql
ALTER AGGREGATE name ( type ) RENAME TO new_name
ALTER AGGREGATE name ( type ) OWNER TO new_owner
```

### ALTER DATABASE

Modifier un paramètre spécifique à une base de données.

```sql
ALTER DATABASE name SET parameter { TO | = } { value | DEFAULT }
ALTER DATABASE name RESET parameter
ALTER DATABASE name RENAME TO new_name
ALTER DATABASE name OWNER TO new_owner
```

### ALTER DOMAIN

Modifier la définition d'un paramètre spécifique au domaine.

```sql
ALTER DOMAIN name { SET DEFAULT expression | DROP DEFAULT }
ALTER DOMAIN name { SET | DROP } NOT NULL
ALTER DOMAIN name ADD domain_constraint
ALTER DOMAIN name DROP CONSTRAINT constraint_name [ RESTRICT | CASCADE ]
ALTER DOMAIN name OWNER TO new_owner
```

### ALTER FUNCTION

Modifier la définition d'une fonction.

```sql
ALTER FUNCTION name ( [ type [, ...] ] ) RENAME TO new_name
ALTER FUNCTION name ( [ type [, ...] ] ) OWNER TO new_owner
```

### ALTER GROUP

Modifier un groupe d'utilisateurs.

```sql
ALTER GROUP groupname ADD USER username [, ... ]
ALTER GROUP groupname DROP USER username [, ... ]
ALTER GROUP groupname RENAME TO new_name
```

### ALTER INDEX

Modifier la définition d'un indice.

```sql
ALTER INDEX name OWNER TO new_owner
ALTER INDEX name SET TABLESPACE indexspace_name
ALTER INDEX name RENAME TO new_name
```

### ALTER LANGUAGE

Modifier la définition d'un langage procédural.

```sql
ALTER LANGUAGE name RENAME TO new_name
```

### ALTER OPERATOR

Modifier la définition d'un opérateur.

```sql
ALTER OPERATOR name ( { lefttype | NONE }, { righttype | NONE } )
OWNER TO new_owner
```

### ALTER OPERATOR CLASS

Modifier la définition d'une classe d'opérateurs.

```sql
ALTER OPERATOR CLASS name USING index_method RENAME TO new_name
ALTER OPERATOR CLASS name USING index_method OWNER TO new_owner
```

### ALTER SCHEMA

Modifier la définition d'un schéma.

```sql
ALTER SCHEMA name RENAME TO new_name
ALTER SCHEMA name OWNER TO new_owner
```

### ALTER SEQUENCE

Modifier la définition d'un générateur de séquence.

```sql
ALTER SEQUENCE name [ INCREMENT [ BY ] increment ]
[ MINVALUE minvalue | NO MINVALUE ]
[ MAXVALUE maxvalue | NO MAXVALUE ]
[ RESTART [ WITH ] start ] [ CACHE cache ] [ [ NO ] CYCLE ]
```

### ALTER TABLE

Modifier la définition d'un tableau.

```sql
ALTER TABLE [ ONLY ] name [ * ]
action [, ... ]
ALTER TABLE [ ONLY ] name [ * ]
RENAME [ COLUMN ] column TO new_column
ALTER TABLE name
RENAME TO new_name
```

Où l'action est l'une des lignes suivantes :

```sql
ADD [ COLUMN ] column_type [ column_constraint [ ... ] ]
DROP [ COLUMN ] column [ RESTRICT | CASCADE ]
ALTER [ COLUMN ] column TYPE type [ USING expression ]
ALTER [ COLUMN ] column SET DEFAULT expression
ALTER [ COLUMN ] column DROP DEFAULT
ALTER [ COLUMN ] column { SET | DROP } NOT NULL
ALTER [ COLUMN ] column SET STATISTICS integer
ALTER [ COLUMN ] column SET STORAGE { PLAIN | EXTERNAL | EXTENDED | MAIN }
ADD table_constraint
DROP CONSTRAINT constraint_name [ RESTRICT | CASCADE ]
CLUSTER ON index_name
SET WITHOUT CLUSTER
SET WITHOUT OIDS
OWNER TO new_owner
SET TABLESPACE tablespace_name
```

### ALTER TABLESPACE

Modifier la définition d'un tablespace.

```sql
ALTER TABLESPACE name RENAME TO new_name
ALTER TABLESPACE name OWNER TO new_owner
```

### ALTER TRIGGER

Modifier la définition d'un déclencheur.

```sql
ALTER TRIGGER name ON table RENAME TO new_name
```

### ALTER TYPE

Modifier la définition d'un type.

```sql
ALTER TYPE name OWNER TO new_owner
```

### ALTER USER

Modifier un compte utilisateur de la base de données.

```sql
ALTER USER name [ [ WITH ] option [ ... ] ]
ALTER USER name RENAME TO new_name
ALTER USER name SET parameter { TO | = } { value | DEFAULT }
ALTER USER name RESET parameter
```

Où l'option peut être :

```sql
[ ENCRYPTED | UNENCRYPTED ] PASSWORD 'password'
| CREATEDB | NOCREATEDB
| CREATEUSER | NOCREATEUSER
| VALID UNTIL 'abstime'
```

### ANALYZE

Collecter des statistiques sur une base de données.

```sql
ANALYZE [ VERBOSE ] [ table [ (column [, ...] ) ] ]
```

### BEGIN

Démarrer un bloc de transaction.

```sql
BEGIN [ WORK | TRANSACTION ] [ transaction_mode [, ...] ]
```

Où transaction_mode est l'un de :

```sql
ISOLATION LEVEL { 
    SERIALIZABLE | REPEATABLE READ | READ COMMITTED
    | READ UNCOMMITTED
}
READ WRITE | READ ONLY
```

### CHECKPOINT

Force un point de contrôle du journal des transactions.

```sql
CHECKPOINT
```

### CLOSE

Fermer un curseur.

```sql
CLOSE name
```

### CLUSTER

Regrouper une table en fonction d'un index.

```sql
CLUSTER index_name ON table_name
CLUSTER table_name
CLUSTER
```

### COMMENT

Définir ou modifier le commentaire d'un objet.

```sql
COMMENT ON {
    TABLE object_name |
    COLUMN table_name.column_name |
    AGGREGATE agg_name (agg_type) |
    CAST (source_type AS target_type) |
    CONSTRAINT constraint_name ON table_name |
    CONVERSION object_name |
    DATABASE object_name |
    DOMAIN object_name |
    FUNCTION func_name (arg1_type, arg2_type, ...) |
    INDEX object_name |
    LARGE OBJECT large_object_oid |
    OPERATOR op (left_operand_type, right_operand_type) |
    OPERATOR CLASS object_name USING index_method |
    [ PROCEDURAL ] LANGUAGE object_name |
    RULE rule_name ON table_name |
    SCHEMA object_name |
    SEQUENCE object_name |
    TRIGGER trigger_name ON table_name |
    TYPE object_name |
    VIEW object_name
} 
IS 'text'
```

### COMMIT

Valider la transaction en cours.

```sql
COMMIT [ WORK | TRANSACTION ]
```

### COPY

Copier des données entre un fichier et une table.

```sql
COPY table_name [ ( column [, ...] ) ]
FROM { 'filename' | STDIN }
[ WITH ]
[ BINARY ]
[ OIDS ]
[ DELIMITER [ AS ] 'delimiter' ]
[ NULL [ AS ] 'null string' ]
[ CSV [ QUOTE [ AS ] 'quote' ]
[ ESCAPE [ AS ] 'escape' ]
[ FORCE NOT NULL column [, ...] ]
COPY table_name [ ( column [, ...] ) ]
TO { 'filename' | STDOUT }
[ [ WITH ]
[ BINARY ]
[ OIDS ]
[ DELIMITER [ AS ] 'delimiter' ]
[ NULL [ AS ] 'null string' ]
[ CSV [ QUOTE [ AS ] 'quote' ]
[ ESCAPE [ AS ] 'escape' ]
[ FORCE QUOTE column [, ...] ]
```

### CREATE AGGREGATE

Définir une nouvelle fonction d'agrégation.

```sql
CREATE AGGREGATE name (
    BASETYPE = input_data_type,
    SFUNC = sfunc,
    STYPE = state_data_type
    [, FINALFUNC = ffunc ]
    [, INITCOND = initial_condition ]
)
```

### CREATE CAST

Définir une nouvelle distribution.

```sql
CREATE CAST (source_type AS target_type)
WITH FUNCTION func_name (arg_types)
[ AS ASSIGNMENT | AS IMPLICIT ]
CREATE CAST (source_type AS target_type)
WITHOUT FUNCTION
[ AS ASSIGNMENT | AS IMPLICIT ]
```

### CREATE CONSTRAINT TRIGGER

Définir un nouveau déclencheur de contrainte.

```sql
CREATE CONSTRAINT TRIGGER name
AFTER events ON
table_name constraint attributes
FOR EACH ROW EXECUTE PROCEDURE func_name ( args )
```

### CREATE CONVERSION

Définir une nouvelle conversion.

```sql
CREATE [DEFAULT] CONVERSION name
FOR source_encoding TO dest_encoding FROM func_name
```

### CREATE DATABASE

Créez une nouvelle base de données.

```sql
CREATE DATABASE name
[ [ WITH ] [ OWNER [=] db_owner ]
    [ TEMPLATE [=] template ]
    [ ENCODING [=] encoding ]
    [ TABLESPACE [=] tablespace ] 
]
```

### CREATE DOMAIN

Définir un nouveau domaine.

```sql
CREATE DOMAIN name [AS] data_type
[ DEFAULT expression ]
[ constraint [ ... ] ]
```

Où la contrainte est :

```sql
[ CONSTRAINT constraint_name ]
{ NOT NULL | NULL | CHECK (expression) }
```

### CREATE FUNCTION

Définir une nouvelle fonction.

```sql
CREATE [ OR REPLACE ] FUNCTION name ( [ [ arg_name ] arg_type [, ...] ] )
RETURNS ret_type
{ LANGUAGE lang_name
    | IMMUTABLE | STABLE | VOLATILE
    | CALLED ON NULL INPUT | RETURNS NULL ON NULL INPUT | STRICT
    | [ EXTERNAL ] SECURITY INVOKER | [ EXTERNAL ] SECURITY DEFINER
    | AS 'definition'
    | AS 'obj_file', 'link_symbol'
} ...
[ WITH ( attribute [, ...] ) ]
```

### CREATE GROUP

Définir un nouveau groupe d'utilisateurs.

```sql
CREATE GROUP name [ [ WITH ] option [ ... ] ]
Where option can be:
SYSID gid
| USER username [, ...]
```

### CREATE INDEX

Définir un nouvel index.

```sql
CREATE [ UNIQUE ] INDEX name ON table [ USING method ]
( { column | ( expression ) } [ opclass ] [, ...] )
[ TABLESPACE tablespace ]
[ WHERE predicate ]
```

### CREATE LANGUAGE

Définir un nouveau langage procédural.

```sql
CREATE [ TRUSTED ] [ PROCEDURAL ] LANGUAGE name
HANDLER call_handler [ VALIDATOR val_function ]
```

### CREATE OPERATOR

Définir un nouvel opérateur.

```sql
CREATE OPERATOR name (
    PROCEDURE = func_name
    [, LEFTARG = left_type ] [, RIGHTARG = right_type ]
    [, COMMUTATOR = com_op ] [, NEGATOR = neg_op ]
    [, RESTRICT = res_proc ] [, JOIN = join_proc ]
    [, HASHES ] [, MERGES ]
    [, SORT1 = left_sort_op ] [, SORT2 = right_sort_op ]
    [, LTCMP = less_than_op ] [, GTCMP = greater_than_op ]
)
```

### CREATE OPERATOR CLASS

Définir une nouvelle classe d'opérateurs.

```sql
CREATE OPERATOR CLASS name [ DEFAULT ] FOR TYPE data_type
USING index_method AS
{ OPERATOR strategy_number operator_name [ ( op_type, op_type ) ] [ RECHECK ]
    | FUNCTION support_number func_name ( argument_type [, ...] )
    | STORAGE storage_type
} [, ... ]
```

### CREATE RULE

Définir une nouvelle règle de réécriture.

```sql
CREATE [ OR REPLACE ] RULE name AS ON event
TO table [ WHERE condition ]
DO [ ALSO | INSTEAD ] { NOTHING | command | ( command ; command ... ) }
```

### CREATE SCHEMA

Définir un nouveau schéma.

```sql
CREATE SCHEMA schema_name
[ AUTHORIZATION username ] [ schema_element [ ... ] ]
CREATE SCHEMA AUTHORIZATION username
[ schema_element [ ... ] ]
```

### CREATE SEQUENCE

Définir un nouveau générateur de séquence.

```sql
CREATE [ TEMPORARY | TEMP ] SEQUENCE name
[ INCREMENT [ BY ] increment ]
[ MINVALUE minvalue | NO MINVALUE ]
[ MAXVALUE maxvalue | NO MAXVALUE ]
[ START [ WITH ] start ] [ CACHE cache ] [ [ NO ] CYCLE ]
```

### CREATE TABLE

Définir une nouvelle table.

```sql
CREATE [ [ GLOBAL | LOCAL ] { 
    TEMPORARY | TEMP } ] TABLE table_name ( { 
        column_name data_type [ DEFAULT default_expr ] [ column_constraint [ ... ] ]
        | table_constraint
        | LIKE parent_table [ { INCLUDING | EXCLUDING } DEFAULTS ] 
    } [, ... ]
)
[ INHERITS ( parent_table [, ... ] ) ]
[ WITH OIDS | WITHOUT OIDS ]
[ ON COMMIT { PRESERVE ROWS | DELETE ROWS | DROP } ]
[ TABLESPACE tablespace ]
```

Où column_constraint est :

```sql
[ CONSTRAINT constraint_name ] { 
    NOT NULL |
    NULL |
    UNIQUE [ USING INDEX TABLESPACE tablespace ] |
    PRIMARY KEY [ USING INDEX TABLESPACE tablespace ] |
    CHECK (expression) |
    REFERENCES ref_table [ ( ref_column ) ]
    [ MATCH FULL | MATCH PARTIAL | MATCH SIMPLE ]
    [ ON DELETE action ] [ ON UPDATE action ] 
}
[ DEFERRABLE | NOT DEFERRABLE ] [ INITIALLY DEFERRED | INITIALLY IMMEDIATE ]
```

Et table_constraint est :

```sql
[ CONSTRAINT constraint_name ]
{ UNIQUE ( column_name [, ... ] ) [ USING INDEX TABLESPACE tablespace ] |
PRIMARY KEY ( column_name [, ... ] ) [ USING INDEX TABLESPACE tablespace ] |
CHECK ( expression ) |
FOREIGN KEY ( column_name [, ... ] )
REFERENCES ref_table [ ( ref_column [, ... ] ) ]
[ MATCH FULL | MATCH PARTIAL | MATCH SIMPLE ]
[ ON DELETE action ] [ ON UPDATE action ] }
[ DEFERRABLE | NOT DEFERRABLE ] [ INITIALLY DEFERRED | INITIALLY IMMEDIATE ]
```

### CREATE TABLE AS

Définir une nouvelle table à partir des résultats d'une requête.

```sql
CREATE [ [ GLOBAL | LOCAL ] { TEMPORARY | TEMP } ] TABLE table_name
[ (column_name [, ...] ) ] [ [ WITH | WITHOUT ] OIDS ]
AS query
```

### CREATE TABLESPACE

Définir un nouveau tablespace.

```sql
CREATE TABLESPACE tablespace_name [ OWNER username ] LOCATION 'directory'
```

### CREATE TRIGGER

Définissez un nouveau déclencheur.

```sql
CREATE TRIGGER name { BEFORE | AFTER } { event [ OR ... ] }
ON table [ FOR [ EACH ] { ROW | STATEMENT } ]
EXECUTE PROCEDURE func_name ( arguments )
```

### CREATE TYPE

Définir un nouveau type de données.

```sql
CREATE TYPE name AS
( attribute_name data_type [, ... ] )
CREATE TYPE name (
INPUT = input_function,
OUTPUT = output_function
[, RECEIVE = receive_function ]
[, SEND = send_function ]
[, ANALYZE = analyze_function ]
[, INTERNALLENGTH = { internal_length | VARIABLE } ]
[, PASSEDBYVALUE ]
[, ALIGNMENT = alignment ]
[, STORAGE = storage ]
[, DEFAULT = default ]
[, ELEMENT = element ]
[, DELIMITER = delimiter ]
)
```

### CREATE USER

Définissez un nouveau compte d'utilisateur de la base de données.

```sql
CREATE USER name [ [ WITH ] option [ ... ] ]
```

Où l'option peut être :

```sql
SYSID uid
| [ ENCRYPTED | UNENCRYPTED ] PASSWORD 'password'
| CREATEDB | NOCREATEDB
| CREATEUSER | NOCREATEUSER
| IN GROUP group_name [, ...]
| VALID UNTIL 'abs_time'
```

### CREATE VIEW

Définir une nouvelle vue.

```sql
CREATE [ OR REPLACE ] VIEW name [ ( column_name [, ...] ) ] AS query
```

### DEALLOCATE

Désaffecter une déclaration préparée.

```sql
DEALLOCATE [ PREPARE ] plan_name
```

### DECLARE

Définir un curseur.

```sql
DECLARE name [ BINARY ] [ INSENSITIVE ] [ [ NO ] SCROLL ]
CURSOR [ { WITH | WITHOUT } HOLD ] FOR query
[ FOR { READ ONLY | UPDATE [ OF column [, ...] ] } ]
```

### DELETE

Supprimer les lignes d'un tableau.

```sql
DELETE FROM [ ONLY ] table [ WHERE condition ]
```

### DROP AGGREGATE

Supprimer une fonction d'agrégation.

```sql
DROP AGGREGATE name ( type ) [ CASCADE | RESTRICT ]
```

### DROP CAST

Enlever un plâtre.

```sql
DROP CAST (source_type AS target_type) [ CASCADE | RESTRICT ]
```

### DROP CONVERSION

Remove a conversion.

```sql
DROP CONVERSION name [ CASCADE | RESTRICT ]
```

### DROP DATABASE

Supprimer une base de données.

```sql
DROP DATABASE name
```

### DROP DOMAIN

Supprimer un domaine.

```sql
DROP DOMAIN name [, ...] [ CASCADE | RESTRICT ]
```

### DROP FUNCTION

Supprimer une fonction.

```sql
DROP FUNCTION name ( [ type [, ...] ] ) [ CASCADE | RESTRICT ]
```

### DROP GROUP

Supprimer un groupe d'utilisateurs.

```sql
DROP GROUP name
```

### DROP INDEX

Supprimer un index.

```sql
DROP INDEX name [, ...] [ CASCADE | RESTRICT ]
```

### DROP LANGUAGE

Supprimer un langage procédural.

```sql
DROP [ PROCEDURAL ] LANGUAGE name [ CASCADE | RESTRICT ]
```

### DROP OPERATOR

Supprimer un opérateur.

```sql
DROP OPERATOR name ( { left_type | NONE }, { right_type | NONE } )
[ CASCADE | RESTRICT ]
```

### DROP OPERATOR CLASS

Supprimer une classe d'opérateur.

```sql
DROP OPERATOR CLASS name USING index_method [ CASCADE | RESTRICT ]
```

### DROP RULE

Supprimer une règle de réécriture.

```sql
DROP RULE name ON relation [ CASCADE | RESTRICT ]
```

### DROP SCHEMA

Supprimer un schéma.

```sql
DROP SCHEMA name [, ...] [ CASCADE | RESTRICT ]
```

### DROP SEQUENCE

Supprimer une séquence.

```sql
DROP SEQUENCE name [, ...] [ CASCADE | RESTRICT ]
```

### DROP TABLE

Retirer une table.

```sql
DROP TABLE name [, ...] [ CASCADE | RESTRICT ]
```

### DROP TABLESPACE

Supprimer un tablespace.

```sql
DROP TABLESPACE tablespace_name
```

### DROP TRIGGER

Retirer une gâchette.

```sql
DROP TRIGGER name ON table [ CASCADE | RESTRICT ]
```

### DROP TYPE

Supprime un type de données.

```sql
DROP TYPE name [, ...] [ CASCADE | RESTRICT ]
```

### DROP USER

Supprimez un compte d'utilisateur de base de données.

```sql
DROP USER name
```

### DROP VIEW

Supprimer une vue.

```sql
DROP VIEW name [, ...] [ CASCADE | RESTRICT ]
```

### END

Valider la transaction en cours.

```sql
END [ WORK | TRANSACTION ]
```

### EXECUTE

Exécuter une déclaration préparée.

```sql
EXECUTE plan_name [ (parameter [, ...] ) ]
```

### EXPLAIN

Afficher le plan d'exécution d'une instruction.

```sql
EXPLAIN [ ANALYZE ] [ VERBOSE ] statement
```

### FETCH

Récupérer les lignes d'une requête à l'aide d'un curseur.

```sql
FETCH [ direction { FROM | IN } ] cursor_name
```

Où la direction peut être vide ou l'une de :

```sql
NEXT
PRIOR
FIRST
LAST
ABSOLUTE count
RELATIVE count
count
ALL
FORWARD
FORWARD count
FORWARD ALL
BACKWARD
BACKWARD count
BACKWARD ALL
```

### GRANT

Définir les privilèges d'accès.

```sql
GRANT { { SELECT | INSERT | UPDATE | DELETE | RULE | REFERENCES | TRIGGER }
[,...] | ALL [ PRIVILEGES ] }
ON [ TABLE ] table_name [, ...]
TO { username | GROUP group_name | PUBLIC } [, ...] [ WITH GRANT OPTION ]

GRANT { { CREATE | TEMPORARY | TEMP } [,...] | ALL [ PRIVILEGES ] }
ON DATABASE db_name [, ...]
TO { username | GROUP group_name | PUBLIC } [, ...] [ WITH GRANT OPTION ]

GRANT { CREATE | ALL [ PRIVILEGES ] }
ON TABLESPACE tablespace_name [, ...]
TO { username | GROUP group_name | PUBLIC } [, ...] [ WITH GRANT OPTION ]

GRANT { EXECUTE | ALL [ PRIVILEGES ] }
ON FUNCTION func_name ([type, ...]) [, ...]
TO { username | GROUP group_name | PUBLIC } [, ...] [ WITH GRANT OPTION ]

GRANT { USAGE | ALL [ PRIVILEGES ] }
ON LANGUAGE lang_name [, ...]
TO { username | GROUP group_name | PUBLIC } [, ...] [ WITH GRANT OPTION ]

GRANT { { CREATE | USAGE } [,...] | ALL [ PRIVILEGES ] }
ON SCHEMA schema_name [, ...]
TO { username | GROUP group_name | PUBLIC } [, ...] [ WITH GRANT OPTION ]
```

### INSERT

Créer de nouvelles lignes dans un tableau.

```sql
INSERT INTO table [ ( column [, ...] ) ]
{ DEFAULT VALUES | VALUES ( { expression | DEFAULT } [, ...] ) | query }
```

### LISTEN

Écoutez une notification.

```sql
LISTEN name
```

### LOAD

Charge ou recharge un fichier de bibliothèque partagée.

```sql
LOAD 'filename'
```

### LOCK

Verrouillez une table.

```sql
LOCK [ TABLE ] name [, ...] [ IN lock_mode MODE ] [ NOWAIT ]
```

Où lock_mode est l'un de :

```sql
ACCESS SHARE | ROW SHARE | ROW EXCLUSIVE | SHARE UPDATE EXCLUSIVE
| SHARE | SHARE ROW EXCLUSIVE | EXCLUSIVE | ACCESS EXCLUSIVE
```

### MOVE

Positionner un curseur.

```sql
MOVE [ direction { FROM | IN } ] cursor_name
```

### NOTIFY

Générer une notification.

```sql
NOTIFY name
```

### PREPARE

Préparer une déclaration pour l'exécution.

```sql
PREPARE plan_name [ (data_type [, ...] ) ] AS statement
```

### REINDEX

Reconstruire les index.

```sql
REINDEX { DATABASE | TABLE | INDEX } name [ FORCE ]
```

### RELEASE SAVEPOINT

Détruit un point de sauvegarde précédemment défini.

```sql
RELEASE [ SAVEPOINT ] savepoint_name
```

### RESET

Restaure la valeur d'un paramètre d'exécution à la valeur par défaut.

```sql
RESET name
RESET ALL
```

### REVOKE

Supprimer les privilèges d'accès.

```sql
REVOKE [ GRANT OPTION FOR ]
{ { SELECT | INSERT | UPDATE | DELETE | RULE | REFERENCES | TRIGGER }
[,...] | ALL [ PRIVILEGES ] }
ON [ TABLE ] table_name [, ...]
FROM { username | GROUP group_name | PUBLIC } [, ...]
[ CASCADE | RESTRICT ]

REVOKE [ GRANT OPTION FOR ]
{ { CREATE | TEMPORARY | TEMP } [,...] | ALL [ PRIVILEGES ] }
ON DATABASE db_name [, ...]
FROM { username | GROUP group_name | PUBLIC } [, ...]
[ CASCADE | RESTRICT ]

REVOKE [ GRANT OPTION FOR ]
{ CREATE | ALL [ PRIVILEGES ] }
ON TABLESPACE tablespace_name [, ...]
FROM { username | GROUP group_name | PUBLIC } [, ...]
[ CASCADE | RESTRICT ]

REVOKE [ GRANT OPTION FOR ]
{ EXECUTE | ALL [ PRIVILEGES ] }
ON FUNCTION func_name ([type, ...]) [, ...]
FROM { username | GROUP group_name | PUBLIC } [, ...]
[ CASCADE | RESTRICT ]

REVOKE [ GRANT OPTION FOR ]
{ USAGE | ALL [ PRIVILEGES ] }
ON LANGUAGE lang_name [, ...]
FROM { username | GROUP group_name | PUBLIC } [, ...]
[ CASCADE | RESTRICT ]

REVOKE [ GRANT OPTION FOR ]
{ { CREATE | USAGE } [,...] | ALL [ PRIVILEGES ] }
ON SCHEMA schema_name [, ...]
FROM { username | GROUP group_name | PUBLIC } [, ...]
[ CASCADE | RESTRICT ]
```

### ROLLBACK

Abandonner la transaction en cours.

```sql
ROLLBACK [ WORK | TRANSACTION ]
```

### ROLLBACK TO SAVEPOINT

Revenir à un point de sauvegarde.

```sql
ROLLBACK [ WORK | TRANSACTION ] TO [ SAVEPOINT ] savepoint_name
```

### SAVEPOINT

Définir un nouveau point de sauvegarde dans la transaction en cours.

```sql
SAVEPOINT savepoint_name
```

### SELECT

Récupérer les lignes d'une table ou d'une vue.

```sql
SELECT [ ALL | DISTINCT [ ON ( expression [, ...] ) ] ]
* | expression [ AS output_name ] [, ...]
[ FROM from_item [, ...] ]
[ WHERE condition ]
[ GROUP BY expression [, ...] ]
[ HAVING condition [, ...] ]
[ { UNION | INTERSECT | EXCEPT } [ ALL ] select ]
[ ORDER BY expression [ ASC | DESC | USING operator ] [, ...] ]
[ LIMIT { count | ALL } ]
[ OFFSET start ]
[ FOR UPDATE [ OF table_name [, ...] ] ]
Where from_item can be one of:
[ ONLY ] table_name [ * ] [ [ AS ] alias [ ( column_alias [, ...] ) ] ]
( select ) [ AS ] alias [ ( column_alias [, ...] ) ]
function_name ( [ argument [, ...] ] )
[ AS ] alias [ ( column_alias [, ...] | column_definition [, ...] ) ]
function_name ( [ argument [, ...] ] ) AS ( column_definition [, ...] )
from_item [ NATURAL ] join_type from_item
[ ON join_condition | USING ( join_column [, ...] ) ]
```

### SELECT INTO

Définir une nouvelle table à partir des résultats d'une requête.

```sql
SELECT [ ALL | DISTINCT [ ON ( expression [, ...] ) ] ]
* | expression [ AS output_name ] [, ...]
INTO [ TEMPORARY | TEMP ] [ TABLE ] new_table
[ FROM from_item [, ...] ]
[ WHERE condition ]
[ GROUP BY expression [, ...] ]
[ HAVING condition [, ...] ]
[ { UNION | INTERSECT | EXCEPT } [ ALL ] select ]
[ ORDER BY expression [ ASC | DESC | USING operator ] [, ...] ]
[ LIMIT { count | ALL } ]
[ OFFSET start ]
[ FOR UPDATE [ OF table_name [, ...] ] ]
```

### SET

Modifier un paramètre d'exécution.

```sql
SET [ SESSION | LOCAL ] name { TO | = } { value | 'value' | DEFAULT }
SET [ SESSION | LOCAL ] TIME ZONE { time_zone | LOCAL | DEFAULT }
```

### SET CONSTRAINTS

Définir les modes de vérification des contraintes pour la transaction en cours.

```sql
SET CONSTRAINTS { ALL | name [, ...] } { DEFERRED | IMMEDIATE }
```

### SET SESSION AUTHORIZATION

Définit l'identifiant de l'utilisateur de la session et l'identifiant de l'utilisateur actuel de la session en cours.

```sql
SET [ SESSION | LOCAL ] SESSION AUTHORIZATION username
SET [ SESSION | LOCAL ] SESSION AUTHORIZATION DEFAULT
RESET SESSION AUTHORIZATION
```

### SET TRANSACTION

Définit les caractéristiques de la transaction en cours.

```sql
SET TRANSACTION transaction_mode [, ...]
SET SESSION CHARACTERISTICS AS TRANSACTION transaction_mode [, ...]
```

Où transaction_mode est l'un de -

```sql
ISOLATION LEVEL { SERIALIZABLE | REPEATABLE READ | READ COMMITTED
| READ UNCOMMITTED }
READ WRITE | READ ONLY
```

### SHOW

Affiche la valeur d'un paramètre d'exécution.

```sql
SHOW name
SHOW ALL
```

### START TRANSACTION

Démarrer un bloc de transaction.

```sql
START TRANSACTION [ transaction_mode [, ...] ]
```

Où transaction_mode est l'un de :

```sql
ISOLATION LEVEL { SERIALIZABLE | REPEATABLE READ | READ COMMITTED
| READ UNCOMMITTED }
READ WRITE | READ ONLY
```

### TRUNCATE

Videz une table.

```sql
TRUNCATE [ TABLE ] name
```

### UNLISTEN

Arrêtez d'écouter une notification.

```sql
UNLISTEN { name | * }
```

### UPDATE

Mettre à jour les lignes d'une table.

```sql
UPDATE [ ONLY ] table SET column = { expression | DEFAULT } [, ...]
[ FROM from_list ]
[ WHERE condition ]
```

### VACUUM

Collecte des ordures et éventuellement analyse d'une base de données.

```sql
VACUUM [ FULL ] [ FREEZE ] [ VERBOSE ] [ table ]
VACUUM [ FULL ] [ FREEZE ] [ VERBOSE ] ANALYZE [ table [ (column [, ...] ) ] ]
```
