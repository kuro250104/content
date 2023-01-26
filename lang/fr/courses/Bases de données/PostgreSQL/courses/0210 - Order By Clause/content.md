La clause **ORDER BY** de PostgreSQL est utilisée pour trier les données dans un ordre croissant ou décroissant, en fonction d'une ou plusieurs colonnes.

## Syntaxe

La syntaxe de base de la clause **ORDER BY** est la suivante :

```sql
SELECT column-list
FROM table_name
[WHERE condition]
[ORDER BY column1, column2, .. columnN] [ASC | DESC];
```

Vous pouvez utiliser plus d'une colonne dans la clause **ORDER BY**. Assurez-vous que, quelle que soit la colonne que vous utilisez pour trier, cette colonne doit être disponible dans la liste des colonnes.

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

Voici un exemple, qui trierait le résultat dans l'ordre croissant par SALAIRE :

```sql
testdb=# SELECT * FROM COMPANY ORDER BY AGE ASC;
```

Cela donnerait le résultat suivant :

```bash
  id | name  | age | address    | salary
 ----+-------+-----+------------+--------
   6 | Kim   |  22 | South-Hall |  45000
   3 | Teddy |  23 | Norway     |  20000
   7 | James |  24 | Houston    |  10000
   8 | Paul  |  24 | Houston    |  20000
   4 | Mark  |  25 | Rich-Mond  |  65000
   2 | Allen |  25 | Texas      |  15000
   5 | David |  27 | Texas      |  85000
   1 | Paul  |  32 | California |  20000
   9 | James |  44 | Norway     |   5000
  10 | James |  45 | Texas      |   5000
(10 rows)
```

Voici un exemple, qui trierait le résultat dans l'ordre croissant par NOM et SALAIRE :

```sql
testdb=# SELECT * FROM COMPANY ORDER BY NAME, SALARY ASC;
```

Cela donnerait le résultat suivant :

```bash
id | name  | age | address      | salary
----+-------+-----+--------------+--------
  2 | Allen |  25 | Texas        |  15000
  5 | David |  27 | Texas        |  85000
 10 | James |  45 | Texas        |   5000
  9 | James |  44 | Norway       |   5000
  7 | James |  24 | Houston      |  10000
  6 | Kim   |  22 | South-Hall   |  45000
  4 | Mark  |  25 | Rich-Mond    |  65000
  1 | Paul  |  32 | California   |  20000
  8 | Paul  |  24 | Houston      |  20000
  3 | Teddy |  23 | Norway       |  20000
(10 rows)
```

Voici un exemple, qui trierait le résultat dans l'ordre décroissant par NOM :

```sql
testdb=# SELECT * FROM COMPANY ORDER BY NAME DESC;
```

Cela donnerait le résultat suivant :

```bash
id | name  | age | address    | salary
----+-------+-----+------------+--------
  3 | Teddy |  23 | Norway     |  20000
  1 | Paul  |  32 | California |  20000
  8 | Paul  |  24 | Houston    |  20000
  4 | Mark  |  25 | Rich-Mond  |  65000
  6 | Kim   |  22 | South-Hall |  45000
  7 | James |  24 | Houston    |  10000
  9 | James |  44 | Norway     |   5000
 10 | James |  45 | Texas      |   5000
  5 | David |  27 | Texas      |  85000
  2 | Allen |  25 | Texas      |  15000
(10 rows)
```
