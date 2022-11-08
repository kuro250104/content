## Introduction

Les contraintes sont les règles appliquées aux colonnes de données d'une table. Elles sont utilisées pour limiter le type de données qui peuvent entrer dans une table. Cela garantit l'exactitude et la fiabilité des données dans la base de données.

Les contraintes peuvent être appliquées au niveau de la colonne ou de la table. Les contraintes de niveau colonne ne s'appliquent qu'à une seule colonne, tandis que les contraintes de niveau table s'appliquent à l'ensemble de la table.

Voici les contraintes les plus courantes utilisées dans SQLite.

- **NOT NULL Constraint** − Assure qu'une colonne ne peut pas avoir une valeur NULL..
- **DEFAULT Constraint** − Fournit une valeur par défaut pour une colonne lorsqu'aucune valeur n'est spécifiée.
- **UNIQUE Constraint** − Permet de s'assurer que toutes les valeurs d'une colonne sont différentes.
- **PRIMARY Key** − Identifie de manière unique chaque ligne/enregistrement dans une table de base de données.
- **CHECK Constraint** − Garantit que toutes les valeurs d'une colonne satisfont à certaines conditions.

## NOT NULL Contrainte

Par défaut, une colonne peut contenir des valeurs **NULL**. Si vous ne voulez pas qu'une colonne ait une valeur - , vous devez définir une contrainte sur cette colonne en spécifiant que **NULL** n'est pas autorisé pour cette colonne.

Une valeur **NULL** n'est pas synonyme d'absence de données, elle représente plutôt des données inconnues.

### Exemple

Par exemple, l'instruction SQLite suivante crée une nouvelle table appelée COMPANY et ajoute cinq colonnes, dont trois, ID et NAME et AGE, spécifient de ne pas accepter les **NULL**.

```sql
CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

## DEFAUT Contrainte

La contrainte **DEFAULT** fournit une valeur par défaut à une colonne lorsque l'instruction **INSERT INTO** ne fournit pas de valeur spécifique.

### Exemple

Par exemple, l'instruction SQLite suivante crée une nouvelle table appelée COMPANY et ajoute cinq colonnes. Ici, la colonne SALARY est définie par défaut à 5000.00, donc au cas où l'instruction **INSERT INTO** ne fournit pas de valeur pour cette colonne, alors par défaut, cette colonne sera définie à 5000.00.

```sql
CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL    DEFAULT 50000.00
);
```

## Contrainte UNIQUE

La contrainte **UNIQUE** empêche deux enregistrements d'avoir des valeurs identiques dans une colonne particulière. Dans la table SOCIÉTÉ, par exemple, vous pourriez vouloir empêcher deux ou plusieurs personnes d'avoir un âge identique.

### Exemple

Par exemple, l'instruction SQLite suivante crée une nouvelle table appelée COMPANY et ajoute cinq colonnes. Ici, la colonne AGE est définie comme étant **UNIQUE**, de sorte que vous ne pouvez pas avoir deux enregistrements avec le même âge.

```sql
CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL UNIQUE,
    ADDRESS        CHAR(50),
    SALARY         REAL    DEFAULT 50000.00
);
```

## PRIMARY KEY Constraint

La contrainte **PRIMARY KEY** identifie de manière unique chaque enregistrement d'une table de base de données. Il peut y avoir plusieurs colonnes UNIQUE, mais une seule clé primaire dans une table. Les clés primaires sont importantes lors de la conception des tables de la base de données. Les clés primaires sont des identifiants uniques.

Nous les utilisons pour faire référence aux lignes de la table. Les clés primaires deviennent des clés étrangères dans d'autres tables, lors de la création de relations entre les tables. En raison d'un "oubli de codage de longue date", les clés primaires peuvent être NULL dans SQLite. Ce n'est pas le cas dans d'autres bases de données.

Une clé primaire est un champ dans une table qui identifie de manière unique chaque ligne/enregistrement dans une table de base de données. Les clés primaires doivent contenir des valeurs uniques. Une colonne de clé primaire ne peut pas avoir de valeurs NULL.

Une table ne peut avoir qu'une seule clé primaire, qui peut consister en un ou plusieurs champs. Lorsque plusieurs champs sont utilisés comme clé primaire, ils sont appelés **composite key**.

Si une table a une clé primaire définie sur un ou plusieurs champs, vous ne pouvez pas avoir deux enregistrements ayant la même valeur de ce ou ces champs.

### Exemple

Vous avez déjà vu plusieurs exemples ci-dessus où nous avons créé la table COMPANY avec l'ID comme clé primaire.

```sql
CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

## Contrainte CHECK

La contrainte **CHECK** permet à une condition de vérifier la valeur saisie dans un enregistrement. Si la condition est évaluée à faux, l'enregistrement viole la contrainte et n'est pas saisi dans la table.

### Exemple

Par exemple, le SQLite suivant crée une nouvelle table appelée COMPANY et ajoute cinq colonnes. Ici, nous ajoutons une colonne **CHECK** with SALARY, de sorte que vous ne pouvez pas avoir de SALARY zéro.

```sql
CREATE TABLE COMPANY3(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL    CHECK(SALARY > 0)
);
```

## Contrainte d'abandon

SQLite supporte un sous-ensemble limité de la commande **ALTER TABLE**. La commande **ALTER TABLE** de SQLite permet à l'utilisateur de renommer une table ou d'ajouter une nouvelle colonne à une table existante. Il n'est pas possible de renommer une colonne, de supprimer une colonne ou d'ajouter ou de supprimer des contraintes dans une table.