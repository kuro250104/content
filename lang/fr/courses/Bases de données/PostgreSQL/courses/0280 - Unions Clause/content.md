La clause/opérateur **UNION** de PostgreSQL est utilisée pour combiner les résultats de deux ou plusieurs instructions **SELECT** sans renvoyer de lignes en double.

Pour utiliser **UNION**, chaque **SELECT** doit avoir le même nombre de colonnes sélectionnées, le même nombre d'expressions de colonnes, le même type de données, et les avoir dans le même ordre, mais elles ne doivent pas nécessairement avoir la même longueur.

## Syntaxe

La syntaxe de base de **UNION** est la suivante :

```sql
SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]

UNION

SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]
```

Ici, la condition donnée peut être n'importe quelle expression donnée en fonction de vos besoins.

## Exemple

Considérons les deux tableaux suivants : (a) Le tableau de la SOCIÉTÉ est le suivant :

```bash
testdb=# SELECT * from COMPANY;
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
testdb=# SELECT * from DEPARTMENT;
 id | dept        | emp_id
----+-------------+--------
  1 | IT Billing  |      1
  2 | Engineering |      2
  3 | Finance     |      7
  4 | Engineering |      3
  5 | Finance     |      4
  6 | Engineering |      5
  7 | Finance     |      6
(7 rows)
```

Maintenant, joignons ces deux tables en utilisant l'instruction **SELECT** avec la clause **UNION** comme suit :

```sql
testdb=# SELECT EMP_ID, NAME, DEPT FROM COMPANY INNER JOIN DEPARTMENT
    ON COMPANY.ID = DEPARTMENT.EMP_ID
    UNION
        SELECT EMP_ID, NAME, DEPT FROM COMPANY LEFT OUTER JOIN DEPARTMENT
            ON COMPANY.ID = DEPARTMENT.EMP_ID;
```

Cela donnerait le résultat suivant :

```bash
emp_id | name  |  dept
--------+-------+--------------
     5 | David | Engineering
     6 | Kim   | Finance
     2 | Allen | Engineering
     3 | Teddy | Engineering
     4 | Mark  | Finance
     1 | Paul  | IT Billing
     7 | James | Finance
(7 rows)
```

## The UNION ALL Clause

L'opérateur **UNION ALL** est utilisé pour combiner les résultats de deux instructions **SELECT**, y compris les lignes en double. Les mêmes règles qui s'appliquent à **UNION** s'appliquent également à l'opérateur **UNION ALL**.

## Syntaxe

La syntaxe de base de **UNION ALL** est la suivante :

```sql
SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]

UNION ALL

SELECT column1 [, column2 ]
FROM table1 [, table2 ]
[WHERE condition]
```

Ici, la condition donnée peut être n'importe quelle expression donnée en fonction de vos besoins.

## Exemple

Maintenant, joignons les deux tables mentionnées ci-dessus dans notre déclaration **SELECT** comme suit :

```sql
testdb=# SELECT EMP_ID, NAME, DEPT FROM COMPANY INNER JOIN DEPARTMENT
    ON COMPANY.ID = DEPARTMENT.EMP_ID
    UNION ALL
        SELECT EMP_ID, NAME, DEPT FROM COMPANY LEFT OUTER JOIN DEPARTMENT
            ON COMPANY.ID = DEPARTMENT.EMP_ID;
```

Cela donnerait le résultat suivant :

```bash
emp_id | name  | dept
--------+-------+--------------
    1  | Paul  | IT Billing
    2  | Allen | Engineering
    7  | James | Finance
    3  | Teddy | Engineering
    4  | Mark  | Finance
    5  | David | Engineering
    6  | Kim   | Finance
    1  | Paul  | IT Billing
    2  | Allen | Engineering
    7  | James | Finance
    3  | Teddy | Engineering
    4  | Mark  | Finance
    5  | David | Engineering
    6  | Kim   | Finance
(14 rows)
```
