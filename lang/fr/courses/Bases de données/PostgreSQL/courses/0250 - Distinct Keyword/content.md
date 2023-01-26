Le mot clé **DISTINCT** de PostgreSQL est utilisé en conjonction avec l'instruction **SELECT** pour éliminer tous les enregistrements en double et ne récupérer que les enregistrements uniques.

Il peut y avoir une situation où vous avez plusieurs enregistrements en double dans une table. Lors de la récupération de ces enregistrements, il est plus logique de ne récupérer que les enregistrements uniques au lieu de récupérer les enregistrements en double.

## Syntaxe

La syntaxe de base du mot-clé **DISTINCT** pour éliminer les enregistrements en double est la suivante :

```sql
SELECT DISTINCT column1, column2,.....columnN
FROM table_name
WHERE [condition]
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

Ajoutons deux autres enregistrements à cette table comme suit :

```sql
INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (8, 'Paul', 32, 'California', 20000.00 );

INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (9, 'Allen', 25, 'Texas', 15000.00 );
```

Maintenant, les enregistrements dans la table SOCIÉTÉ seraient :

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
  8 | Paul  |  32 | California |  20000
  9 | Allen |  25 | Texas      |  15000
(9 rows)
```

Tout d'abord, voyons comment la requête **SELECT** suivante renvoie des enregistrements de salaire en double :

```sql
testdb=# SELECT name FROM COMPANY;
```

Cela donnerait le résultat suivant :

```bash
name
-------
 Paul
 Allen
 Teddy
 Mark
 David
 Kim
 James
 Paul
 Allen
(9 rows)
```

Maintenant, utilisons le mot clé **DISTINCT** avec la requête **SELECT** ci-dessus et voyons le résultat :

```sql
testdb=# SELECT DISTINCT name FROM COMPANY;
```

Cela donnerait le résultat suivant, où nous n'avons pas d'entrée en double :

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
