La clause LIMIT de SQLite est utilisée pour limiter la quantité de données retournées par l'instruction SELECT.

## Syntaxe

Voici la syntaxe de base de l'instruction SELECT avec la clause LIMIT.

```sql
SELECT column1, column2, columnN 
FROM table_name
LIMIT [no of rows]
```

Voici la syntaxe de la clause LIMIT lorsqu'elle est utilisée avec la clause OFFSET.

```sql
SELECT column1, column2, columnN 
FROM table_name
LIMIT [no of rows] OFFSET [row num]
```

Le moteur SQLite retournera les lignes à partir de la ligne suivante jusqu'à l'OFFSET donné comme montré ci-dessous dans le dernier exemple.

## Exemple

Considérons une table de l'entreprise avec les enregistrements suivants -

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
```

Voici un exemple qui limite le nombre de lignes dans la table en fonction du nombre de lignes que vous voulez récupérer de la table.

```sql
sqlite> SELECT * FROM COMPANY LIMIT 6;
```

Cela donnera le résultat suivant.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
```

Cependant, dans certaines situations, vous pouvez avoir besoin de prélever un ensemble d'enregistrements à partir d'un décalage particulier. Voici un exemple qui récupère 3 enregistrements à partir de la 3ème position.

```sql
sqlite> SELECT * FROM COMPANY LIMIT 3 OFFSET 2;
```

Cela donnera le résultat suivant.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
```