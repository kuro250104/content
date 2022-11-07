La clause **HAVING** vous permet de spécifier des conditions qui filtrent les résultats des groupes qui apparaissent dans les résultats finaux.

La clause **WHERE** place des conditions sur les colonnes sélectionnées, tandis que la clause **HAVING** place des conditions sur les groupes créés par la clause **GROUP BY**.

## Syntaxe

Voici la position de la clause HAVING dans une requête **SELECT**.

```sql
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
```

La clause **HAVING** doit suivre la clause **GROUP BY** dans une requête et doit également précéder la clause ORDER BY si elle est utilisée. Voici la syntaxe de l'instruction **SELECT**, y compris la clause **HAVING**.

```sql
SELECT column1, column2
FROM table1, table2
WHERE [ conditions ]
GROUP BY column1, column2
HAVING [ conditions ]
ORDER BY column1, column2
```

## Exemple

Considérons une table de l'entreprise avec les enregistrements suivants.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
8           Paul        24          Houston     20000.0
9           James       44          Norway      5000.0
10          James       45          Texas       5000.0
```

Voici l'exemple qui affichera l'enregistrement pour lequel le nombre de noms est inférieur à 2.

```sql
sqlite > SELECT * FROM COMPANY GROUP BY name HAVING count(name) < 2;
```

Cela donnera le résultat suivant.

```sql
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
2           Allen       25          Texas       15000
5           David       27          Texas       85000
6           Kim         22          South-Hall  45000
4           Mark        25          Rich-Mond   65000
3           Teddy       23          Norway      20000
```

Voici l'exemple qui affichera l'enregistrement pour lequel le nombre de noms est supérieur à 2.

```sql
sqlite > SELECT * FROM COMPANY GROUP BY name HAVING count(name) > 2;
```

Cela donnera le résultat suivant.

```sql
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
10          James       45          Texas       5000
```