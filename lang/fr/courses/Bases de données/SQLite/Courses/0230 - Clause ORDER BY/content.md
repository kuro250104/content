La clause ORDER BY de SQLite est utilisée pour trier les données dans un ordre croissant ou décroissant, sur la base d'une ou plusieurs colonnes.

## Syntaxe

Voici la syntaxe de base de la clause **ORDER BY**.

```sql
SELECT column-list 
FROM table_name 
[WHERE condition] 
[ORDER BY column1, column2, .. columnN] [ASC | DESC];
```

Vous pouvez utiliser plus d'une colonne dans la clause ORDER BY. Assurez-vous que la colonne que vous utilisez pour trier doit être disponible dans la liste de colonnes.

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
```

L'exemple suivant permet de trier le résultat par ordre décroissant de SALAIRE.

```sql
sqlite> SELECT * FROM COMPANY ORDER BY SALARY ASC;
```

Cela donnera le résultat suivant.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
7           James       24          Houston     10000.0
2           Allen       25          Texas       15000.0
1           Paul        32          California  20000.0
3           Teddy       23          Norway      20000.0
6           Kim         22          South-Hall  45000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
```

Voici un exemple qui permettra de trier le résultat dans l'ordre décroissant par NOM et SALAIRE.

```sql
sqlite> SELECT * FROM COMPANY ORDER BY NAME, SALARY ASC;
```

Cela donnera le résultat suivant.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
2           Allen       25          Texas       15000.0
5           David       27          Texas       85000.0
7           James       24          Houston     10000.0
6           Kim         22          South-Hall  45000.0
4           Mark        25          Rich-Mond   65000.0
1           Paul        32          California  20000.0
3           Teddy       23          Norway      20000.0
```

Voici un exemple qui permettra de trier le résultat dans l'ordre décroissant du NOM.

```sql
sqlite> SELECT * FROM COMPANY ORDER BY NAME DESC;
```

Cela donnera le résultat suivant.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
3           Teddy       23          Norway      20000.0
1           Paul        32          California  20000.0
4           Mark        25          Rich-Mond   65000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
5           David       27          Texas       85000.0
2           Allen       25          Texas       15000.0
```