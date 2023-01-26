Les **triggers** PostgreSQL sont des fonctions de rappel de base de données, qui sont automatiquement exécutées/invoquées lorsqu'un événement de base de données spécifié se produit.

Les points suivants sont importants pour les déclencheurs PostgreSQL.

- Un déclencheur PostgreSQL peut être spécifié pour déclencher :
    - Avant que l'opération ne soit tentée sur une ligne (avant que les contraintes ne soient vérifiées et que l'opération INSERT, UPDATE ou DELETE ne soit tentée).
    - Après la fin de l'opération (après la vérification des contraintes et la fin de l'opération INSERT, UPDATE ou DELETE).
    - Au lieu de l'opération (dans le cas d'insertions, de mises à jour ou de suppressions sur une vue).
- Un déclencheur marqué FOR EACH ROW est appelé une fois pour chaque ligne que l'opération modifie. En revanche, un déclencheur marqué FOR EACH STATEMENT ne s'exécute qu'une fois pour une opération donnée, quel que soit le nombre de lignes qu'elle modifie.
- La clause WHEN et les actions du déclencheur peuvent accéder aux éléments de la ligne insérée, supprimée ou mise à jour en utilisant des références de la forme NEW.column-name et OLD.column-name, où column-name est le nom d'une colonne de la table à laquelle le déclencheur est associé.
- Si une clause **WHEN** est fournie, les instructions PostgreSQL spécifiées ne sont exécutées que pour les lignes pour lesquelles la clause WHEN est vraie. Si aucune clause WHEN n'est fournie, les instructions PostgreSQL sont exécutées pour toutes les lignes.
- Si plusieurs déclencheurs du même type sont définis pour le même événement, ils seront déclenchés dans l'ordre alphabétique de leur nom.
- Le mot clé **BEFORE**, **AFTER** ou **INSTEAD OF** détermine quand les actions du déclencheur seront exécutées par rapport à l'insertion, la modification ou la suppression de la ligne associée.
- Les déclencheurs sont automatiquement abandonnés lorsque la table à laquelle ils sont associés est abandonnée.
- La table à modifier doit exister dans la même base de données que la table ou la vue à laquelle le déclencheur est attaché et on doit utiliser juste ```tablename```, pas ```database.tablename```.
- L'option **CONSTRAINT**, lorsqu'elle est spécifiée, crée un déclencheur de contrainte. C'est la même chose qu'un déclencheur normal, sauf que le moment où le déclencheur se déclenche peut être ajusté en utilisant **SET CONSTRAINTS**. Les déclencheurs de contraintes sont censés lever une exception lorsque les contraintes qu'ils mettent en œuvre sont violées.

## Syntaxe

La syntaxe de base de la création d'un déclencheur est la suivante :

```sql
CREATE  TRIGGER trigger_name [BEFORE|AFTER|INSTEAD OF] event_name
ON table_name
[
    -- Trigger logic goes here....
];
```

Ici, **event_name** peut être une opération de base de données **INSERT**, **DELETE**, **UPDATE**, et **TRUNCATE** sur la table mentionnée ```table_name```. Vous pouvez éventuellement préciser **FOR EACH ROW** après le nom de la table.

Voici la syntaxe de la création d'un déclencheur sur une opération UPDATE sur une ou plusieurs colonnes spécifiées d'une table comme suit :

```sql
CREATE  TRIGGER trigger_name [BEFORE|AFTER] UPDATE OF column_name
ON table_name
[
    -- Trigger logic goes here....
];
```

## Exemple

Considérons un cas où nous voulons conserver un procès d'audit pour chaque enregistrement inséré dans la table COMPANY, que nous allons créer comme suit (laissez tomber la table COMPANY si vous l'avez déjà) :

```sql
testdb=# CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

Pour conserver le procès d'audit, nous allons créer une nouvelle table appelée AUDIT où les messages de journal seront insérés chaque fois qu'il y a une entrée dans la table COMPANY pour un nouvel enregistrement :

```sql
testdb=# CREATE TABLE AUDIT(
    EMP_ID INT NOT NULL,
    ENTRY_DATE TEXT NOT NULL
);
```

Ici, ID est l'ID de l'enregistrement ```AUDIT```, et ```EMP_ID``` est l'```ID```, qui viendra de la table COMPANY, et DATE gardera l'horodatage quand l'enregistrement sera créé dans la table COMPANY. Donc maintenant, créons un déclencheur sur la table COMPANY comme suit :

```sql
testdb=# CREATE TRIGGER example_trigger AFTER INSERT ON COMPANY
FOR EACH ROW EXECUTE PROCEDURE auditlogfunc();
```

Où ```auditlogfunc()``` est une procédure PostgreSQL et a la définition suivante :

```sql
CREATE OR REPLACE FUNCTION auditlogfunc() RETURNS TRIGGER AS $example_table$
    BEGIN
        INSERT INTO AUDIT(EMP_ID, ENTRY_DATE) VALUES (new.ID, current_timestamp);
        RETURN NEW;
    END;
$example_table$ LANGUAGE plpgsql;
```

Maintenant, nous allons commencer le travail réel. Commençons par insérer un enregistrement dans la table SOCIÉTÉ, ce qui devrait entraîner la création d'un enregistrement d'audit dans la table AUDIT. Créons donc un enregistrement dans la table SOCIÉTÉ, comme suit :

```sql
testdb=# INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (1, 'Paul', 32, 'California', 20000.00 );
```

Cela créera un enregistrement dans la table SOCIÉTÉ, qui est la suivante :

```bash
id | name | age | address      | salary
----+------+-----+--------------+--------
  1 | Paul |  32 | California   |  20000
```

En même temps, un enregistrement sera créé dans la table **AUDIT**. Cet enregistrement est le résultat d'un déclencheur, que nous avons créé sur l'opération **INSERT** de la table COMPANY. De même, vous pouvez créer vos propres déclencheurs sur les opérations **UPDATE** et **DELETE** en fonction de vos besoins.

```bash
emp_id |          entry_date
--------+-------------------------------
    1  | 2013-05-05 15:49:59.968+05:30
(1 row)
```

## Listing TRIGGERS

Vous pouvez dresser la liste de tous les déclencheurs de la base de données actuelle à partir de la table ```pg_trigger```, comme suit :

```sql
testdb=# SELECT * FROM pg_trigger;
```

L'instruction PostgreSQL ci-dessus énumérera tous les triggers.

Si vous voulez lister les triggers d'une table particulière, alors utilisez la clause AND avec le nom de la table comme suit :

```sql
testdb=# SELECT tgname FROM pg_trigger, pg_class WHERE tgrelid=pg_class.oid AND relname='company';
```

La déclaration PostgreSQL ci-dessus ne donnera également qu'une seule entrée, comme suit :

```bash
    tgname
-----------------
 example_trigger
(1 row)
```

## Dropping TRIGGERS

Voici la commande **DROP**, qui peut être utilisée pour supprimer un déclencheur existant :

```sql
testdb=# DROP TRIGGER trigger_name;
```
