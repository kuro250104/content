Les **Triggers** SQLite sont des fonctions de rappel de la base de données, qui sont automatiquement exécutées/invoquées lorsqu'un événement spécifique de la base de données se produit. Voici les points importants concernant les déclencheurs SQLite.

- Un déclencheur SQLite peut être spécifié pour se déclencher chaque fois qu'un DELETE, INSERT ou UPDATE d'une table de base de données particulière se produit ou chaque fois qu'un UPDATE se produit sur une ou plusieurs colonnes spécifiées d'une table.
- Pour l'instant, SQLite ne supporte que les déclencheurs FOR EACH ROW, pas les déclencheurs FOR EACH STATEMENT. Par conséquent, spécifier explicitement FOR EACH ROW est facultatif.
- La clause WHEN et les actions du déclencheur peuvent accéder aux éléments de la ligne insérée, supprimée ou mise à jour en utilisant des références de la forme NEW.column-name et OLD.column-name, où column-name est le nom d'une colonne de la table à laquelle le déclencheur est associé.
- Si une clause WHEN est fournie, les instructions SQL spécifiées ne sont exécutées que pour les lignes pour lesquelles la clause WHEN est vraie. Si aucune clause WHEN n'est fournie, les instructions SQL sont exécutées pour toutes les lignes.
- Le mot clé BEFORE ou AFTER détermine quand les actions du déclencheur seront exécutées par rapport à l'insertion, la modification ou la suppression de la ligne associée.
- Les déclencheurs sont automatiquement abandonnés lorsque la table à laquelle ils sont associés est abandonnée.
- La table à modifier doit exister dans la même base de données que la table ou la vue à laquelle le déclencheur est attaché et on doit utiliser juste tablename et non database.tablename.
- Une fonction SQL spéciale RAISE() peut être utilisée dans un programme de déclenchement pour lever une exception.

## Syntaxe

Voici la syntaxe de base pour créer un trigger.

```sql
CREATE TRIGGER trigger_name [BEFORE|AFTER] event_name 
ON table_name
BEGIN
    -- Trigger logic goes here....
END;
```

Ici, event_name peut être une opération de base de données INSERT, DELETE et UPDATE sur la table mentionnée table_name. Vous pouvez éventuellement préciser FOR EACH ROW après le nom de la table.

Voici la syntaxe pour créer un déclencheur sur une opération UPDATE sur une ou plusieurs colonnes spécifiées d'une table.

```sql
CREATE TRIGGER trigger_name [BEFORE|AFTER] UPDATE OF column_name 
ON table_name
BEGIN
    -- Trigger logic goes here....
END;
```

## Exemple

Considérons un cas où nous voulons conserver un procès d'audit pour chaque enregistrement inséré dans la table COMPANY, que nous créons comme suit (laissez tomber la table COMPANY si vous l'avez déjà).

```sql
sqlite> CREATE TABLE COMPANY(
    ID INT PRIMARY KEY     NOT NULL,
    NAME           TEXT    NOT NULL,
    AGE            INT     NOT NULL,
    ADDRESS        CHAR(50),
    SALARY         REAL
);
```

Pour conserver le procès d'audit, nous allons créer une nouvelle table appelée AUDIT où les messages de journal seront insérés, chaque fois qu'il y a une entrée dans la table COMPANY pour un nouvel enregistrement.

```sql
sqlite> CREATE TABLE AUDIT(
    EMP_ID INT NOT NULL,
    ENTRY_DATE TEXT NOT NULL
);
```

Ici, ID est l'ID de l'enregistrement AUDIT, et EMP_ID est l'ID qui proviendra de la table COMPANY et DATE gardera l'horodatage quand l'enregistrement sera créé dans la table COMPANY. Maintenant, nous allons créer un déclencheur sur la table COMPANY comme suit -

```sql
sqlite> CREATE TRIGGER audit_log AFTER INSERT 
ON COMPANY
BEGIN
    INSERT INTO AUDIT(EMP_ID, ENTRY_DATE) VALUES (new.ID, datetime('now'));
END;
```

Maintenant, nous allons commencer le travail réel. Commençons par insérer un enregistrement dans la table COMPANY, ce qui devrait entraîner la création d'un enregistrement d'audit dans la table AUDIT. Créez un enregistrement dans la table SOCIÉTÉ comme suit

```sql
sqlite> INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (1, 'Paul', 32, 'California', 20000.00 );
```

Cela créera un enregistrement dans la table SOCIÉTÉ, qui est la suivante -

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
```

En même temps, un enregistrement sera créé dans la table AUDIT. Cet enregistrement est le résultat d'un déclencheur, que nous avons créé sur l'opération INSERT dans la table COMPANY. De même, vous pouvez créer vos propres déclencheurs sur les opérations UPDATE et DELETE en fonction de vos besoins.

```bash
EMP_ID      ENTRY_DATE
----------  -------------------
1           2013-04-05 06:26:00
```

## Listing Triggers

Vous pouvez énumérer tous les déclencheurs à partir de la table sqlite_master comme suit -

```sql
sqlite> SELECT name FROM sqlite_master
WHERE type = 'trigger';
```

L'instruction SQLite ci-dessus n'énumérera qu'une seule entrée, comme suit -

```bash
name
----------
audit_log
```

Si vous voulez répertorier les déclencheurs sur une table particulière, utilisez la clause AND avec le nom de la table comme suit -

```sql
sqlite> SELECT name FROM sqlite_master
WHERE type = 'trigger' AND tbl_name = 'COMPANY';
```

L'instruction SQLite ci-dessus ne répertorie également qu'une seule entrée, comme suit -

```bash
name
----------
audit_log
```

## Dropping Triggers

Voici la commande DROP, qui peut être utilisée pour abandonner un déclencheur existant.

```sql
sqlite> DROP TRIGGER trigger_name;
```