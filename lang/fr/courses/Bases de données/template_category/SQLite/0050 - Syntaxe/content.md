## Introduction

SQLite est suivi d'un ensemble unique de règles et de directives appelées Syntaxe. Ce chapitre énumère toutes les syntaxes de base de SQLite.

## Sensibilité des cas

Le point important à noter est que SQLite est insensible à la casse, c'est-à-dire que les clauses GLOB et glob ont la même signification dans les instructions SQLite.

## Commentaires

Les commentaires SQLite sont des notes supplémentaires que vous pouvez ajouter dans votre code SQLite pour en améliorer la lisibilité. Ils peuvent apparaître n'importe où, y compris à l'intérieur d'expressions et au milieu d'autres instructions SQL, mais ils ne peuvent pas être imbriqués.

Les commentaires SQL commencent par deux caractères "-" consécutifs (ASCII 0x2d) et s'étendent jusqu'au prochain caractère de nouvelle ligne (ASCII 0x0a) ou jusqu'à la fin de l'entrée, selon ce qui se produit en premier.

Vous pouvez également utiliser des commentaires de style C, qui commencent par "/*" et s'étendent jusqu'à la paire de caractères "*/" suivante ou jusqu'à la fin de la saisie, selon la première éventualité. Les commentaires de style C peuvent s'étendre sur plusieurs lignes.

```sql
sqlite> .help -- This is a single line comment
```

## SQLite Statements

Toutes les instructions SQLite commencent par l'un des mots-clés suivants : SELECT, INSERT, UPDATE, DELETE, ALTER, DROP, etc., et toutes les instructions se terminent par un point-virgule ( ;).

## SQLite ANALYZE Statement

```sql
ANALYZE;
or
ANALYZE database_name;
or
ANALYZE database_name.table_name;
```

## SQLite AND/OR Clause

```sql
SELECT column1, column2....columnN
FROM table_name
WHERE CONDITION-1 {AND|OR} CONDITION-2;
```

## SQLite ALTER TABLE Statement

```sql
ALTER TABLE table_name ADD COLUMN column_def...;
```

## SQLite ALTER TABLE Statement (Rename)

```sql
ALTER TABLE table_name RENAME TO new_table_name;
```

## SQLite ATTACH DATABASE Statement

```sql
ATTACH DATABASE 'DatabaseName' As 'Alias-Name';
```

## SQLite BEGIN TRANSACTION Statement

```sql
BEGIN;
or
BEGIN EXCLUSIVE TRANSACTION;
```

## SQLite BETWEEN Clause

```sql
SELECT column1, column2....columnN
FROM table_name
WHERE column_name BETWEEN val-1 AND val-2;
```

## SQLite COMMIT Statement

```sql
COMMIT;
```

## SQLite CREATE INDEX Statement

```sql
CREATE INDEX index_name
ON table_name ( column_name COLLATE NOCASE );
```

## SQLite CREATE UNIQUE INDEX Statement

```sql
CREATE UNIQUE INDEX index_name
ON table_name ( column1, column2,...columnN);
```

## SQLite CREATE TABLE Statement

```sql
CREATE TABLE table_name(
    column1 datatype,
    column2 datatype,
    column3 datatype,
    .....
    columnN datatype,
    PRIMARY KEY( one or more columns )
);
```

## SQLite CREATE TRIGGER Statement

```sql
CREATE TRIGGER database_name.trigger_name 
BEFORE INSERT ON table_name FOR EACH ROW
BEGIN 
    stmt1; 
    stmt2;
    ....
END;
```

## SQLite CREATE VIEW Statement

```sql
CREATE VIEW database_name.view_name AS
SELECT statement....;
```

## SQLite CREATE VIRTUAL TABLE Statement

```sql
CREATE VIRTUAL TABLE database_name.table_name USING weblog( access.log );
or
CREATE VIRTUAL TABLE database_name.table_name USING fts3( );
```

## SQLite COMMIT TRANSACTION Statement

```sql
COMMIT;
```

## SQLite COUNT Clause

```sql
SELECT COUNT(column_name)
FROM table_name
WHERE CONDITION;
```

## SQLite DELETE Statement

```sql
DELETE FROM table_name
WHERE {CONDITION};
```

## SQLite DETACH DATABASE Statement

```sql
DETACH DATABASE 'Alias-Name';
```

## SQLite DISTINCT Clause

```sql
SELECT DISTINCT column1, column2....columnN
FROM table_name;
```

## SQLite DROP INDEX Statement

```sql
DROP INDEX database_name.index_name;
```

## SQLite DROP TABLE Statement

```sql
DROP TABLE database_name.table_name;
```

## SQLite DROP VIEW Statement

```sql
DROP INDEX database_name.view_name;
```

## SQLite DROP TRIGGER Statement

```sql
DROP INDEX database_name.trigger_name;
```

## SQLite EXISTS Clause

```sql
SELECT column1, column2....columnN
FROM table_name
WHERE column_name EXISTS (SELECT * FROM   table_name );
```

## SQLite EXPLAIN Statement

```sql
EXPLAIN INSERT statement...;
or 
EXPLAIN QUERY PLAN SELECT statement...;
SQLite GLOB Clause
SELECT column1, column2....columnN
FROM table_name
WHERE column_name GLOB { PATTERN };
```

## SQLite GROUP BY Clause

```sql
SELECT SUM(column_name)
FROM table_name
WHERE CONDITION
GROUP BY column_name;
```

## SQLite HAVING Clause

```sql
SELECT SUM(column_name)
FROM table_name
WHERE CONDITION
GROUP BY column_name
HAVING (arithematic function condition);
```

## SQLite INSERT INTO Statement

```sql
INSERT INTO table_name( column1, column2....columnN)
VALUES ( value1, value2....valueN);
```

## SQLite IN Clause

```sql
SELECT column1, column2....columnN
FROM table_name
WHERE column_name IN (val-1, val-2,...val-N);
```

## SQLite Like Clause

```sql
SELECT column1, column2....columnN
FROM table_name
WHERE column_name LIKE { PATTERN };
```

## SQLite NOT IN Clause

```sql
SELECT column1, column2....columnN
FROM table_name
WHERE column_name NOT IN (val-1, val-2,...val-N);
```

## SQLite ORDER BY Clause

```sql
SELECT column1, column2....columnN
FROM table_name
WHERE CONDITION
ORDER BY column_name {ASC|DESC};
```

## SQLite PRAGMA Statement

```sql
PRAGMA pragma_name;

For example:

PRAGMA page_size;
PRAGMA cache_size = 1024;
PRAGMA table_info(table_name);
```

## SQLite RELEASE SAVEPOINT Statement

```sql
RELEASE savepoint_name;
```

## SQLite REINDEX Statement

```sql
REINDEX collation_name;
REINDEX database_name.index_name;
REINDEX database_name.table_name;
```

## SQLite ROLLBACK Statement

```sql
ROLLBACK;
or
ROLLBACK TO SAVEPOINT savepoint_name;
```

## SQLite SAVEPOINT Statement

```sql
SAVEPOINT savepoint_name;
```

## SQLite SELECT Statement

```sql
SELECT column1, column2....columnN
FROM table_name;
```

## SQLite UPDATE Statement

```sql
UPDATE table_name
SET column1 = value1, column2 = value2....columnN=valueN
[ WHERE  CONDITION ];
```

## SQLite VACUUM Statement

```sql
VACUUM;
```

## SQLite WHERE Clause

```sql
SELECT column1, column2....columnN
FROM table_name
WHERE CONDITION;
```