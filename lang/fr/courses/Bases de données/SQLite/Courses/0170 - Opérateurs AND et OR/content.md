Les opérateurs SQLite AND & OR sont utilisés pour compiler plusieurs conditions afin de réduire les données sélectionnées dans une déclaration SQLite. Ces deux opérateurs sont appelés opérateurs conjonctifs.

Ces opérateurs permettent d'effectuer des comparaisons multiples avec différents opérateurs dans la même instruction SQLite.

## L'opérateur AND

L'opérateur AND permet l'existence de plusieurs conditions dans la clause WHERE d'une instruction SQLite. En utilisant l'opérateur AND, la condition complète sera considérée comme vraie lorsque toutes les conditions sont vraies. Par exemple, [condition1] AND [condition2] ne sera vraie que si la condition1 et la condition2 sont toutes deux vraies.

### Syntaxe

Voici la syntaxe de base de l'opérateur AND avec la clause WHERE.

```sql
SELECT column1, column2, columnN 
FROM table_name
WHERE [condition1] AND [condition2]...AND [conditionN];
```

Vous pouvez combiner un nombre **N** de conditions en utilisant l'opérateur **AND**. Pour qu'une action soit prise par l'instruction SQLite, qu'il s'agisse d'une transaction ou d'une requête, toutes les conditions séparées par le **AND** doivent être VRAIES.

### Exemple

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

L'instruction **SELECT** suivante répertorie tous les enregistrements pour lesquels AGE est supérieur ou égal à 25 **AND** le salaire est supérieur ou égal à 65000.00.

```sql
sqlite> SELECT * FROM COMPANY WHERE AGE >= 25 AND SALARY >= 65000;

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
```

## L'opérateur OR

L'opérateur **OR** est également utilisé pour combiner plusieurs conditions dans la clause WHERE d'une instruction SQLite. En utilisant l'opérateur OR, la condition complète sera considérée comme vraie si au moins l'une des conditions est vraie. Par exemple, ```[condition1] OR [condition2]``` sera vraie si la condition1 ou la condition2 est vraie.

### Syntaxe

Voici la syntaxe de base de l'opérateur **OR** avec la clause **WHERE**.

```sql
SELECT column1, column2, columnN 
FROM table_name
WHERE [condition1] OR [condition2]...OR [conditionN]
```

Vous pouvez combiner un nombre **N** de conditions en utilisant l'opérateur OR. Pour qu'une action soit entreprise par la déclaration SQLite, qu'il s'agisse d'une transaction ou d'une requête, UNE seule des conditions séparées par l'opérateur OR doit être VRAIE.

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

L'instruction SELECT suivante répertorie tous les enregistrements pour lesquels AGE est supérieur ou égal à 25 **OR** le salaire est supérieur ou égal à 65000.00.

```sql
sqlite> SELECT * FROM COMPANY WHERE AGE >= 25 OR SALARY >= 65000;

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
```
