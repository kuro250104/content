## Introduction

Une expression est une combinaison d'une ou plusieurs valeurs, d'opérateurs et de fonctions SQL qui donnent une valeur.

Les expressions SQL sont comme des formules et elles sont écrites en langage de requête. Vous pouvez également les utiliser pour interroger la base de données à la recherche d'un ensemble spécifique de données.

## Syntaxe

Considérons la syntaxe de base de l'instruction SELECT comme suit -

```sql
SELECT column1, column2, columnN 
FROM table_name 
WHERE [CONDITION | EXPRESSION];
```

Voici les différents types d'expressions SQLite.

## SQLite - Boolean Expressions

Les expressions booléennes de SQLite récupèrent les données sur la base d'une valeur unique correspondante. Voici la syntaxe -

```sql
SELECT column1, column2, columnN 
FROM table_name 
WHERE SINGLE VALUE MATCHTING EXPRESSION;
```

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

Voici un exemple simple montrant l'utilisation des expressions booléennes de SQLite.

```sql
sqlite> SELECT * FROM COMPANY WHERE SALARY = 10000;

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
4           James        24          Houston   10000.0
```

## SQLite - Expression numérique

Ces expressions sont utilisées pour effectuer toute opération mathématique dans toute requête. Voici la syntaxe -

```sql
SELECT numerical_expression as OPERATION_NAME
[FROM table_name WHERE CONDITION] ;
```

Ici, numerical_expression est utilisé pour une expression mathématique ou toute formule. Voici un exemple simple montrant l'utilisation des expressions numériques de SQLite.

```sql
sqlite> SELECT (15 + 6) AS ADDITION
ADDITION = 21
```

Il existe plusieurs fonctions intégrées telles que avg(), sum(), count(), etc., pour effectuer ce que l'on appelle **aggregate data calculations** par rapport à une table ou à une colonne de table spécifique.

```sql
sqlite> SELECT COUNT(*) AS "RECORDS" FROM COMPANY; 
RECORDS = 7
```

## SQLite - Expressions de date

Les expressions de date renvoient les valeurs de date et d'heure actuelles du système. Ces expressions sont utilisées dans diverses manipulations de données.

```sql
sqlite> SELECT CURRENT_TIMESTAMP;
CURRENT_TIMESTAMP = 2013-03-17 10:43:35
```