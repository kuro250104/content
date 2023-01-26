Le NULL de PostgreSQL est le terme utilisé pour représenter une valeur manquante. Une valeur NULL dans une table est une valeur dans un champ qui semble être vide.

Un champ avec une valeur NULL est un champ sans valeur. Il est très important de comprendre qu'une valeur NULL est différente d'une valeur nulle ou d'un champ qui contient des espaces.

## Syntaxe

La syntaxe de base de l'utilisation de NULL lors de la création d'une table est la suivante :

```sql
CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

Ici, **NOT NULL** signifie que la colonne doit toujours accepter une valeur explicite du type de données donné. Il y a deux colonnes où nous n'avons pas utilisé **NOT NULL**. Cela signifie donc que ces colonnes peuvent être **NULL**.

Un champ avec une valeur **NULL** est un champ qui a été laissé vide lors de la création de l'enregistrement.

## Exemple

La valeur **NULL** peut poser des problèmes lors de la sélection des données, car lorsqu'on compare une valeur inconnue à une autre valeur, le résultat est toujours inconnu et n'est pas inclus dans les résultats finaux. Considérons le tableau suivant, la SOCIÉTÉ ayant les enregistrements suivants :

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

Utilisons l'instruction **UPDATE** pour définir quelques valeurs invalides comme étant **NULL** comme suit :

```sql
testdb=# UPDATE COMPANY SET ADDRESS = NULL, SALARY = NULL where ID IN(6,7);
```

Maintenant, la table COMPANY devrait avoir les enregistrements suivants :

```bash
id | name  | age | address     | salary
----+-------+-----+-------------+--------
  1 | Paul  |  32 | California  |  20000
  2 | Allen |  25 | Texas       |  15000
  3 | Teddy |  23 | Norway      |  20000
  4 | Mark  |  25 | Rich-Mond   |  65000
  5 | David |  27 | Texas       |  85000
  6 | Kim   |  22 |             |
  7 | James |  24 |             |
(7 rows)
```

Ensuite, voyons l'utilisation de l'opérateur **IS NOT NULL** pour lister tous les enregistrements où SALARY n'est pas **NULL** :

```sql
testdb=#  SELECT  ID, NAME, AGE, ADDRESS, SALARY
    FROM COMPANY
    WHERE SALARY IS NOT NULL;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
id | name  | age | address    | salary
----+-------+-----+------------+--------
  1 | Paul  |  32 | California |  20000
  2 | Allen |  25 | Texas      |  15000
  3 | Teddy |  23 | Norway     |  20000
  4 | Mark  |  25 | Rich-Mond  |  65000
  5 | David |  27 | Texas      |  85000
(5 rows)
```

Voici l'utilisation de l'opérateur **IS NULL** qui permet de répertorier tous les enregistrements pour lesquels SALARY est **NULL** :

```sql
testdb=#  SELECT  ID, NAME, AGE, ADDRESS, SALARY
        FROM COMPANY
        WHERE SALARY IS NULL;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
id | name  | age | address | salary
----+-------+-----+---------+--------
  6 | Kim   |  22 |         |
  7 | James |  24 |         |
(2 rows)
```
