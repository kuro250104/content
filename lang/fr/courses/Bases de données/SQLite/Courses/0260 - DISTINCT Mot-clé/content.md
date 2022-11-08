Le mot-clé SQLite **DISTINCT** est utilisé en conjonction avec l'instruction **SELECT** pour éliminer tous les enregistrements en double et ne récupérer que les enregistrements uniques.

Il peut y avoir une situation où vous avez plusieurs enregistrements en double dans une table. Lors de l'extraction de tels enregistrements, il est plus logique d'extraire uniquement les enregistrements uniques au lieu d'extraire les enregistrements en double.

## Syntaxe

Voici la syntaxe de base du mot-clé DISTINCT pour éliminer les enregistrements en double.

```sql
SELECT DISTINCT column1, column2,.....columnN 
FROM table_name
WHERE [condition]
```

## Exemple

Considérons une table de l'entreprise avec les enregistrements suivants.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
8           Paul        24          Houston     20000.0
9           James       44          Norway      5000.0
10          James       45          Texas       5000.0
```

Tout d'abord, voyons comment la requête SELECT suivante renvoie les enregistrements de salaire en double.

```sql
sqlite> SELECT name FROM COMPANY;
```

Cela donnera le résultat suivant.

```bash
NAME
----------
Paul
Allen
Teddy
Mark
David
Kim
James
Paul
James
James
```

Maintenant, utilisons le mot clé DISTINCT avec la requête SELECT ci-dessus et voyons le résultat.

```sql
sqlite> SELECT DISTINCT name FROM COMPANY;
```

Cela donnera le résultat suivant, où il n'y a pas de doublon.

```bash
NAME
----------
Paul
Allen
Teddy
Mark
David
Kim
James
```