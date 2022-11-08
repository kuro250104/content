SQLite AUTOINCREMENT est un mot clé utilisé pour incrémenter automatiquement la valeur d'un champ dans une table. Nous pouvons auto incrémenter la valeur d'un champ en utilisant le mot clé AUTOINCREMENT lors de la création d'une table avec un nom de colonne spécifique à auto incrémenter.

Le mot clé AUTOINCREMENT ne peut être utilisé qu'avec le champ INTEGER.

## Syntaxe

L'utilisation de base du mot-clé AUTOINCREMENT est la suivante -.

```sql
CREATE TABLE table_name(
    column1 INTEGER AUTOINCREMENT,
    column2 datatype,
    column3 datatype,
    .....
    columnN datatype,
);
```

## Exemple

Considérons la table COMPANY à créer comme suit -

```sql
sqlite> CREATE TABLE COMPANY(
    ID INTEGER PRIMARY KEY AUTOINCREMENT,
    NAME           TEXT      NOT NULL,
    AGE            INT       NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

Maintenant, insérez les enregistrements suivants dans la table SOCIÉTÉ -

```sql
INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ( 'Paul', 32, 'California', 20000.00 );

INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ('Allen', 25, 'Texas', 15000.00 );

INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ('Teddy', 23, 'Norway', 20000.00 );

INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ( 'Mark', 25, 'Rich-Mond ', 65000.00 );

INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ( 'David', 27, 'Texas', 85000.00 );

INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ( 'Kim', 22, 'South-Hall', 45000.00 );

INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ( 'James', 24, 'Houston', 10000.00 );
```

Cela va insérer 7 tuples dans la table SOCIÉTÉ et SOCIÉTÉ aura les enregistrements suivants -

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