## Introduction

L'opérateur GLOB de SQLite est utilisé pour faire correspondre uniquement des valeurs de texte à un modèle en utilisant des caractères génériques. Si l'expression recherchée peut correspondre à l'expression du motif, l'opérateur GLOB renvoie true, c'est-à-dire 1. Contrairement à l'opérateur LIKE, GLOB est sensible à la casse et suit la syntaxe d'UNIX pour spécifier les jokers suivants.

- Le signe astérisque (*)
- Le point d'interrogation ( ?)

Le signe astérisque (*) représente zéro ou plusieurs chiffres ou caractères. Le point d'interrogation ( ?) représente un seul chiffre ou caractère.

## Syntaxe

Voici la syntaxe de base de * et ?

```sql
SELECT FROM table_name
WHERE column GLOB 'XXXX*'
or 
SELECT FROM table_name
WHERE column GLOB '*XXXX*'
or
SELECT FROM table_name
WHERE column GLOB 'XXXX?'
or
SELECT FROM table_name
WHERE column GLOB '?XXXX'
or
SELECT FROM table_name
WHERE column GLOB '?XXXX?'
or
SELECT FROM table_name
WHERE column GLOB '????'
```

Vous pouvez combiner un nombre N de conditions en utilisant les opérateurs **AND** ou **OR**. Ici, XXXX peut être une valeur numérique ou une chaîne de caractères.

## Exemple

Le tableau suivant présente un certain nombre d'exemples de parties WHERE comportant différentes clauses LIKE avec les opérateurs '*' et ' ?

**Déclaration et description**

- ```WHERE SALARY GLOB '200*'``` - Trouve toutes les valeurs qui commencent par 200
- ```WHERE SALARY GLOB '*200*'``` - Trouve toutes les valeurs qui ont 200 dans n'importe quelle position.
- ```WHERE SALARY GLOB '?00*'``` - Trouve toutes les valeurs qui ont 00 en deuxième et troisième positions.
- ```WHERE SALARY GLOB '2??'``` - Trouve toutes les valeurs qui commencent par 2 et qui ont au moins 3 caractères de long.
- ```WHERE SALARY GLOB '*2'``` - Trouve toutes les valeurs qui se terminent par 2
- ```WHERE SALARY GLOB '?2*3'``` - Trouve toutes les valeurs qui ont un 2 en deuxième position et qui se terminent par un 3.
- ```WHERE SALARY GLOB '2???3'``` - Trouve toutes les valeurs d'un nombre à cinq chiffres qui commencent par 2 et finissent par 3.

Prenons un exemple réel, considérons une table de l'ENTREPRISE avec les enregistrements suivants -

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

Voici un exemple qui affichera tous les enregistrements de la table COMPANY, où AGE commence par 2.

```sql
sqlite> SELECT * FROM COMPANY WHERE AGE  GLOB '2*';
```

Cela donnera le résultat suivant.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
```

Voici un exemple qui affichera tous les enregistrements de la table SOCIÉTÉ où ADRESSE aura un trait d'union (-) dans le texte -.

```sql
sqlite> SELECT * FROM COMPANY WHERE ADDRESS  GLOB '*-*';
```

Cela donnera le résultat suivant.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
4           Mark        25          Rich-Mond   65000.0
6           Kim         22          South-Hall  45000.0
```