La requête **DELETE** de PostgreSQL est utilisée pour supprimer les enregistrements existants d'une table. Vous pouvez utiliser la clause **WHERE** avec la requête **DELETE** pour supprimer les lignes sélectionnées. Sinon, tous les enregistrements seront supprimés.

## Syntaxe

La syntaxe de base d'une requête **DELETE** avec la clause **WHERE** est la suivante :

```sql
DELETE FROM table_name
WHERE [condition];
```

Vous pouvez combiner un nombre N de conditions en utilisant les opérateurs **AND** ou **OR**.

## Exemple

Considérons la table COMPANY, dont les enregistrements sont les suivants :

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

L'exemple suivant permet de SUPPRIMER un client dont l'ID est 7 :

```sql
testdb=# DELETE FROM COMPANY WHERE ID = 2;
```

Maintenant, la table SOCIÉTÉ aura les enregistrements suivants :

```bash
id | name  | age | address     | salary
----+-------+-----+-------------+--------
  1 | Paul  |  32 | California  |  20000
  3 | Teddy |  23 | Norway      |  20000
  4 | Mark  |  25 | Rich-Mond   |  65000
  5 | David |  27 | Texas       |  85000
  6 | Kim   |  22 | South-Hall  |  45000
  7 | James |  24 | Houston     |  10000
(6 rows)
```

Si vous voulez SUPPRIMER tous les enregistrements de la table SOCIÉTÉ, vous n'avez pas besoin d'utiliser la clause **WHERE** avec les requêtes **DELETE**, qui seraient les suivantes :

```sql
testdb=# DELETE FROM COMPANY;
```

Maintenant, la table COMPANY ne contient plus d'enregistrement car tous les enregistrements ont été supprimés par l'instruction **DELETE**.
