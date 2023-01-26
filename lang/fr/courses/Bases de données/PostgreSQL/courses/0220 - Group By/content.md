La clause **GROUP BY** de PostgreSQL est utilisée en collaboration avec l'instruction **SELECT** pour regrouper les lignes d'une table dont les données sont identiques. Cela permet d'éliminer les redondances dans le résultat et/ou de calculer des agrégats qui s'appliquent à ces groupes.

La clause **GROUP BY** suit la clause **WHERE** dans une instruction **SELECT** et précède la clause **ORDER BY**.

## Syntaxe

La syntaxe de base de la clause **GROUP BY** est donnée ci-dessous. La clause **GROUP BY** doit suivre les conditions de la clause **WHERE** et doit précéder la clause **ORDER BY** si elle est utilisée.

```sql
SELECT column-list
FROM table_name
WHERE [ conditions ]
GROUP BY column1, column2....columnN
ORDER BY column1, column2....columnN
```

Vous pouvez utiliser plus d'une colonne dans la clause **GROUP BY**. Assurez-vous que, quelle que soit la colonne que vous utilisez pour regrouper, cette colonne doit être disponible dans la liste des colonnes.

## Exemple

Considérons la table COMPANY dont les enregistrements sont les suivants :

```sql
# select * from COMPANY;
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

Si vous voulez connaître le montant total du salaire de chaque client, alors la requête **GROUP BY** sera la suivante :

```sql
testdb=# SELECT NAME, SUM(SALARY) FROM COMPANY GROUP BY NAME;
```

Cela donnerait le résultat suivant :

```bash
 name  |  sum
 -------+-------
  Teddy | 20000
  Paul  | 20000
  Mark  | 65000
  David | 85000
  Allen | 15000
  Kim   | 45000
  James | 10000
(7 rows)
```

Maintenant, créons trois enregistrements supplémentaires dans la table SOCIÉTÉ en utilisant les instructions **INSERT** suivantes :

```sql
INSERT INTO COMPANY VALUES (8, 'Paul', 24, 'Houston', 20000.00);
INSERT INTO COMPANY VALUES (9, 'James', 44, 'Norway', 5000.00);
INSERT INTO COMPANY VALUES (10, 'James', 45, 'Texas', 5000.00);
```

Maintenant, notre table a les enregistrements suivants avec des noms en double :

```bash
 id | name  | age | address      | salary
 ----+-------+-----+--------------+--------
   1 | Paul  |  32 | California   |  20000
   2 | Allen |  25 | Texas        |  15000
   3 | Teddy |  23 | Norway       |  20000
   4 | Mark  |  25 | Rich-Mond    |  65000
   5 | David |  27 | Texas        |  85000
   6 | Kim   |  22 | South-Hall   |  45000
   7 | James |  24 | Houston      |  10000
   8 | Paul  |  24 | Houston      |  20000
   9 | James |  44 | Norway       |   5000
  10 | James |  45 | Texas        |   5000
(10 rows)
```

Utilisons à nouveau la même instruction pour regrouper tous les enregistrements à l'aide de la colonne NOM, comme suit :

```sql
testdb=# SELECT NAME, SUM(SALARY) FROM COMPANY GROUP BY NAME ORDER BY NAME;
```

Cela donnerait le résultat suivant :

```bash
name  |  sum
-------+-------
 Allen | 15000
 David | 85000
 James | 20000
 Kim   | 45000
 Mark  | 65000
 Paul  | 40000
 Teddy | 20000
(7 rows)
```

Utilisons la clause **ORDER BY** en même temps que la clause **GROUP BY** de la manière suivante :

```sql
testdb=#  SELECT NAME, SUM(SALARY)
        FROM COMPANY GROUP BY NAME ORDER BY NAME DESC;
```

Cela donnerait le résultat suivant :

```bash
name  |  sum
-------+-------
 Teddy | 20000
 Paul  | 40000
 Mark  | 65000
 Kim   | 45000
 James | 20000
 David | 85000
 Allen | 15000
(7 rows)
```
