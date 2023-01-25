PostgreSQL dispose des types de données smallserial, serial et bigserial ; ce ne sont pas de véritables types, mais simplement une commodité de notation pour créer des colonnes d'identifiants uniques. Ils sont similaires à la propriété AUTO_INCREMENT supportée par certaines autres bases de données.

Si vous souhaitez qu'une colonne serial ait une contrainte unique ou soit une clé primaire, elle doit maintenant être spécifiée, comme tout autre type de données.

Le nom de type serial crée une colonne de type integer. Le nom de type bigserial crée une colonne bigint. bigserial doit être utilisé si vous prévoyez l'utilisation de plus de 231 identifiants pendant la durée de vie de la table. Le nom de type smallserial crée une colonne smallint.

## Syntaxe

L'utilisation de base de SERIAL dataype est la suivante :

```sql
CREATE TABLE tablename (
    colname SERIAL
);
```

## Exemple

Considérons que la table SOCIÉTÉ doit être créée de la manière suivante :

```sql
testdb=# CREATE TABLE COMPANY(
    ID  SERIAL PRIMARY KEY,
    NAME           TEXT      NOT NULL,
    AGE            INT       NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

Maintenant, insérez les enregistrements suivants dans la table SOCIÉTÉ :

```sql
INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ('Paul', 32, 'California', 20000.00);

INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ('Allen', 25, 'Texas', 15000.00);

INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ('Teddy', 23, 'Norway', 20000.00);

INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ('Mark', 25, 'Rich-Mond ', 65000.00);

INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ('David', 27, 'Texas', 85000.00);


INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ('Kim', 22, 'South-Hall', 45000.00);

INSERT INTO COMPANY (NAME,AGE,ADDRESS,SALARY)
VALUES ('James', 24, 'Houston', 10000.00);
```

Ceci va insérer sept tuples dans la table COMPANY et COMPANY aura les enregistrements suivants :

```bash
id | name  | age | address    | salary
----+-------+-----+------------+--------
  1 | Paul  |  32 | California |  20000
  2 | Allen |  25 | Texas      |  15000
  3 | Teddy |  23 | Norway     |  20000
  4 | Mark  |  25 | Rich-Mond  |  65000
  5 | David |  27 | Texas      |  85000
  6 | Kim   |  22 | South-Hall |  45000
  7 | James |  24 | Houston    |  10000
```
