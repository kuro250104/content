La commande SQLite **ALTER TABLE** modifie une table existante sans effectuer un vidage complet et un rechargement des données. Vous pouvez renommer une table en utilisant l'instruction **ALTER TABLE** et des colonnes supplémentaires peuvent être ajoutées dans une table existante en utilisant l'instruction **ALTER TABLE**.

Aucune autre opération n'est prise en charge par la commande **ALTER TABLE** en SQLite, à l'exception du renommage d'une table et de l'ajout d'une colonne dans une table existante.

## Syntaxe

Voici la syntaxe de base de **ALTER TABLE** pour RENOMMER une table existante.

```sql
ALTER TABLE database_name.table_name RENAME TO new_table_name;
```

Voici la syntaxe de base de **ALTER TABLE** pour ajouter une nouvelle colonne dans une table existante.

```sql
ALTER TABLE database_name.table_name ADD COLUMN column_def...;
```

## Exemple

Considérons la table SOCIÉTÉ avec les enregistrements suivants -

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

Maintenant, essayons de renommer cette table en utilisant l'instruction ALTER TABLE comme suit -.

```sql
sqlite> ALTER TABLE COMPANY RENAME TO OLD_COMPANY;
```

L'instruction SQLite ci-dessus renommera la table COMPANY en OLD_COMPANY. Maintenant, essayons d'ajouter une nouvelle colonne dans la table OLD_COMPANY comme suit - 

```sql
sqlite> ALTER TABLE OLD_COMPANY ADD COLUMN SEX char(1);
```

La table COMPANY est maintenant modifiée et le résultat de l'instruction SELECT est le suivant.

```bash
ID          NAME        AGE         ADDRESS     SALARY      SEX
----------  ----------  ----------  ----------  ----------  ---
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
```

Il convient de noter que la colonne nouvellement ajoutée est remplie de valeurs NULL.