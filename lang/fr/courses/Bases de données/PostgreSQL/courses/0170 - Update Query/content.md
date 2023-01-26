La requête **UPDATE** de PostgreSQL est utilisée pour modifier les enregistrements existants dans une table. Vous pouvez utiliser la clause **WHERE** avec la requête **UPDATE** pour mettre à jour les lignes sélectionnées. Sinon, toutes les lignes seront mises à jour.

## Syntaxe

La syntaxe de base d'une requête **UPDATE** avec la clause **WHERE** est la suivante :

```sql
UPDATE table_name
SET column1 = value1, column2 = value2...., columnN = valueN
WHERE [condition];
```

Vous pouvez combiner un nombre N de conditions en utilisant les opérateurs **AND** ou **OR**.

## Exemple

Considérons la table COMPANY, dont les enregistrements sont les suivants :

```sql
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

Voici un exemple qui mettrait à jour l'ADRESSE d'un client dont l'ID est 6 :

```sql
testdb=# UPDATE COMPANY SET SALARY = 15000 WHERE ID = 3;
```

Maintenant, la table COMPANY aura les enregistrements suivants :

```bash
id | name  | age | address    | salary
----+-------+-----+------------+--------
  1 | Paul  |  32 | California |  20000
  2 | Allen |  25 | Texas      |  15000
  4 | Mark  |  25 | Rich-Mond  |  65000
  5 | David |  27 | Texas      |  85000
  6 | Kim   |  22 | South-Hall |  45000
  7 | James |  24 | Houston    |  10000
  3 | Teddy |  23 | Norway     |  15000
(7 rows)
```

Si vous voulez modifier toutes les valeurs des colonnes ADRESSE et SALAIRE dans la table SOCIÉTÉ, vous n'avez pas besoin d'utiliser la clause **WHERE** et la requête **UPDATE** serait la suivante :

```sql
testdb=# UPDATE COMPANY SET ADDRESS = 'Texas', SALARY=20000;
```

Maintenant, la table SOCIÉTÉ aura les enregistrements suivants :

```bash
id | name  | age | address | salary
----+-------+-----+---------+--------
  1 | Paul  |  32 | Texas   |  20000
  2 | Allen |  25 | Texas   |  20000
  4 | Mark  |  25 | Texas   |  20000
  5 | David |  27 | Texas   |  20000
  6 | Kim   |  22 | Texas   |  20000
  7 | James |  24 | Texas   |  20000
  3 | Teddy |  23 | Texas   |  20000
(7 rows)
```
