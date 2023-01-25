Les vues sont des pseudo-tables. C'est-à-dire qu'elles ne sont pas de véritables tableaux ; elles apparaissent néanmoins comme des tableaux ordinaires à SELECT. Une vue peut représenter un sous-ensemble d'une table réelle, en sélectionnant certaines colonnes ou certaines lignes d'une table ordinaire. Une vue peut même représenter des tables jointes. Étant donné que des autorisations distinctes sont attribuées aux vues, vous pouvez les utiliser pour restreindre l'accès aux tables afin que les utilisateurs ne voient que des lignes ou des colonnes spécifiques d'une table.

Une vue peut contenir toutes les lignes d'une table ou des lignes sélectionnées dans une ou plusieurs tables. Une vue peut être créée à partir d'une ou plusieurs tables, ce qui dépend de la requête PostgreSQL écrite pour créer une vue.

Les vues, qui sont des sortes de tables virtuelles, permettent aux utilisateurs de faire ce qui suit :

- Structurer les données d'une manière que les utilisateurs ou les catégories d'utilisateurs trouvent naturelle ou intuitive.
- Restreindre l'accès aux données de sorte qu'un utilisateur ne puisse voir que des données limitées au lieu du tableau complet.
- Résumer les données de divers tableaux, qui peuvent être utilisés pour générer des rapports.

Comme les vues ne sont pas des tables ordinaires, il se peut que vous ne puissiez pas exécuter une instruction DELETE, INSERT ou UPDATE sur une vue. Cependant, vous pouvez créer une RULE pour corriger ce problème d'utilisation de DELETE, INSERT ou UPDATE sur une vue.

## Creating Views

Les vues PostgreSQL sont créées à l'aide de l'instruction **CREATE VIEW**. Les vues PostgreSQL peuvent être créées à partir d'une table unique, de plusieurs tables ou d'une autre vue.

La syntaxe de base de **CREATE VIEW** est la suivante :

```sql
CREATE [TEMP | TEMPORARY] VIEW view_name AS
SELECT column1, column2.....
FROM table_name
WHERE [condition];
```

Vous pouvez inclure plusieurs tables dans votre instruction SELECT de la même manière que vous les utilisez dans une requête SELECT PostgreSQL normale. Si le mot clé optionnel TEMP ou TEMPORARY est présent, la vue sera créée dans l'espace temporaire. Les vues temporaires sont automatiquement abandonnées à la fin de la session en cours.

## Exemple

Considérons que la table SOCIÉTÉ comporte les enregistrements suivants :

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

Voici maintenant un exemple de création d'une vue à partir de la table SOCIÉTÉ. Cette vue sera utilisée pour n'avoir que quelques colonnes de la table SOCIÉTÉ.

```sql
testdb=# CREATE VIEW COMPANY_VIEW AS
SELECT ID, NAME, AGE
FROM  COMPANY;
```

Maintenant, vous pouvez interroger COMPANY_VIEW de la même manière que vous interrogez une table réelle. Voici l'exemple suivant :

```sql
testdb=# SELECT * FROM COMPANY_VIEW;
```

Cela donnerait le résultat suivant :

```bash
id | name  | age
----+-------+-----
  1 | Paul  |  32
  2 | Allen |  25
  3 | Teddy |  23
  4 | Mark  |  25
  5 | David |  27
  6 | Kim   |  22
  7 | James |  24
(7 rows)
```

## Dropping Views

Pour supprimer une vue, il suffit d'utiliser l'instruction **DROP VIEW** avec le nom de la vue. La syntaxe de base de l'instruction **DROP VIEW** est la suivante : 

```sql
testdb=# DROP VIEW view_name;
```

La commande suivante va supprimer la vue COMPANY_VIEW, que nous avons créée dans la dernière section :

```sql
testdb=# DROP VIEW COMPANY_VIEW;
```
