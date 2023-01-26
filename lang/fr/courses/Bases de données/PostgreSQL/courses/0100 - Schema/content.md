Un schéma est une collection de tables nommées. Un schéma peut également contenir des vues, des index, des séquences, des types de données, des opérateurs et des fonctions. Les schémas sont analogues aux répertoires au niveau du système d'exploitation, sauf que les schémas ne peuvent pas être imbriqués. L'instruction PostgreSQL **CREATE SCHEMA** crée un schéma.

## Syntaxe

La syntaxe de base de CREATE SCHEMA est la suivante :

```sql
CREATE SCHEMA name;
```

Où **name** est le nom du schéma.

## Syntax to Create Table in Schema

La syntaxe de base pour créer une table dans un schéma est la suivante :

```sql
CREATE TABLE myschema.mytable (
...
);
```

## Exemple

Voyons un exemple de création d'un schéma. Connectez-vous à la base de données ```testdb``` et créez un schéma myschema comme suit :

```bash
testdb=# create schema myschema;
CREATE SCHEMA
```

Le message "CREATE SCHEMA" signifie que le schéma a été créé avec succès.

Maintenant, créons une table dans le schéma ci-dessus, comme suit :

```sql
testdb=# create table myschema.company(
    ID   INT              NOT NULL,
    NAME VARCHAR (20)     NOT NULL,
    AGE  INT              NOT NULL,
    ADDRESS  CHAR (25),
    SALARY   DECIMAL (18, 2),
    PRIMARY KEY (ID)
);
```

Cela va créer une table vide. Vous pouvez vérifier la table créée avec la commande donnée ci-dessous :

```bash
testdb=# select * from myschema.company;
```

Cela donnerait le résultat suivant :

```bash
id | name | age | address | salary
----+------+-----+---------+--------
(0 rows)
```

## Syntaxe de Drop Schema

Pour abandonner un schéma s'il est vide (tous les objets qu'il contient ont été abandonnés), utilisez la commande :

```sql
DROP SCHEMA myschema;
```

Pour supprimer un schéma, y compris tous les objets qu'il contient, utilisez la commande :

```sql
DROP SCHEMA myschema CASCADE;
```

## Avantages de l'utilisation d'un schéma

- Il permet à de nombreux utilisateurs d'utiliser une base de données sans interférer les uns avec les autres.
- Il organise les objets de la base de données en groupes logiques pour les rendre plus faciles à gérer.
- Les applications tierces peuvent être placées dans des schémas distincts afin qu'elles n'entrent pas en conflit avec les noms d'autres objets.
