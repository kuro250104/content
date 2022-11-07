La clause **WHERE** de SQLite est utilisée pour spécifier une condition lors de la récupération des données d'une ou plusieurs tables.

Si la condition donnée est satisfaite, c'est-à-dire vraie, elle renvoie la valeur spécifique de la table. Vous devrez utiliser la clause WHERE pour filtrer les enregistrements et ne récupérer que les enregistrements nécessaires.

La clause **WHERE** n'est pas seulement utilisée dans l'instruction **SELECT**, mais aussi dans les instructions **UPDATE**, **DELETE**, etc., qui seront abordées dans les chapitres suivants.

## Syntaxe

Voici la syntaxe de base de l'instruction SQLite **SELECT** avec la clause **WHERE**.

```sql
SELECT column1, column2, columnN 
FROM table_name
WHERE [condition]
```

## Exemple

Vous pouvez spécifier une condition en utilisant des opérateurs logiques ou de comparaison tels que >, <, =, LIKE, NOT, etc. Considérons la table COMPANY avec les enregistrements suivants -

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

Voici un exemple simple de l'utilisation des opérateurs logiques de SQLite. L'instruction **SELECT** suivante liste tous les enregistrements pour lesquels AGE est supérieur ou égal à 25 ET le salaire est supérieur ou égal à 65000.00.

```bash
sqlite> SELECT * FROM COMPANY WHERE AGE >= 25 AND SALARY >= 65000;

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
```

L'instruction **SELECT** suivante répertorie tous les enregistrements pour lesquels AGE est supérieur ou égal à 25 OU le salaire est supérieur ou égal à 65000.00.

```sal
sqlite> SELECT * FROM COMPANY WHERE AGE >= 25 OR SALARY >= 65000;

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
```

L'instruction **SELECT** suivante répertorie tous les enregistrements où AGE n'est pas NULL, c'est-à-dire tous les enregistrements car aucun d'entre eux n'a un AGE égal à NULL.

```sql
sqlite>  SELECT * FROM COMPANY WHERE AGE IS NOT NULL;

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

L'instruction SELECT suivante liste tous les enregistrements dont le NOM commence par "Ki", peu importe ce qui vient après "Ki".

```sql
sqlite> SELECT * FROM COMPANY WHERE NAME LIKE 'Ki%';

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
6           Kim         22          South-Hall  45000.0
```

L'instruction **SELECT** suivante liste tous les enregistrements dont le NOM commence par "Ki", peu importe ce qui vient après "Ki".

```sql
sqlite> SELECT * FROM COMPANY WHERE NAME GLOB 'Ki*';

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
6           Kim         22          South-Hall  45000.0
```

L'instruction **SELECT** suivante répertorie tous les enregistrements pour lesquels la valeur AGE est soit 25, soit 27.

```sql
sqlite> SELECT * FROM COMPANY WHERE AGE IN ( 25, 27 );

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
2           Allen       25          Texas       15000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
```

L'instruction **SELECT** suivante liste tous les enregistrements pour lesquels la valeur AGE n'est ni 25 ni 27.

```sql
sqlite> SELECT * FROM COMPANY WHERE AGE NOT IN ( 25, 27 );

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
3           Teddy       23          Norway      20000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
```

L'instruction **SELECT** suivante répertorie tous les enregistrements dont la valeur AGE est comprise entre 25 et 27.

```sql
sqlite> SELECT * FROM COMPANY WHERE AGE BETWEEN 25 AND 27;

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
2           Allen       25          Texas       15000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
```

L'instruction **SELECT** suivante utilise une sous-requête SQL, où la sous-requête trouve tous les enregistrements dont le champ AGE a un SALAIRE > 65000, puis la clause **WHERE** est utilisée avec l'opérateur **EXISTS** pour répertorier tous les enregistrements où le champ AGE de la requête externe existe dans le résultat renvoyé par la sous-requête.

```sql
sqlite> SELECT AGE FROM COMPANY 
    WHERE EXISTS (SELECT AGE FROM COMPANY WHERE SALARY > 65000);

AGE
----------
32
25
23
25
27
22
24
```

L'instruction **SELECT** suivante utilise une sous-requête SQL dans laquelle la sous-requête trouve tous les enregistrements dont le champ AGE a un SALAIRE > 65000, puis la clause **WHERE** est utilisée avec l'opérateur > pour répertorier tous les enregistrements dont l'AGE de la requête externe est supérieur à l'âge dans le résultat renvoyé par la sous-requête.

```sql
sqlite> SELECT * FROM COMPANY 
    WHERE AGE > (SELECT AGE FROM COMPANY WHERE SALARY > 65000);

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
```