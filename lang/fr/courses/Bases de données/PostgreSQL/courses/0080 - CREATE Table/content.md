L'instruction PostgreSQL **CREATE TABLE** est utilisée pour créer une nouvelle table dans l'une des bases de données.

## Syntaxe

La syntaxe de base de l'instruction **CREATE TABLE** est la suivante :

```sql
CREATE TABLE table_name(
    column1 datatype,
    column2 datatype,
    column3 datatype,
    .....
    columnN datatype,
    PRIMARY KEY( one or more columns )
);
```

**CREATE TABLE** est un mot-clé qui indique au système de base de données de créer une nouvelle table. Le nom ou l'identifiant unique de la table suit l'instruction **CREATE TABLE**. Initialement, la table vide dans la base de données actuelle appartient à l'utilisateur qui émet la commande.

Ensuite, entre parenthèses, vient la liste, qui définit chaque colonne de la table et le type de données qu'elle contient. La syntaxe deviendra plus claire avec l'exemple ci-dessous.

## Exemples

L'exemple suivant crée une table COMPANY avec ID comme clé primaire et NOT NULL comme contraintes, indiquant que ces champs ne peuvent pas être NULL lors de la création d'enregistrements dans cette table :

```sql
CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

Créons un tableau supplémentaire, que nous utiliserons dans nos exercices dans les chapitres suivants :

```sql
CREATE TABLE DEPARTMENT(
    ID INT PRIMARY KEY      NOT NULL,
    DEPT           CHAR(50) NOT NULL,
    EMP_ID         INT      NOT NULL
);
```

Vous pouvez vérifier si votre table a été créée avec succès en utilisant la commande ```\d```, qui sera utilisée pour répertorier toutes les tables dans une base de données attachée.

```bash
testdb-# \d
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```bash
          List of relations
 Schema |    Name    | Type  |  Owner
--------+------------+-------+----------
 public | company    | table | postgres
 public | department | table | postgres
(2 rows)
```

Utilisez ```\d tablename``` pour décrire chaque table comme indiqué ci-dessous :

```bash
testdb-# \d company
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant : - 1.

```bash
       Table "public.company"
  Column   |     Type      | Modifiers
-----------+---------------+-----------
 id        | integer       | not null
 name      | text          | not null
 age       | integer       | not null
 address   | character(50) |
 salary    | real          |
 join_date | date          |
Indexes:
    "company_pkey" PRIMARY KEY, btree (id)
```
