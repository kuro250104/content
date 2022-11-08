La clause/opérateur SQLite **UNION** est utilisée pour combiner les résultats de deux ou plusieurs instructions **SELECT** sans renvoyer de lignes en double.

Pour utiliser **UNION**, chaque **SELECT** doit avoir le même nombre de colonnes sélectionnées, le même nombre d'expressions de colonnes, le même type de données, et les avoir dans le même ordre, mais ils ne doivent pas nécessairement être de la même longueur.

## Syntaxe

Voici la syntaxe de base de **UNION**.

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

Considérez les deux tableaux suivants : (a) Tableau de l'entreprise comme suit -

```bash
sqlite> select * from COMPANY;
ID          NAME                  AGE         ADDRESS     SALARY
----------  --------------------  ----------  ----------  ----------
1           Paul                  32          California  20000.0
2           Allen                 25          Texas       15000.0
3           Teddy                 23          Norway      20000.0
4           Mark                  25          Rich-Mond   65000.0
5           David                 27          Texas       85000.0
6           Kim                   22          South-Hall  45000.0
7           James                 24          Houston     10000.0
```

(b) Une autre table est DEPARTMENT comme suit -

```bash
ID          DEPT                  EMP_ID
----------  --------------------  ----------
1           IT Billing            1
2           Engineering           2
3           Finance               7
4           Engineering           3
5           Finance               4
6           Engineering           5
7           Finance               6
```

Maintenant, joignons ces deux tables en utilisant l'instruction SELECT avec la clause UNION comme suit -.

```sql
sqlite> SELECT EMP_ID, NAME, DEPT FROM COMPANY INNER JOIN DEPARTMENT
    ON COMPANY.ID = DEPARTMENT.EMP_ID
    
    UNION
    
    SELECT EMP_ID, NAME, DEPT FROM COMPANY LEFT OUTER JOIN DEPARTMENT
    ON COMPANY.ID = DEPARTMENT.EMP_ID;
```

Cela donnera le résultat suivant.

```bash
EMP_ID      NAME                  DEPT
----------  --------------------  ----------
1           Paul                  IT Billing
2           Allen                 Engineering
3           Teddy                 Engineering
4           Mark                  Finance
5           David                 Engineering
6           Kim                   Finance
7           James                 Finance
```

## La clause UNION ALL

L'opérateur **UNION ALL** est utilisé pour combiner les résultats de deux instructions **SELECT**, y compris les lignes en double.

Les mêmes règles qui s'appliquent à **UNION** s'appliquent également à l'opérateur **UNION ALL**.

### Syntaxe

Voici la syntaxe de base de **UNION ALL**.

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

Maintenant, joignons les deux tables mentionnées dans notre déclaration SELECT comme suit -

```sql
sqlite>  SELECT EMP_ID, NAME, DEPT FROM COMPANY INNER JOIN DEPARTMENT
    ON COMPANY.ID = DEPARTMENT.EMP_ID
    
    UNION ALL

    SELECT EMP_ID, NAME, DEPT FROM COMPANY LEFT OUTER JOIN DEPARTMENT
    ON COMPANY.ID = DEPARTMENT.EMP_ID;
```

Cela donnera le résultat suivant.

```bash
EMP_ID      NAME                  DEPT
----------  --------------------  ----------
1           Paul                  IT Billing
2           Allen                 Engineering
3           Teddy                 Engineering
4           Mark                  Finance
5           David                 Engineering
6           Kim                   Finance
7           James                 Finance
1           Paul                  IT Billing
2           Allen                 Engineering
3           Teddy                 Engineering
4           Mark                  Finance
5           David                 Engineering
6           Kim                   Finance
7           James                 Finance
```