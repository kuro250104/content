La clause **GROUP BY** de SQLite est utilisée en collaboration avec l'instruction **SELECT** pour organiser des données identiques en groupes.

La clause **GROUP BY** suit la clause WHERE dans une instruction **SELECT** et précède la clause **ORDER BY**.

## Syntaxe

Voici la syntaxe de base de la clause **GROUP BY**. La clause **GROUP BY** doit suivre les conditions de la clause WHERE et doit précéder la clause ORDER BY si elle est utilisée.

```sql
SELECT column-list
FROM table_name
WHERE [ conditions ]
GROUP BY column1, column2....columnN
ORDER BY column1, column2....columnN
```

Vous pouvez utiliser plus d'une colonne dans la clause GROUP BY. Assurez-vous que, quelle que soit la colonne que vous utilisez pour regrouper, cette colonne doit être disponible dans la liste de colonnes.

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
```

Si vous voulez connaître le montant total du salaire de chaque client, alors la requête GROUP BY sera la suivante : -.

```sql
sqlite> SELECT NAME, SUM(SALARY) FROM COMPANY GROUP BY NAME;
```

Cela donnera le résultat suivant -

```bash
NAME        SUM(SALARY)
----------  -----------
Allen       15000.0
David       85000.0
James       10000.0
Kim         45000.0
Mark        65000.0
Paul        20000.0
Teddy       20000.0
```

Maintenant, créons trois enregistrements supplémentaires dans la table COMPANY en utilisant les instructions INSERT suivantes.

```bash
INSERT INTO COMPANY VALUES (8, 'Paul', 24, 'Houston', 20000.00 );
INSERT INTO COMPANY VALUES (9, 'James', 44, 'Norway', 5000.00 );
INSERT INTO COMPANY VALUES (10, 'James', 45, 'Texas', 5000.00 );
```

Maintenant, notre table a les enregistrements suivants avec des noms en double.

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

Utilisons à nouveau la même instruction pour regrouper tous les enregistrements à l'aide de la colonne NOM, comme suit

```sql
sqlite> SELECT NAME, SUM(SALARY) FROM COMPANY GROUP BY NAME ORDER BY NAME;
```

Cela donnera le résultat suivant.

```bash
NAME        SUM(SALARY)
----------  -----------
Allen       15000
David       85000
James       20000
Kim         45000
Mark        65000
Paul        40000
Teddy       20000
```

Utilisons la clause **ORDER BY** en même temps que la clause **GROUP BY** de la manière suivante -.

```sql
sqlite>  SELECT NAME, SUM(SALARY) 
    FROM COMPANY GROUP BY NAME ORDER BY NAME DESC;
```

Cela donnera le résultat suivant.

```bash
NAME        SUM(SALARY)
----------  -----------
Teddy       20000
Paul        40000
Mark        65000
Kim         45000
James       20000
David       85000
Allen       15000
```