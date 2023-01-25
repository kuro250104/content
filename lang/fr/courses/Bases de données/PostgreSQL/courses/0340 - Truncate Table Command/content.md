La commande PostgreSQL **TRUNCATE TABLE** est utilisée pour supprimer les données complètes d'une table existante. Vous pouvez également utiliser la commande DROP TABLE pour supprimer une table complète, mais cela supprimerait la structure complète de la table de la base de données et vous devriez recréer cette table à nouveau si vous souhaitez stocker des données.

Cette commande a le même effet que la commande **DELETE** sur chaque table, mais comme elle n'analyse pas réellement les tables, elle est plus rapide. De plus, elle récupère immédiatement de l'espace disque, sans nécessiter une opération VACUUM ultérieure. Cette fonction est particulièrement utile pour les grandes tables.

## Syntaxe

La syntaxe de base de TRUNCATE TABLE est la suivante :

```sql
TRUNCATE TABLE  table_name;
```

## Exemple

Considérons que la table SOCIÉTÉ possède les enregistrements suivants :

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

L'exemple suivant permet de tronquer :

```sql
testdb=# TRUNCATE TABLE COMPANY;
```

Maintenant, la table COMPANY est tronquée et le résultat de l'instruction SELECT est le suivant :

```sql
testdb=# SELECT * FROM CUSTOMERS;
 id | name | age | address | salary
----+------+-----+---------+--------
(0 rows)
```
