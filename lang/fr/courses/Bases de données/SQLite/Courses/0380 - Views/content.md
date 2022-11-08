Une vue n'est rien d'autre qu'une instruction SQLite qui est stockée dans la base de données avec un nom associé. Il s'agit en fait d'une composition d'une table sous la forme d'une requête SQLite prédéfinie.

Une vue peut contenir toutes les lignes d'une table ou des lignes sélectionnées dans une ou plusieurs tables. Une vue peut être créée à partir d'une ou plusieurs tables, ce qui dépend de la requête SQLite écrite pour créer une vue.

Les vues, qui sont des sortes de tables virtuelles, permettent aux utilisateurs de -

- Structurer les données d'une manière que les utilisateurs ou les catégories d'utilisateurs trouvent naturelle ou intuitive.
- Restreindre l'accès aux données de sorte qu'un utilisateur ne puisse voir que des données limitées au lieu d'un tableau complet.
- Résumer les données de divers tableaux, qui peuvent être utilisés pour générer des rapports.

Les vues SQLite sont en lecture seule et donc vous ne pouvez pas exécuter une instruction DELETE, INSERT ou UPDATE sur une vue. Cependant, vous pouvez créer un déclencheur sur une vue qui se déclenche lors d'une tentative de DELETE, INSERT, ou UPDATE d'une vue et faire ce dont vous avez besoin dans le corps du déclencheur.

## Creating Views

Les vues SQLite sont créées à l'aide de l'instruction CREATE VIEW. Les vues SQLite peuvent être créées à partir d'une seule table, de plusieurs tables ou d'une autre vue.

Voici la syntaxe de base de CREATE VIEW.

```sql
CREATE [TEMP | TEMPORARY] VIEW view_name AS
SELECT column1, column2.....
FROM table_name
WHERE [condition];
```

Vous pouvez inclure plusieurs tables dans votre instruction SELECT de la même manière que vous les utilisez dans une requête SELECT SQL normale. Si le mot-clé facultatif TEMP ou TEMPORARY est présent, la vue sera créée dans la base de données temporaire.

### Exemple

Considérons une table de l'entreprise avec les enregistrements suivants -

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

Voici un exemple de création d'une vue à partir de la table COMPANY. Cette vue sera utilisée pour avoir seulement quelques colonnes de la table COMPANY.

```sql
sqlite> CREATE VIEW COMPANY_VIEW AS
SELECT ID, NAME, AGE
FROM  COMPANY;
```

Vous pouvez maintenant interroger COMPANY_VIEW de la même manière que vous interrogez une table réelle. Voici un exemple -

```sql
sqlite> SELECT * FROM COMPANY_VIEW;
```

Cela donnera le résultat suivant.

```bash
ID          NAME        AGE
----------  ----------  ----------
1           Paul        32
2           Allen       25
3           Teddy       23
4           Mark        25
5           David       27
6           Kim         22
7           James       24
```

## Dropping Views

Pour supprimer une vue, il suffit d'utiliser l'instruction **DROP VIEW** avec le view_name. La syntaxe de base de l'instruction **DROP VIEW** est la suivante - 

```sql
sqlite> DROP VIEW view_name;
```

La commande suivante va supprimer la vue COMPANY_VIEW, que nous avons créée dans la dernière section.

```sql
sqlite> DROP VIEW COMPANY_VIEW;
```