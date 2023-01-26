Les opérateurs PostgreSQL **AND** et **OR** sont utilisés pour combiner plusieurs conditions afin de réduire les données sélectionnées dans une déclaration PostgreSQL. Ces deux opérateurs sont appelés opérateurs conjonctifs.

Ces opérateurs fournissent un moyen d'effectuer des comparaisons multiples avec différents opérateurs dans la même déclaration PostgreSQL.

## The AND Operator

L'opérateur **AND** permet l'existence de plusieurs conditions dans la clause **WHERE** d'une déclaration PostgreSQL. En utilisant l'opérateur **AND**, la condition complète sera considérée comme vraie lorsque toutes les conditions sont vraies. Par exemple, ```[condition1] ET [condition2]``` ne sera vraie que si la condition1 et la condition2 sont toutes deux vraies.

### Syntaxe

La syntaxe de base de l'opérateur **AND** avec la clause **WHERE** est la suivante :

```sql
SELECT column1, column2, columnN
FROM table_name
WHERE [condition1] AND [condition2]...AND [conditionN];
```

Vous pouvez combiner un nombre N de conditions en utilisant l'opérateur **AND**. Pour qu'une action soit prise par l'instruction PostgreSQL, qu'il s'agisse d'une transaction ou d'une requête, toutes les conditions séparées par le **AND** doivent être VRAIES.

### Exemple

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

L'instruction **SELECT** suivante répertorie tous les enregistrements pour lesquels AGE est supérieur ou égal à 25 **AND** le salaire est supérieur ou égal à 65000.00 :

```sql
testdb=# SELECT * FROM COMPANY WHERE AGE >= 25 AND SALARY >= 65000;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
id | name  | age | address    | salary
----+-------+-----+------------+--------
  4 | Mark  |  25 | Rich-Mond  |  65000
  5 | David |  27 | Texas      |  85000
(2 rows)
```

## The OR Operator

L'opérateur **OR** est également utilisé pour combiner plusieurs conditions dans la clause **WHERE** d'une déclaration PostgreSQL. En utilisant l'opérateur **OR**, la condition complète sera considérée comme vraie si au moins une des conditions est vraie. Par exemple, ```[condition1] OU [condition2]``` sera vrai si la condition1 ou la condition2 est vraie.

### Syntaxe

La syntaxe de base de l'opérateur **OR** avec la clause **WHERE** est la suivante :

```sql
SELECT column1, column2, columnN
FROM table_name
WHERE [condition1] OR [condition2]...OR [conditionN]
```

Vous pouvez combiner un nombre N de conditions en utilisant l'opérateur **OR**. Pour qu'une action soit prise par l'instruction PostgreSQL, qu'il s'agisse d'une transaction ou d'une requête, seule UNE des conditions séparées par l'opérateur **OR** doit être VRAIE.

### Exemple

Considérons la table SOCIÉTÉ, comportant les enregistrements suivants :

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

L'instruction **SELECT** suivante répertorie tous les enregistrements pour lesquels **AGE** est supérieur ou égal à 25 **OR** le salaire est supérieur ou égal à 65000.00 :

```sql
testdb=# SELECT * FROM COMPANY WHERE AGE >= 25 OR SALARY >= 65000;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
id | name  | age | address    | salary
----+-------+-----+------------+--------
  1 | Paul  |  32 | California |  20000
  2 | Allen |  25 | Texas      |  15000
  4 | Mark  |  25 | Rich-Mond  |  65000
  5 | David |  27 | Texas      |  85000
(4 rows)
```
