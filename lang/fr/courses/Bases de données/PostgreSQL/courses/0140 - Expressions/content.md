Une expression est une combinaison d'une ou plusieurs valeurs, opérateurs et fonctions PostgreSQL qui s'évaluent à une valeur.

Les EXPRESSIONS PostgreSQL sont comme des formules et elles sont écrites en langage de requête. Vous pouvez également les utiliser pour interroger la base de données pour un ensemble spécifique de données.

## Syntaxe

Considérons la syntaxe de base de l'instruction **SELECT** comme suit :

```sql
SELECT column1, column2, columnN
FROM table_name
WHERE [CONDITION | EXPRESSION];
```

Il existe différents types d'expressions PostgreSQL, qui sont mentionnés ci-dessous :

## PostgreSQL - Boolean Expressions

Les expressions booléennes de PostgreSQL récupèrent les données sur la base d'une valeur unique correspondante. Voici la syntaxe :

```sql
SELECT column1, column2, columnN
FROM table_name
WHERE SINGLE VALUE MATCHTING EXPRESSION;
```

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

Voici un exemple simple montrant l'utilisation des expressions booléennes de PostgreSQL :

```sql
testdb=# SELECT * FROM COMPANY WHERE SALARY = 10000;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
id | name  | age | address  | salary
----+-------+-----+----------+--------
  7 | James |  24 | Houston  |  10000
(1 row)
```

## PostgreSQL - Numeric Expression

Ces expressions sont utilisées pour effectuer toute opération mathématique dans toute requête. Voici la syntaxe :

```sql
SELECT numerical_expression as  OPERATION_NAME
[FROM table_name WHERE CONDITION] ;
```

Ici, numerical_expression est utilisé pour une expression mathématique ou toute formule. Voici un exemple simple montrant l'utilisation des expressions numériques SQL :

```bash
testdb=# SELECT (15 + 6) AS ADDITION ;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
addition
----------
    21
(1 row)
```

Il existe plusieurs fonctions intégrées telles que ```avg()```, ```sum()```, ```count()``` pour effectuer ce que l'on appelle des calculs de données agrégées par rapport à une table ou une colonne de table spécifique.

```bash
testdb=# SELECT COUNT(*) AS "RECORDS" FROM COMPANY;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
RECORDS
---------
    7
(1 row)
```

## PostgreSQL - Date Expressions

Les expressions de date renvoient les valeurs de date et d'heure actuelles du système et ces expressions sont utilisées dans diverses manipulations de données.

```bash
testdb=#  SELECT CURRENT_TIMESTAMP;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
             now
-------------------------------
 2013-05-06 14:38:28.078+05:30
(1 row)
```
