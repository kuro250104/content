L'instruction PostgreSQL **DROP TABLE** est utilisée pour supprimer la définition d'une table et toutes les données, index, règles, triggers et contraintes associés à cette table.

Vous devez être prudent lorsque vous utilisez cette commande car une fois qu'une table est supprimée, toutes les informations disponibles dans la table sont également perdues à jamais.

## Syntaxe

La commande **DROP TABLE** est écrite comme cela :

```sql
DROP TABLE table_name;
```

## Exemple

Nous avions créé les tables DEPARTMENT et COMPANY dans le chapitre précédent. Tout d'abord, vérifiez ces tables (utilisez ```\d``` pour lister les tables) :

```bash
testdb-# \d
```

Cela donnerait le résultat suivant :

```bash
          List of relations
 Schema |    Name    | Type  |  Owner
--------+------------+-------+----------
 public | company    | table | postgres
 public | department | table | postgres
(2 rows)
```

Cela signifie que les tables DEPARTMENT et COMPANY sont présentes. Nous allons donc les supprimer de la manière suivante :

```bash
testdb=# drop table department, company;
```

Cela donnerait le résultat suivant :

```bash
DROP TABLE
testdb=# \d
relations found.
testdb=# 
```

Le message retourné par **DROP TABLE** indique que la commande **DROP TABLE** a été exécutée avec succès.
