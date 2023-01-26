La clause Joins de PostgreSQL est utilisée pour combiner les enregistrements de deux ou plusieurs tables dans une base de données. Un **JOIN** est un moyen de combiner des champs de deux tables en utilisant des valeurs communes à chacune.

Les types de jointures dans PostgreSQL sont :

- The CROSS JOIN
- The INNER JOIN
- The LEFT OUTER JOIN
- The RIGHT OUTER JOIN
- The FULL OUTER JOIN

Avant de poursuivre, considérons deux tables, COMPANY et DEPARTMENT. Nous avons déjà vu les instructions **INSERT** pour remplir la table SOCIÉTÉ. Supposons donc que la liste des enregistrements disponibles dans la table SOCIÉTÉ :

```bash
id | name  | age | address   | salary | join_date
----+-------+-----+-----------+--------+-----------
  1 | Paul  |  32 | California|  20000 | 2001-07-13
  3 | Teddy |  23 | Norway    |  20000 |
  4 | Mark  |  25 | Rich-Mond |  65000 | 2007-12-13
  5 | David |  27 | Texas     |  85000 | 2007-12-13
  2 | Allen |  25 | Texas     |        | 2007-12-13
  8 | Paul  |  24 | Houston   |  20000 | 2005-07-13
  9 | James |  44 | Norway    |   5000 | 2005-07-13
 10 | James |  45 | Texas     |   5000 | 2005-07-13
```

Une autre table est DEPARTMENT, à la définition suivante :

```sql
CREATE TABLE DEPARTMENT(
    ID INT PRIMARY KEY      NOT NULL,
    DEPT           CHAR(50) NOT NULL,
    EMP_ID         INT      NOT NULL
);
```

Voici la liste des instructions **INSERT** pour alimenter la table DEPARTMENT :

```sql
INSERT INTO DEPARTMENT (ID, DEPT, EMP_ID)
VALUES (1, 'IT Billing', 1 );

INSERT INTO DEPARTMENT (ID, DEPT, EMP_ID)
VALUES (2, 'Engineering', 2 );

INSERT INTO DEPARTMENT (ID, DEPT, EMP_ID)
VALUES (3, 'Finance', 7 );
```

Finalement, nous avons la liste suivante d'enregistrements disponibles dans la table DEPARTMENT :

```bash
id | dept        | emp_id
----+-------------+--------
  1 | IT Billing  |  1
  2 | Engineering |  2
  3 | Finance     |  7
```

## The CROSS JOIN

Un **CROSS JOIN** fait correspondre chaque ligne de la première table avec chaque ligne de la deuxième table. Si les tableaux d'entrée ont respectivement ```x``` et``` y``` colonnes, le tableau résultant aura ```x+y``` colonnes. Comme les **CROSS JOIN** peuvent générer des tableaux extrêmement volumineux, il faut veiller à ne les utiliser que lorsque cela est approprié.

Voici la syntaxe d'un **CROSS JOIN** :

```sql
SELECT ... FROM table1 CROSS JOIN table2 ...
```

En se basant sur les tableaux ci-dessus, nous pouvons écrire un **CROSS JOIN** comme suit :

```sql
testdb=# SELECT EMP_ID, NAME, DEPT FROM COMPANY CROSS JOIN DEPARTMENT;
```

La requête donnée ci-dessus produira le résultat suivant :

```bash
emp_id| name  |  dept
------|-------|--------------
    1 | Paul  | IT Billing
    1 | Teddy | IT Billing
    1 | Mark  | IT Billing
    1 | David | IT Billing
    1 | Allen | IT Billing
    1 | Paul  | IT Billing
    1 | James | IT Billing
    1 | James | IT Billing
    2 | Paul  | Engineering
    2 | Teddy | Engineering
    2 | Mark  | Engineering
    2 | David | Engineering
    2 | Allen | Engineering
    2 | Paul  | Engineering
    2 | James | Engineering
    2 | James | Engineering
    7 | Paul  | Finance
    7 | Teddy | Finance
    7 | Mark  | Finance
    7 | David | Finance
    7 | Allen | Finance
    7 | Paul  | Finance
    7 | James | Finance
    7 | James | Finance
```

## The INNER JOIN

Un **INNER JOIN** crée une nouvelle table de résultats en combinant les valeurs des colonnes de deux tables (table1 et table2) sur la base du prédicat de jointure. La requête compare chaque ligne de table1 avec chaque ligne de table2 pour trouver toutes les paires de lignes qui satisfont le prédicat de jonction. Lorsque le prédicat de jonction est satisfait, les valeurs des colonnes de chaque paire de lignes correspondantes de table1 et table2 sont combinées dans une ligne de résultat.

Un **INNER JOIN** est le type de jointure le plus courant et le type de jointure par défaut. Vous pouvez utiliser le mot-clé **INNER** de manière facultative.

La syntaxe de **INNER JOIN** est la suivante :

```sql
SELECT table1.column1, table2.column2...
FROM table1
INNER JOIN table2
ON table1.common_filed = table2.common_field;
```

Sur la base des tableaux ci-dessus, nous pouvons écrire un **INNER JOIN** comme suit :

```sql
testdb=# SELECT EMP_ID, NAME, DEPT FROM COMPANY INNER JOIN DEPARTMENT
        ON COMPANY.ID = DEPARTMENT.EMP_ID;
```

La requête donnée ci-dessus produira le résultat suivant :

```bash
emp_id | name  | dept
--------+-------+------------
    1  | Paul  | IT Billing
    2  | Allen | Engineering
```

## The LEFT OUTER JOIN

Le **OUTER JOIN** est une extension du **INNER JOIN**. La norme SQL définit trois types de **OUTER JOINS** : **LEFT**, **RIGHT**, et **FULL** et PostgreSQL supporte tous ces types.

Dans le cas d'un **LEFT OUTER JOIN**, une jointure interne est d'abord effectuée. Ensuite, pour chaque ligne de la table T1 qui ne satisfait pas la condition de jointure avec une ligne de la table T2, une ligne jointe est ajoutée avec des valeurs nulles dans les colonnes de T2. Ainsi, la table jointe comporte toujours au moins une ligne pour chaque ligne de T1.

Voici la syntaxe de la jointure **LEFT OUTER JOIN** :

```sql
SELECT ... FROM table1 LEFT OUTER JOIN table2 ON conditional_expression ...
```

En se basant sur les tableaux ci-dessus, nous pouvons écrire une jointure interne comme suit :

```sql
testdb=# SELECT EMP_ID, NAME, DEPT FROM COMPANY LEFT OUTER JOIN DEPARTMENT
   ON COMPANY.ID = DEPARTMENT.EMP_ID;
```

La requête donnée ci-dessus produira le résultat suivant :

```bash
emp_id | name  | dept
--------+-------+------------
    1  | Paul  | IT Billing
    2  | Allen | Engineering
       | James |
       | David |
       | Paul  |
       | Mark  |
       | Teddy |
       | James |
```

## The RIGHT OUTER JOIN

Tout d'abord, une jointure interne est effectuée. Ensuite, pour chaque ligne de la table T2 qui ne satisfait pas à la condition de jointure avec une ligne de la table T1, une ligne jointe est ajoutée avec des valeurs nulles dans les colonnes de T1. Il s'agit de l'inverse d'une jointure gauche ; le tableau de résultats contiendra toujours une ligne pour chaque ligne de T2.

Voici la syntaxe d'une jointure **OUTER DROITE**.

```sql
SELECT ... FROM table1 RIGHT OUTER JOIN table2 ON conditional_expression ...
```

En se basant sur les tableaux ci-dessus, nous pouvons écrire une jointure interne comme suit :

```sql
testdb=# SELECT EMP_ID, NAME, DEPT FROM COMPANY RIGHT OUTER JOIN DEPARTMENT
    ON COMPANY.ID = DEPARTMENT.EMP_ID;
```

La requête donnée ci-dessus produira le résultat suivant :

```bash
emp_id | name  | dept
--------+-------+--------
    1  | Paul  | IT Billing
    2  | Allen | Engineering
    7  |       | Finance
```

## The FULL OUTER JOIN

Tout d'abord, une jointure interne est effectuée. Ensuite, pour chaque ligne de la table T1 qui ne satisfait pas la condition de jointure avec une ligne de la table T2, une ligne jointe est ajoutée avec des valeurs nulles dans les colonnes de T2. De plus, pour chaque ligne de T2 qui ne satisfait pas la condition de jointure avec une ligne de T1, une ligne jointe avec des valeurs nulles dans les colonnes de T1 est ajoutée.

Voici la syntaxe de la jointure **FULL OUTER JOIN** :

```sql
SELECT ... FROM table1 FULL OUTER JOIN table2 ON conditional_expression ...
```

En se basant sur les tableaux ci-dessus, nous pouvons écrire une jointure interne comme suit :

```sql
testdb=# SELECT EMP_ID, NAME, DEPT FROM COMPANY FULL OUTER JOIN DEPARTMENT
    ON COMPANY.ID = DEPARTMENT.EMP_ID;
```

La requête donnée ci-dessus produira le résultat suivant :

```bash
emp_id | name  | dept
--------+-------+---------------
    1  | Paul  | IT Billing
    2  | Allen | Engineering
    7  |       | Finance
       | James |
       | David |
       | Paul  |
       | Mark  |
       | Teddy |
       | James |
```
