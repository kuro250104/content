La clause SQLite **JOINS** est utilisée pour combiner les enregistrements de deux ou plusieurs tables dans une base de données. Une jointure est un moyen de combiner des champs de deux tables en utilisant des valeurs communes à chacune d'elles.

SQL définit trois grands types de jointures -

- Le **CROSS JOIN**
- La **JOIN INNER**
- Le **OUTER JOIN**

Avant de poursuivre, considérons deux tables COMPANY et DEPARTMENT. Nous avons déjà vu les instructions **INSERT** pour remplir la table COMPANY. Supposons donc que la liste des enregistrements disponibles dans la table SOCIÉTÉ -

```sql
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
```

Une autre table est DEPARTMENT avec la définition suivante -

```sql
CREATE TABLE DEPARTMENT(
    ID INT PRIMARY KEY      NOT NULL,
    DEPT           CHAR(50) NOT NULL,
    EMP_ID         INT      NOT NULL
);
```

Voici la liste des instructions **INSERT** pour alimenter la table DEPARTMENT -.

```sql
INSERT INTO DEPARTMENT (ID, DEPT, EMP_ID)
VALUES (1, 'IT Billing', 1 );

INSERT INTO DEPARTMENT (ID, DEPT, EMP_ID)
VALUES (2, 'Engineering', 2 );

INSERT INTO DEPARTMENT (ID, DEPT, EMP_ID)
VALUES (3, 'Finance', 7 );
```

Finalement, nous avons la liste suivante d'enregistrements disponibles dans la table DEPARTMENT -.

```bash
ID          DEPT        EMP_ID
----------  ----------  ----------
1           IT Billing  1
2           Engineering 2
3           Finance     7
```

## Le CROSS JOIN

**CROSS JOIN** fait correspondre chaque ligne de la première table avec chaque ligne de la deuxième table. Si les tableaux d'entrée ont respectivement x et y lignes, le tableau résultant aura x*y lignes. Comme les **CROSS JOIN** peuvent générer des tableaux extrêmement volumineux, il faut veiller à ne les utiliser que lorsque c'est approprié.

Voici la syntaxe d'un **CROSS JOIN**

```sql
SELECT ... FROM table1 CROSS JOIN table2 ...
```

En se basant sur les tableaux ci-dessus, vous pouvez écrire un CROSS JOIN comme suit -

```sql
sqlite> SELECT EMP_ID, NAME, DEPT FROM COMPANY CROSS JOIN DEPARTMENT;
```

La requête ci-dessus produira le résultat suivant -

```bash
EMP_ID      NAME        DEPT
----------  ----------  ----------
1           Paul        IT Billing
2           Paul        Engineering
7           Paul        Finance
1           Allen       IT Billing
2           Allen       Engineering
7           Allen       Finance
1           Teddy       IT Billing
2           Teddy       Engineering
7           Teddy       Finance
1           Mark        IT Billing
2           Mark        Engineering
7           Mark        Finance
1           David       IT Billing
2           David       Engineering
7           David       Finance
1           Kim         IT Billing
2           Kim         Engineering
7           Kim         Finance
1           James       IT Billing
2           James       Engineering
7           James       Finance
```

## Le INNER JOIN

**INNER JOIN** crée une nouvelle table de résultats en combinant les valeurs des colonnes de deux tables (table1 et table2) sur la base du prédicat de jointure. La requête compare chaque ligne de table1 avec chaque ligne de table2 pour trouver toutes les paires de lignes qui satisfont le prédicat de jonction. Lorsque le prédicat de jonction est satisfait, les valeurs des colonnes de chaque paire de lignes A et B sont combinées dans une ligne de résultat.

Un **INNER JOIN** est le type de jointure le plus courant et le plus courant par défaut. Vous pouvez utiliser le mot-clé **INNER** de manière facultative.

Voici la syntaxe de l'**INNER JOIN** -

```sql
SELECT ... FROM table1 [INNER] JOIN table2 ON conditional_expression ...
```

Pour éviter les redondances et raccourcir la formulation, les conditions **INNER JOIN** peuvent être déclarées avec une expression USING. Cette expression spécifie une liste d'une ou plusieurs colonnes.

```sql
SELECT ... FROM table1 JOIN table2 USING ( column1 ,... ) ...
```

Un **NATURAL JOIN** est similaire à un **JOIN...USING**, sauf qu'il teste automatiquement l'égalité entre les valeurs de chaque colonne qui existe dans les deux tables.

```sql
SELECT ... FROM table1 NATURAL JOIN table2...
```

En se basant sur les tableaux ci-dessus, vous pouvez écrire un **INNER JOIN** comme suit -

```sql
sqlite> SELECT EMP_ID, NAME, DEPT FROM COMPANY INNER JOIN DEPARTMENT
    ON COMPANY.ID = DEPARTMENT.EMP_ID;
```

La requête ci-dessus produira le résultat suivant -

```bash
EMP_ID      NAME        DEPT
----------  ----------  ----------
1           Paul        IT Billing
2           Allen       Engineering
7           James       Finance
```

## Le OUTER JOIN

**OUTER JOIN** est une extension de **INNER JOIN**. Bien que la norme SQL définissent trois types de **OUTER JOINS** : **LEFT**, **RIGHT**, et **FULL**, SQLite ne supporte que le **LEFT OUTER JOIN**.

Les **OUTER JOINS** ont une condition identique aux **INNER JOINS**, exprimée à l'aide d'un mot-clé **ON**, **USING**, ou **NATURAL**. La table de résultats initiale est calculée de la même manière. Une fois que la jointure primaire est calculée, une jointure **OUTER** prend toutes les lignes non jointes de l'une ou des deux tables, les remplit de **NULL** et les ajoute à la table résultante.

Voici la syntaxe de la jointure gauche (**LEFT OUTER JOIN**).

```sql
SELECT ... FROM table1 LEFT OUTER JOIN table2 ON conditional_expression ...
```

Pour éviter les redondances et raccourcir la formulation, les conditions **OUTER JOIN** peuvent être déclarées avec une expression **USING**. Cette expression spécifie une liste d'une ou plusieurs colonnes.

```sql
SELECT ... FROM table1 LEFT OUTER JOIN table2 USING ( column1 ,... ) ...
```

En se basant sur les tableaux ci-dessus, vous pouvez écrire une jointure externe comme suit -

```sql
sqlite> SELECT EMP_ID, NAME, DEPT FROM COMPANY LEFT OUTER JOIN DEPARTMENT
    ON COMPANY.ID = DEPARTMENT.EMP_ID;
```

La requête ci-dessus produira le résultat suivant -

```sql
EMP_ID      NAME        DEPT
----------  ----------  ----------
1           Paul        IT Billing
2           Allen       Engineering
            Teddy
            Mark
            David
            Kim
7           James       Finance
```