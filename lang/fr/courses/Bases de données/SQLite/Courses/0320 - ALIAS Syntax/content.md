Vous pouvez renommer une table ou une colonne temporairement en donnant un autre nom, qui est connu sous le nom d'**ALIAS**. L'utilisation d'alias de table permet de renommer une table dans une instruction SQLite particulière. Le renommage est un changement temporaire et le nom réel de la table ne change pas dans la base de données.

Les alias de colonne sont utilisés pour renommer les colonnes d'une table dans le but d'une requête SQLite particulière.

## Syntaxe

Voici la syntaxe de base d'un alias de table.

```sql
SELECT column1, column2....
FROM table_name AS alias_name
WHERE [condition];
```

Voici la syntaxe de base d'un alias de colonne.

```sql
SELECT column_name AS alias_name
FROM table_name
WHERE [condition];
```

## Example

Considérons les deux tableaux suivants : (a) Le tableau de la SOCIÉTÉ est le suivant : -.

```sql
sqlite> select * from COMPANY;
ID          NAME                  AGE         ADDRESS     SALARY
----------  --------------------  ----------  ----------  ----------
1           Paul                  32          California  20000.0
2           Allen                 25          Texas       15000.0
3           Teddy                 23          Norway      20000.0
4           Mark                  25          Rich-Mond   65000.0
5           David                 27          Texas       85000.0
6           Kim                   22          South-Hall  45000.0
7           James                 24          Houston     10000.0
```

(b) Une autre table est DEPARTMENT comme suit -

```bash
ID          DEPT                  EMP_ID
----------  --------------------  ----------
1           IT Billing            1
2           Engineering           2
3           Finance               7
4           Engineering           3
5           Finance               4
6           Engineering           5
7           Finance               6
```

Maintenant, voici l'utilisation de **TABLE ALIAS** où nous utilisons C et D comme alias pour les tables COMPANY et DEPARTMENT respectivement -.

```sql
sqlite> SELECT C.ID, C.NAME, C.AGE, D.DEPT
    FROM COMPANY AS C, DEPARTMENT AS D
    WHERE  C.ID = D.EMP_ID;
```

L'instruction SQLite ci-dessus produira le résultat suivant -

```bash
ID          NAME        AGE         DEPT
----------  ----------  ----------  ----------
1           Paul        32          IT Billing
2           Allen       25          Engineering
3           Teddy       23          Engineering
4           Mark        25          Finance
5           David       27          Engineering
6           Kim         22          Finance
7           James       24          Finance
```

Prenons un exemple de l'utilisation de **COLUMN ALIAS** où COMPANY_ID est un alias de la colonne ID et COMPANY_NAME est un alias de la colonne name.

```sql
sqlite> SELECT C.ID AS COMPANY_ID, C.NAME AS COMPANY_NAME, C.AGE, D.DEPT
    FROM COMPANY AS C, DEPARTMENT AS D
    WHERE  C.ID = D.EMP_ID;
```

L'instruction SQLite ci-dessus produira le résultat suivant -

```bash
COMPANY_ID  COMPANY_NAME  AGE         DEPT
----------  ------------  ----------  ----------
1           Paul          32          IT Billing
2           Allen         25          Engineering
3           Teddy         23          Engineering
4           Mark          25          Finance
5           David         27          Engineering
6           Kim           22          Finance
7           James         24          Finance
```