L'instruction **SELECT** de PostgreSQL est utilisée pour récupérer les données d'une table de base de données, qui renvoie les données sous la forme d'une table de résultats. Ces tables de résultats sont appelées ensembles de résultats.

## Syntaxe

La syntaxe de base de l'instruction **SELECT** est la suivante :

```sql
SELECT column1, column2, columnN FROM table_name;
```

Ici, colonne1, colonne2... sont les champs d'une table, dont vous voulez récupérer les valeurs. Si vous voulez récupérer tous les champs disponibles dans le champ, vous pouvez utiliser la syntaxe suivante :

```sql
SELECT * FROM table_name;
```

## Exemple

Considérons la table COMPANY dont les enregistrements sont les suivants :

```bash
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

L'exemple suivant permet de récupérer les champs ID, Nom et Salaire des clients disponibles dans la table CUSTOMERS.

```bash
testdb=# SELECT ID, NAME, SALARY FROM COMPANY ;
```

Cela donnerait le résultat suivant :

```bash
 id | name  | salary
 ----+-------+--------
   1 | Paul  |  20000
   2 | Allen |  15000
   3 | Teddy |  20000
   4 | Mark  |  65000
   5 | David |  85000
   6 | Kim   |  45000
   7 | James |  10000
(7 rows)
```

Si vous voulez récupérer tous les champs de la table CUSTOMERS, utilisez la requête suivante :

```bash
testdb=# SELECT * FROM COMPANY;
```

Cela donnerait le résultat suivant :

```bash
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
