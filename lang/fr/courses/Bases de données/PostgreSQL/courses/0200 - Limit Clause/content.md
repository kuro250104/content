La clause **LIMIT** de PostgreSQL est utilisée pour limiter la quantité de données retournées par l'instruction **SELECT**.

## Syntaxe

La syntaxe de base de l'instruction **SELECT** avec la clause **LIMIT** est la suivante :

```sql
SELECT column1, column2, columnN
FROM table_name
LIMIT [no of rows]
```

Voici la syntaxe de la clause **LIMIT** lorsqu'elle est utilisée avec la clause **OFFSET** :

```sql
SELECT column1, column2, columnN
FROM table_name
LIMIT [no of rows] OFFSET [row num]
```

**LIMIT** et **OFFSET** vous permettent de ne récupérer qu'une partie des lignes qui sont générées par le reste de la requête.

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

Voici un exemple qui limite le nombre de lignes dans le tableau en fonction du nombre de lignes que vous voulez extraire du tableau :

```sql
testdb=# SELECT * FROM COMPANY LIMIT 4;
```

Cela donnerait le résultat suivant :

```bash
id | name  | age | address     | salary
----+-------+-----+-------------+--------
  1 | Paul  |  32 | California  |  20000
  2 | Allen |  25 | Texas       |  15000
  3 | Teddy |  23 | Norway      |  20000
  4 | Mark  |  25 | Rich-Mond   |  65000
(4 rows)
```

Cependant, dans certaines situations, vous pouvez avoir besoin de prélever un ensemble d'enregistrements à partir d'un décalage particulier. Voici un exemple qui permet de récupérer trois enregistrements à partir de la troisième position :

```sql
testdb=# SELECT * FROM COMPANY LIMIT 3 OFFSET 2;
```

Cela donnerait le résultat suivant :

```bash
id | name  | age | address   | salary
----+-------+-----+-----------+--------
  3 | Teddy |  23 | Norway    |  20000
  4 | Mark  |  25 | Rich-Mond |  65000
  5 | David |  27 | Texas     |  85000
(3 rows)
```
