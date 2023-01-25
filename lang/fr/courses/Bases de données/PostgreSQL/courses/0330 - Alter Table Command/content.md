La commande **ALTER TABLE** de PostgreSQL est utilisée pour ajouter, supprimer ou modifier des colonnes dans une table existante.

Vous pouvez également utiliser la commande **ALTER TABLE** pour ajouter et supprimer diverses contraintes sur une table existante.

## Syntaxe

La syntaxe de base d'**ALTER TABLE** pour ajouter une nouvelle colonne dans une table existante est la suivante :

```sql
ALTER TABLE table_name ADD column_name datatype;
```

La syntaxe de base d'**ALTER TABLE** pour **DROP COLUMN** dans une table existante est la suivante :

```sql
ALTER TABLE table_name DROP COLUMN column_name;
```

La syntaxe de base d'**ALTER TABLE** pour changer le **TYPE DE DONNÉES** d'une colonne dans une table est la suivante :

```sql
ALTER TABLE table_name ALTER COLUMN column_name TYPE datatype;
```

La syntaxe de base d'**ALTER TABLE** pour ajouter une contrainte **NOT NULL** à une colonne dans une table est la suivante :

```sql
ALTER TABLE table_name MODIFY column_name datatype NOT NULL;
```

La syntaxe de base d'**ALTER TABLE** pour ajouter un **CONSTRAINT UNIQUE** à une table est la suivante :

```sql
ALTER TABLE table_name
ADD CONSTRAINT MyUniqueConstraint UNIQUE(column1, column2...);
```

La syntaxe de base d'**ALTER TABLE** pour ajouter un **CONSTRAINT DE CONTRÔLE** à une table est la suivante :

```sql
ALTER TABLE table_name
ADD CONSTRAINT MyUniqueConstraint CHECK (CONDITION);
```

La syntaxe de base d'**ALTER TABLE** pour ajouter la contrainte **PRIMARY KEY** à une table est la suivante :

```sql
ALTER TABLE table_name
ADD CONSTRAINT MyPrimaryKey PRIMARY KEY (column1, column2...);
```

La syntaxe de base d'**ALTER TABLE** pour **DROP CONSTRAINT** à partir d'une table est la suivante :

```sql
ALTER TABLE table_name
DROP CONSTRAINT MyUniqueConstraint;
```

Si vous utilisez MySQL, le code est le suivant :

```sql
ALTER TABLE table_name
DROP INDEX MyUniqueConstraint;
```

La syntaxe de base de la commande ALTER TABLE pour supprimer la contrainte PRIMARY KEY d'une table est la suivante :

```sql
ALTER TABLE table_name
DROP CONSTRAINT MyPrimaryKey;
```

Si vous utilisez MySQL, le code est le suivant :

```sql
ALTER TABLE table_name
DROP PRIMARY KEY;
```

## Exemple

Considérons que notre table SOCIÉTÉ possède les enregistrements suivants :

```bash
id | name  | age | address   | salary
----+-------+-----+-----------+--------
  1 | Paul  |  32 | California|  20000
  2 | Allen |  25 | Texas     |  15000
  3 | Teddy |  23 | Norway    |  20000
  4 | Mark  |  25 | Rich-Mond |  65000
  5 | David |  27 | Texas     |  85000
  6 | Kim   |  22 | South-Hall|  45000
  7 | James |  24 | Houston   |  10000
```

L'exemple suivant permet d'AJOUTER une nouvelle colonne dans une table existante :

```sql
testdb=# ALTER TABLE COMPANY ADD GENDER char(1);
```

Maintenant, la table COMPANY est modifiée et le résultat de l'instruction SELECT est le suivant :

```sql
id | name  | age | address     | salary | gender
----+-------+-----+-------------+--------+--------
  1 | Paul  |  32 | California  |  20000 |
  2 | Allen |  25 | Texas       |  15000 |
  3 | Teddy |  23 | Norway      |  20000 |
  4 | Mark  |  25 | Rich-Mond   |  65000 |
  5 | David |  27 | Texas       |  85000 |
  6 | Kim   |  22 | South-Hall  |  45000 |
  7 | James |  24 | Houston     |  10000 |
(7 rows)
```

Voici un exemple de suppression de la colonne "sexe" d'une table existante :

```sql
testdb=# ALTER TABLE COMPANY DROP GENDER;
```

Maintenant, la table COMPANY est modifiée et le résultat de l'instruction **SELECT** est le suivant :

```bash
id | name  | age | address   | salary
----+-------+-----+-----------+--------
  1 | Paul  |  32 | California|  20000
  2 | Allen |  25 | Texas     |  15000
  3 | Teddy |  23 | Norway    |  20000
  4 | Mark  |  25 | Rich-Mond |  65000
  5 | David |  27 | Texas     |  85000
  6 | Kim   |  22 | South-Hall|  45000
  7 | James |  24 | Houston   |  10000
```
