## Introduction

L'instruction SQLite **INSERT INTO** est utilisée pour ajouter de nouvelles lignes de données dans une table de la base de données.

## Syntaxe

Voici les deux syntaxes de base de l'instruction **INSERT INTO**.

```sql
INSERT INTO TABLE_NAME [(column1, column2, column3,...columnN)]  
VALUES (value1, value2, value3,...valueN);
```

Ici, colonne1, colonne2,...colonneN sont les noms des colonnes de la table dans laquelle vous voulez insérer des données.

Il se peut que vous n'ayez pas besoin de spécifier le nom de la ou des colonnes dans la requête SQLite si vous ajoutez des valeurs pour toutes les colonnes de la table. Toutefois, assurez-vous que l'ordre des valeurs est le même que celui des colonnes de la table. La syntaxe de la requête SQLite INSERT INTO serait la suivante -

```sql
INSERT INTO TABLE_NAME VALUES (value1,value2,value3,...valueN);
```

## Exemple

Considérez que vous avez déjà créé la table COMPANY dans votre testDB.db comme suit -

```sql
sqlite> CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

Maintenant, les instructions suivantes créeraient six enregistrements dans la table COMPANY.

```sql
INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (1, 'Paul', 32, 'California', 20000.00 );

INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (2, 'Allen', 25, 'Texas', 15000.00 );

INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (3, 'Teddy', 23, 'Norway', 20000.00 );

INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (4, 'Mark', 25, 'Rich-Mond ', 65000.00 );

INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (5, 'David', 27, 'Texas', 85000.00 );

INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (6, 'Kim', 22, 'South-Hall', 45000.00 );
```

Vous pouvez créer un enregistrement dans la table SOCIÉTÉ en utilisant la deuxième syntaxe comme suit -

```sql
INSERT INTO COMPANY VALUES (7, 'James', 24, 'Houston', 10000.00 );
```

Toutes les instructions ci-dessus créent les enregistrements suivants dans la table COMPANY. Dans le chapitre suivant, vous apprendrez comment afficher tous ces enregistrements à partir d'une table.

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

## Remplir un tableau à l'aide d'un autre tableau

Vous pouvez introduire des données dans une table par le biais d'une instruction select sur une autre table, à condition que cette dernière possède un ensemble de champs qui sont nécessaires pour remplir la première table. Voici la syntaxe

```sql
INSERT INTO first_table_name [(column1, column2, ... columnN)] 
    SELECT column1, column2, ...columnN 
    FROM second_table_name
    [WHERE condition];
```

Pour l'instant, vous pouvez ignorer l'instruction ci-dessus. Tout d'abord, apprenons les clauses SELECT et WHERE qui seront abordées dans les chapitres suivants.