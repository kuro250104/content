La clause **WHERE** de PostgreSQL est utilisée pour spécifier une condition lors de l'extraction des données d'une seule table ou de la jonction avec plusieurs tables.

Si la condition donnée est satisfaite, alors seulement elle renvoie une valeur spécifique de la table. Vous pouvez filtrer les lignes que vous ne voulez pas inclure dans le jeu de résultats en utilisant la clause **WHERE**.

La clause **WHERE** n'est pas seulement utilisée dans l'instruction **SELECT**, mais aussi dans les instructions **UPDATE**, **DELETE**, etc. que nous examinerons dans les chapitres suivants.

## Syntaxe

La syntaxe de base de l'instruction **SELECT** avec la clause **WHERE** est la suivante :

```sql
SELECT column1, column2, columnN
FROM table_name
WHERE [search_condition];
```

Vous pouvez spécifier une condition de recherche en utilisant des opérateurs de comparaison ou des opérateurs logiques, comme **>**, **<**, **=**, **LIKE**, **NOT**, etc. Les exemples suivants permettent de comprendre ce concept.

## Exemple

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

Voici des exemples simples montrant l'utilisation des opérateurs logiques de PostgreSQL. L'instruction **SELECT** suivante répertorie tous les enregistrements pour lesquels l'âge est supérieur ou égal à 25 et le salaire est supérieur ou égal à 65000.00 :

```sql
testdb=# SELECT * FROM COMPANY WHERE AGE >= 25 AND SALARY >= 65000;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
id | name  | age |  address   | salary
----+-------+-----+------------+--------
  4 | Mark  |  25 | Rich-Mond  |  65000
  5 | David |  27 | Texas      |  85000
(2 rows)
```

L'instruction **SELECT** suivante répertorie tous les enregistrements pour lesquels AGE est supérieur ou égal à 25 OU le salaire est supérieur ou égal à 65000.00 :

```sql
testdb=# SELECT * FROM COMPANY WHERE AGE >= 25 OR SALARY >= 65000;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
id | name  | age | address     | salary
----+-------+-----+-------------+--------
  1 | Paul  |  32 | California  |  20000
  2 | Allen |  25 | Texas       |  15000
  4 | Mark  |  25 | Rich-Mond   |  65000
  5 | David |  27 | Texas       |  85000
(4 rows)
```

L'instruction **SELECT** suivante répertorie tous les enregistrements où AGE n'est pas NULL, c'est-à-dire tous les enregistrements, car aucun enregistrement n'a un AGE égal à NULL.

```bash
testdb=#  SELECT * FROM COMPANY WHERE AGE IS NOT NULL;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
 id | name  | age | address    | salary
 ----+-------+-----+------------+--------
   1 | Paul  |  32 | California |  20000
   2 | Allen |  25 | Texas      |  15000
   3 | Teddy |  23 | Norway     |  20000
   4 | Mark  |  25 | Rich-Mond  |  65000
   5 | David |  27 | Texas      |  85000
   6 | Kim   |  22 | South-Hall |  45000
   7 | James |  24 | Houston    |  10000
(7 rows)
```

L'instruction **SELECT** suivante répertorie tous les enregistrements dont le NOM commence par "Pa", peu importe ce qui vient après "Pa" :

```sql
testdb=# SELECT * FROM COMPANY WHERE NAME LIKE 'Pa%';
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
id | name | age |address    | salary
----+------+-----+-----------+--------
  1 | Paul |  32 | California|  20000
```

L'instruction **SELECT** suivante liste tous les enregistrements pour lesquels la valeur AGE est soit 25, soit 27 :

```sql
testdb=# SELECT * FROM COMPANY WHERE AGE IN ( 25, 27 );
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
id | name  | age | address    | salary
----+-------+-----+------------+--------
  2 | Allen |  25 | Texas      |  15000
  4 | Mark  |  25 | Rich-Mond  |  65000
  5 | David |  27 | Texas      |  85000
(3 rows)
```

L'instruction **SELECT** suivante répertorie tous les enregistrements pour lesquels la valeur AGE n'est ni 25 ni 27 :

```sql
testdb=# SELECT * FROM COMPANY WHERE AGE NOT IN ( 25, 27 );
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
id | name  | age | address    | salary
----+-------+-----+------------+--------
  1 | Paul  |  32 | California |  20000
  3 | Teddy |  23 | Norway     |  20000
  6 | Kim   |  22 | South-Hall |  45000
  7 | James |  24 | Houston    |  10000
(4 rows)
```

L'instruction **SELECT** suivante répertorie tous les enregistrements dont la valeur AGE est comprise entre 25 et 27 ans :

```sql
testdb=# SELECT * FROM COMPANY WHERE AGE BETWEEN 25 AND 27;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
id | name  | age | address    | salary
----+-------+-----+------------+--------
  2 | Allen |  25 | Texas      |  15000
  4 | Mark  |  25 | Rich-Mond  |  65000
  5 | David |  27 | Texas      |  85000
(3 rows)
```

L'instruction **SELECT** suivante utilise une sous-requête SQL où la sous-requête trouve tous les enregistrements avec le champ AGE ayant un SALAIRE > 65000 et ensuite la clause **WHERE** est utilisée avec l'opérateur **EXISTS** pour lister tous les enregistrements où AGE de la requête externe existe dans le résultat renvoyé par la sous-requête :

```sql
testdb=# SELECT AGE FROM COMPANY
        WHERE EXISTS (SELECT AGE FROM COMPANY WHERE SALARY > 65000);
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
age
-----
  32
  25
  23
  25
  27
  22
  24
(7 rows)
```

L'instruction **SELECT** suivante utilise une sous-requête SQL où la sous-requête trouve tous les enregistrements avec le champ AGE ayant un SALAIRE > 65000 et ensuite la clause **WHERE** est utilisée avec l'opérateur > pour lister tous les enregistrements où l'AGE de la requête externe est plus grand que l'âge dans le résultat renvoyé par la sous-requête :

```sql
testdb=# SELECT * FROM COMPANY
        WHERE AGE > (SELECT AGE FROM COMPANY WHERE SALARY > 65000);
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
id | name | age | address    | salary
----+------+-----+------------+--------
  1 | Paul |  32 | California |  20000
```
