Dans PostgreSQL, la requête **WITH** permet d'écrire des instructions auxiliaires à utiliser dans une requête plus importante. Elle permet de décomposer des requêtes complexes et volumineuses en formes plus simples, facilement lisibles. Ces instructions, souvent appelées Common Table Expressions ou CTE, peuvent être considérées comme définissant des tables temporaires qui n'existent que pour une seule requête.

La requête **WITH** étant une requête CTE, elle est particulièrement utile lorsque la sous-requête est exécutée plusieurs fois. Elle est également utile à la place des tables temporaires. Elle calcule l'agrégation une fois et nous permet de la référencer par son nom (qui peut être multiple) dans les requêtes.

La clause **WITH** doit être définie avant d'être utilisée dans la requête.

### Syntaxe

La syntaxe de base de la requête **WITH** est la suivante :

```sql
WITH
    name_for_summary_data AS (
        SELECT Statement)
    SELECT columns
    FROM name_for_summary_data
    WHERE conditions <=> (
        SELECT column
        FROM name_for_summary_data)
    [ORDER BY columns]
```

Où **name_for_summary_data** est le nom donné à la clause **WITH**. Le **name_for_summary_data**  peut être le même que celui d'une table existante et sera prioritaire.
Vous pouvez utiliser des instructions modifiant les données (**INSERT**, **UPDATE** ou **DELETE**) dans WITH. Cela vous permet d'effectuer plusieurs opérations différentes dans la même requête.

## Recursive WITH

Les requêtes **WITH récursives** ou **hiérarchiques** sont une forme d'**ETC** où un **ETC** peut faire référence à lui-même, c'est-à-dire qu'une requête **WITH** peut faire référence à sa propre sortie, d'où le nom de récursif.

### Exemple

Considérons la table COMPANY dont les enregistrements sont les suivants :

```bash
testdb# select * from COMPANY;
 id | name  | age | address   | salary
----+-------+-----+-----------+--------
  1 | Paul  |  32 | California|  20000
  2 | Allen |  25 | Texas     |  15000
  3 | Teddy |  23 | Norway    |  20000
  4 | Mark  |  25 | Rich-Mond |  65000
  5 | David |  27 | Texas     |  85000
  6 | Kim   |  22 | South-Hall|  45000
  7 | James |  24 | Houston   |  10000
(7 rows)
```

Maintenant, écrivons une requête en utilisant la clause **WITH** pour sélectionner les enregistrements du tableau ci-dessus, comme suit :

```sql
With CTE AS
(Select
 ID
, NAME
, AGE
, ADDRESS
, SALARY
FROM COMPANY )
Select * From CTE;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

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
(7 rows)
```

Maintenant, écrivons une requête en utilisant le mot clé **RECURSIVE** avec la clause **WITH**, pour trouver la somme des salaires inférieurs à 20000, comme suit :

```sql
WITH RECURSIVE t(n) AS (
    VALUES (0)
    UNION ALL
    SELECT SALARY FROM COMPANY WHERE SALARY < 20000
)
SELECT sum(n) FROM t;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
 sum
-------
 25000
(1 row)
```

Rédigeons une requête en utilisant des instructions de modification de données avec la clause **WITH**, comme indiqué ci-dessous.

Tout d'abord, créez une table COMPANY1 similaire à la table COMPANY. La requête de l'exemple déplace effectivement des lignes de la table COMPANY vers la table COMPANY1. L'instruction **DELETE** de la clause **WITH** supprime les lignes spécifiées de la table COMPANY, et renvoie leur contenu au moyen de la clause **RETURNING**. Ensuite, la requête primaire lit cette sortie et l'insère dans la table COMPANY1 :

```sql
CREATE TABLE COMPANY1(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);

WITH moved_rows AS (
    DELETE FROM COMPANY
    WHERE
        SALARY >= 30000
    RETURNING *
)
INSERT INTO COMPANY1 (SELECT * FROM moved_rows);
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```sql
INSERT 0 3
```

Maintenant, les enregistrements dans les tables SOCIÉTÉ et SOCIÉTÉ1 sont les suivants :

```bash
testdb=# SELECT * FROM COMPANY;
 id | name  | age |  address   | salary
----+-------+-----+------------+--------
  1 | Paul  |  32 | California |  20000
  2 | Allen |  25 | Texas      |  15000
  3 | Teddy |  23 | Norway     |  20000
  7 | James |  24 | Houston    |  10000
(4 rows)


testdb=# SELECT * FROM COMPANY1;
 id | name  | age | address | salary
----+-------+-----+-------------+--------
  4 | Mark  |  25 | Rich-Mond   |  65000
  5 | David |  27 | Texas       |  85000
  6 | Kim   |  22 | South-Hall  |  45000
(3 rows)
```
