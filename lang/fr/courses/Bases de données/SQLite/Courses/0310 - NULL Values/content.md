SQLite **NULL** est le terme utilisé pour représenter une valeur manquante. Une valeur NULL dans une table est une valeur dans un champ qui semble être vide.

Un champ avec une valeur **NULL** est un champ sans valeur. Il est très important de comprendre qu'une valeur **NULL** est différente d'une valeur nulle ou d'un champ qui contient des espaces.

## Syntaxe

Voici la syntaxe de base de l'utilisation de **NULL** lors de la création d'une table.

```sql
SQLite> CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

Ici, **NOT NULL** signifie que la colonne doit toujours accepter une valeur explicite du type de données donné. Il y a deux colonnes pour lesquelles nous n'avons pas utilisé **NOT NULL**, ce qui signifie que ces colonnes pourraient être **NULL**.

Un champ avec une valeur NULL est un champ qui a été laissé vide lors de la création de l'enregistrement.

## Exemple

La valeur **NULL** peut poser des problèmes lors de la sélection des données, car lorsqu'on compare une valeur inconnue à une autre valeur, le résultat est toujours inconnu et n'est pas inclus dans les résultats finaux. Considérez le tableau suivant, L'ENTREPRISE avec les enregistrements suivants -

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

Utilisons l'instruction **UPDATE** pour définir quelques valeurs invalides comme étant **NULL** comme suit -

```sql
sqlite> UPDATE COMPANY SET ADDRESS = NULL, SALARY = NULL where ID IN(6,7);
```

Maintenant, la table SOCIÉTÉ aura les enregistrements suivants.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22
7           James       24
```

Ensuite, voyons l'utilisation de l'opérateur **IS NOT NULL** pour répertorier tous les enregistrements où SALARY n'est pas **NULL**.

```sql
sqlite> SELECT  ID, NAME, AGE, ADDRESS, SALARY
    FROM COMPANY
    WHERE SALARY IS NOT NULL;
```

L'instruction SQLite ci-dessus produira le résultat suivant -

```sql
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
```

Voici l'utilisation de l'opérateur **IS NULL**, qui permet de répertorier tous les enregistrements où SALARY est **NULL**.

```sql
sqlite> SELECT  ID, NAME, AGE, ADDRESS, SALARY
    FROM COMPANY
    WHERE SALARY IS NULL;
```

L'instruction SQLite ci-dessus produira le résultat suivant.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
6           Kim         22
7           James       24
```