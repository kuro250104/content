Les contraintes sont les règles appliquées aux colonnes de données d'une table. Elles sont utilisées pour éviter que des données non valides soient saisies dans la base de données. Cela garantit l'exactitude et la fiabilité des données dans la base de données.

Les contraintes peuvent être appliquées au niveau de la colonne ou de la table. Les contraintes de niveau colonne ne s'appliquent qu'à une seule colonne, tandis que les contraintes de niveau table s'appliquent à l'ensemble de la table. La définition d'un type de données pour une colonne est une contrainte en soi. Par exemple, une colonne de type DATE contraint la colonne à des dates valides.

Les contraintes suivantes sont couramment utilisées dans PostgreSQL.

- **NOT NULL Constraint** − Assure qu'une colonne ne peut pas avoir de valeur NULL.
- **UNIQUE Constraint** − Permet de s'assurer que toutes les valeurs d'une colonne sont différentes.
- **PRIMARY Key** − Identifie de manière unique chaque ligne/enregistrement dans une table de base de données.
- **FOREIGN Key** − Constraint les données en fonction des colonnes d'autres tables.
- **CHECK Constraint** − La contrainte **CHECK** garantit que toutes les valeurs d'une colonne remplissent certaines conditions.
- **EXCLUSION Constraint** − La contrainte **EXCLUDE** garantit que si deux lignes quelconques sont comparées sur la ou les colonnes ou expressions spécifiées à l'aide du ou des opérateurs spécifiés, toutes ces comparaisons ne retourneront pas VRAI.

## NOT NULL Constraint

Par défaut, une colonne peut contenir des valeurs NULL. Si vous ne voulez pas qu'une colonne ait une valeur NULL, vous devez alors définir une telle contrainte sur cette colonne en spécifiant que NULL n'est désormais pas autorisé pour cette colonne. Une contrainte NOT NULL est toujours écrite comme une contrainte de colonne.

Une valeur NULL n'est pas synonyme d'absence de données ; elle représente plutôt des données inconnues.

### Exemple

Par exemple, l'instruction PostgreSQL suivante crée une nouvelle table appelée COMPANY1 et ajoute cinq colonnes, dont trois, ID et NAME et AGE, spécifient qu'elles n'acceptent pas les valeurs NULL :

```sql
CREATE TABLE COMPANY1(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

## UNIQUE Constraint

La contrainte **UNIQUE** empêche deux enregistrements d'avoir des valeurs identiques dans une colonne particulière. Dans la table SOCIÉTÉ, par exemple, vous pourriez vouloir empêcher deux personnes ou plus d'avoir un âge identique.

### Exemple

Par exemple, l'instruction PostgreSQL suivante crée une nouvelle table appelée COMPANY3 et ajoute cinq colonnes. Ici, la colonne AGE est définie comme UNIQUE, de sorte que vous ne pouvez pas avoir deux enregistrements avec le même âge :

```sql
CREATE TABLE COMPANY3(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL UNIQUE,
    ADDRESS        CHAR(50),
    SALARY         REAL    DEFAULT 50000.00
);
```

## PRIMARY KEY Constraint

La contrainte **PRIMARY KEY** identifie de manière unique chaque enregistrement d'une table de base de données. Il peut y avoir plusieurs colonnes **UNIQUE**, mais une seule clé primaire dans une table. Les clés primaires sont importantes lors de la conception des tables de la base de données. Les clés primaires sont des identifiants uniques.

Nous les utilisons pour faire référence aux lignes de la table. Les clés primaires deviennent des clés étrangères dans d'autres tables, lors de la création de relations entre les tables. En raison d'un "oubli de codage de longue date", les clés primaires peuvent être NULL dans SQLite. Ce n'est pas le cas dans d'autres bases de données

Une clé primaire est un champ dans une table, qui identifie de manière unique chaque ligne/enregistrement dans une table de base de données. Les clés primaires doivent contenir des valeurs uniques. Une colonne de clé primaire ne peut pas avoir de valeurs NULL.

Une table ne peut avoir qu'une seule clé primaire, qui peut consister en un ou plusieurs champs. Lorsque plusieurs champs sont utilisés comme clé primaire, ils sont appelés clé composite.

Si une table a une clé primaire définie sur un ou plusieurs champs, vous ne pouvez pas avoir deux enregistrements ayant la même valeur de ce ou ces champs.

## Exemple

Vous avez déjà vu plusieurs exemples ci-dessus où nous avons créé la table COMAPNY4 avec ID comme clé primaire :

```sql
CREATE TABLE COMPANY4(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

## FOREIGN KEY Constraint

Une contrainte de clé étrangère spécifie que les valeurs d'une colonne (ou d'un groupe de colonnes) doivent correspondre aux valeurs apparaissant dans une ligne d'une autre table. On dit que cela maintient l'intégrité référentielle entre deux tables liées. On les appelle clés étrangères parce que les contraintes sont étrangères, c'est-à-dire extérieures à la table. Les clés étrangères sont parfois appelées clés de référencement.

### Exemple

Par exemple, l'instruction PostgreSQL suivante crée une nouvelle table appelée COMPANY5 et ajoute cinq colonnes :

```sql
CREATE TABLE COMPANY6(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

Par exemple, l'instruction PostgreSQL suivante crée une nouvelle table appelée DEPARTMENT1, qui ajoute trois colonnes. La colonne EMP_ID est la clé étrangère et fait référence au champ ID de la table COMPANY6 :

```sql
CREATE TABLE DEPARTMENT1(
    ID INT PRIMARY KEY      NOT NULL,
    DEPT           CHAR(50) NOT NULL,
    EMP_ID         INT      references COMPANY6(ID)
);
```

## CHECK Constraint

La contrainte **CHECK** permet à une condition de vérifier la valeur saisie dans un enregistrement. Si la condition est fausse, l'enregistrement viole la contrainte et n'est pas saisi dans la table.

### Exemple

Par exemple, l'instruction PostgreSQL suivante crée une nouvelle table appelée COMPANY5 et ajoute cinq colonnes. Ici, nous ajoutons un **CHECK** avec la colonne SALARY, de sorte que vous ne pouvez pas avoir de SALARY comme Zéro :

```sql
CREATE TABLE COMPANY5(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL    CHECK(SALARY > 0)
);
```

## EXCLUSION Constraint

Les contraintes d'exclusion garantissent que si deux lignes quelconques sont comparées sur les colonnes ou les expressions spécifiées à l'aide des opérateurs spécifiés, au moins une de ces comparaisons d'opérateurs retournera faux ou null.

### Exemple

Par exemple, l'instruction PostgreSQL suivante crée une nouvelle table appelée COMPANY7 et ajoute cinq colonnes. Ici, nous ajoutons une contrainte **EXCLUDE** :

```sql
CREATE TABLE COMPANY7(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT,
    AGE            INT  ,
    ADDRESS        CHAR(50),
    SALARY         REAL,
    EXCLUDE USING gist
    (NAME WITH =,
    AGE WITH <>)
);
```

Ici, USING gist est le type d'index à construire et à utiliser pour l'application.

Vous devez exécuter la commande **CREATE EXTENSION** btree_gist, une fois par base de données. Cela installera l'extension btree_gist, qui définit les contraintes d'exclusion sur les types de données scalaires simples.

Comme nous avons imposé que l'âge soit le même, voyons cela en insérant des enregistrements dans le tableau :

```sql
INSERT INTO COMPANY7 VALUES(1, 'Paul', 32, 'California', 20000.00 );
INSERT INTO COMPANY7 VALUES(2, 'Paul', 32, 'Texas', 20000.00 );
INSERT INTO COMPANY7 VALUES(3, 'Paul', 42, 'California', 20000.00 );
```

Pour les deux premières instructions **INSERT**, les enregistrements sont ajoutés à la table COMPANY7. Pour la troisième instruction **INSERT**, l'erreur suivante apparaît :

```bash
ERROR:  conflicting key value violates exclusion constraint "company7_name_age_excl"
DETAIL:  Key (name, age)=(Paul, 42) conflicts with existing key (name, age)=(Paul, 32).
```

## Dropping Constraints

Pour supprimer une contrainte, vous devez connaître son nom. Si le nom est connu, il est facile de la supprimer. Sinon, vous devez trouver le nom généré par le système. La commande psql \d table name peut être utile ici. La syntaxe générale est :

```sql
ALTER TABLE table_name DROP CONSTRAINT some_name;
```
