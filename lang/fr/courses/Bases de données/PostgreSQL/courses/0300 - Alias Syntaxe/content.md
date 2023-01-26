Vous pouvez renommer une table ou une colonne temporairement en donnant un autre nom, qui est connu comme **ALIAS**. L'utilisation d'alias de table permet de renommer une table dans une instruction PostgreSQL particulière. Le renommage est un changement temporaire et le nom réel de la table ne change pas dans la base de données.

Les alias de colonne sont utilisés pour renommer les colonnes d'une table dans le but d'une requête PostgreSQL particulière.

## Syntaxe

La syntaxe de base de l'alias de table est la suivante :

```sql
SELECT column1, column2....
FROM table_name AS alias_name
WHERE [condition];
```

La syntaxe de base de l'alias de colonne est la suivante :

```sql
SELECT column_name AS alias_name
FROM table_name
WHERE [condition];
```

## Exemple

Considérons les deux tableaux suivants : (a) Le tableau de la SOCIÉTÉ est le suivant :

```bash
testdb=# select * from COMPANY;
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

(b) Une autre table est DEPARTMENT comme suit :

```bash
id | dept         | emp_id
----+--------------+--------
  1 | IT Billing   |      1
  2 | Engineering  |      2
  3 | Finance      |      7
  4 | Engineering  |      3
  5 | Finance      |      4
  6 | Engineering  |      5
  7 | Finance      |      6
(7 rows)
```

Maintenant, voici l'utilisation de **TABLE ALIAS** où nous utilisons C et D comme alias pour les tables COMPANY et DEPARTMENT, respectivement :

```sql
testdb=# SELECT C.ID, C.NAME, C.AGE, D.DEPT
    FROM COMPANY AS C, DEPARTMENT AS D
    WHERE  C.ID = D.EMP_ID;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
id | name  | age |  dept
----+-------+-----+------------
  1 | Paul  |  32 | IT Billing
  2 | Allen |  25 | Engineering
  7 | James |  24 | Finance
  3 | Teddy |  23 | Engineering
  4 | Mark  |  25 | Finance
  5 | David |  27 | Engineering
  6 | Kim   |  22 | Finance
(7 rows)
```

Voyons un exemple de l'utilisation de **COLUMN ALIAS** où COMPANY_ID est un alias de la colonne ID et COMPANY_NAME est un alias de la colonne name :

```bash
testdb=# SELECT C.ID AS COMPANY_ID, C.NAME AS COMPANY_NAME, C.AGE, D.DEPT
    FROM COMPANY AS C, DEPARTMENT AS D
    WHERE  C.ID = D.EMP_ID;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
company_id | company_name | age | dept
------------+--------------+-----+------------
      1    | Paul         |  32 | IT Billing
      2    | Allen        |  25 | Engineering
      7    | James        |  24 | Finance
      3    | Teddy        |  23 | Engineering
      4    | Mark         |  25 | Finance
      5    | David        |  27 | Engineering
      6    | Kim          |  22 | Finance
(7 rows)
```
