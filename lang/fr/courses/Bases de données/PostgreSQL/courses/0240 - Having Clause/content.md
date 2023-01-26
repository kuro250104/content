La clause **HAVING** nous permet de sélectionner des lignes particulières pour lesquelles le résultat de la fonction répond à certaines conditions.

La clause **WHERE** pose des conditions sur les colonnes sélectionnées, tandis que la clause **HAVING** pose des conditions sur les groupes créés par la clause **GROUP BY**.

## Syntaxe

Voici l'emplacement de la clause **HAVING** dans une requête **SELECT** :

```sql
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
```

La clause **HAVING** doit suivre la clause **GROUP BY** dans une requête et doit également précéder la clause **ORDER BY** si elle est utilisée. Voici la syntaxe de l'instruction **SELECT**, y compris la clause **HAVING** :

```sql
SELECT column1, column2
FROM table1, table2
WHERE [ conditions ]
GROUP BY column1, column2
HAVING [ conditions ]
ORDER BY column1, column2
```

## Exemple

Considérons la table COMPANY dont les enregistrements sont les suivants :

```bash
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

L'exemple suivant affiche les enregistrements pour lesquels le nombre de noms est inférieur à 2 :

```sql
testdb-# SELECT NAME FROM COMPANY GROUP BY name HAVING count(name) < 2;
```

Cela donnerait le résultat suivant :

```bash
 name
 -------
  Teddy
  Paul
  Mark
  David
  Allen
  Kim
  James
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

L'exemple suivant affiche les enregistrements pour lesquels le nombre de noms est supérieur à 1 :

```sql
testdb-# SELECT NAME FROM COMPANY GROUP BY name HAVING count(name) > 1;
```

Cela donnerait le résultat suivant :

```bash
name
-------
 Paul
 James
(2 rows)
```
