## Introduction

L'instruction SQLite **CREATE TABLE** est utilisée pour créer une nouvelle table dans l'une des bases de données données données. La création d'une table de base implique de nommer la table et de définir ses colonnes et le type de données de chaque colonne.

## Syntaxe

Voici la syntaxe de base de l'instruction **CREATE TABLE**.

```sql
CREATE TABLE database_name.table_name(
   column1 datatype PRIMARY KEY(one or more columns),
   column2 datatype,
   column3 datatype,
   .....
   columnN datatype
);
```

**CREATE TABLE** est le mot clé qui indique au système de base de données de créer une nouvelle table. Le nom ou l'identifiant unique de la table suit l'instruction **CREATE TABLE**. En option, vous pouvez spécifier le database_name avec le table_name.

## Exemple

L'exemple suivant crée une table COMPANY dont la clé primaire est ID et les contraintes NOT NULL indiquent que ces champs ne peuvent pas être NULL lors de la création d'enregistrements dans cette table.

```sql
sqlite> CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

Créons un tableau supplémentaire, que nous utiliserons dans nos exercices des chapitres suivants.

```sql
sqlite> CREATE TABLE DEPARTMENT(
   ID INT PRIMARY KEY      NOT NULL,
   DEPT           CHAR(50) NOT NULL,
   EMP_ID         INT      NOT NULL
);
```

Vous pouvez vérifier si votre table a été créée avec succès en utilisant la commande SQLite ```.tables```, qui sera utilisée pour lister toutes les tables dans une base de données attachée.

```sql
sqlite>.tables
COMPANY     DEPARTMENT
```

Ici, vous pouvez voir la table COMPANY deux fois car elle montre la table COMPANY pour la base de données principale et la table test.COMPANY pour l'alias 'test' créé pour votre testDB.db. Vous pouvez obtenir des informations complètes sur une table en utilisant la commande SQLite ```.schema``` suivante.

```sql
sqlite>.schema COMPANY
CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```