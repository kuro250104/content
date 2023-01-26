Une sous-requête ou une requête interne ou une requête imbriquée est une requête à l'intérieur d'une autre requête PostgreSQL et incorporée dans la clause WHERE.

Une sous-requête est utilisée pour renvoyer des données qui seront utilisées dans la requête principale comme condition pour restreindre davantage les données à récupérer.

Les sous-requêtes peuvent être utilisées avec les instructions SELECT, INSERT, UPDATE et DELETE, ainsi qu'avec des opérateurs tels que =, <, >, >=, <=, IN, etc.

Il y a quelques règles que les sous-requêtes doivent respecter : 

- Les instructions SELECT, INSERT, UPDATE et DELETE.
- Les sous-requêtes doivent être placées entre parenthèses.
- Une sous-requête ne peut comporter qu'une seule colonne dans la clause SELECT, sauf si plusieurs colonnes sont présentes dans la requête principale pour que la sous-requête puisse comparer les colonnes sélectionnées.
- Un ORDER BY ne peut pas être utilisé dans une sous-requête, bien que la requête principale puisse utiliser un ORDER BY. Le GROUP BY peut être utilisé pour exécuter la même fonction que le ORDER BY dans une sous-requête.
- Les sous-requêtes qui renvoient plus d'une ligne ne peuvent être utilisées qu'avec des opérateurs de valeurs multiples, tels que l'opérateur IN, EXISTS, NOT IN, ANY/SOME, ALL.
- L'opérateur BETWEEN ne peut pas être utilisé avec une sous-requête ; cependant, BETWEEN peut être utilisé dans la sous-requête.

## Sous-requêtes avec l'instruction SELECT

Les sous-requêtes sont le plus souvent utilisées avec l'instruction SELECT. La syntaxe de base est la suivante :

```sql
SELECT column_name [, column_name ]
FROM   table1 [, table2 ]
WHERE  column_name OPERATOR
    (SELECT column_name [, column_name ]
    FROM table1 [, table2 ]
    [WHERE])
```

## Example

Considérons la table SOCIÉTÉ comportant les enregistrements suivants :

```bash
id | name  | age | address   | salary
----+-------+-----+-----------+--------
  1 | Paul  |  32 | California|  20000
  2 | Allen |  25 | Texas     |  15000
  3 | Teddy |  23 | Norway    |  20000
  4 | Mark  |  25 | Rich-Mond |  65000
  5 | David |  27 | Texas     |  85000
  6 | Kim   |  22 | South-Hall|  45000
  7 | James |  24 | Houston   |  10000
(7 rows)
```

Maintenant, vérifions la sous-requête suivante avec l'instruction SELECT :

```sql
testdb=# SELECT *
    FROM COMPANY
    WHERE ID IN (SELECT ID
    FROM COMPANY
    WHERE SALARY > 45000) ;
```

Cela donnerait le résultat suivant :

```bash
id | name  | age |  address    | salary
----+-------+-----+-------------+--------
  4 | Mark  |  25 | Rich-Mond   |  65000
  5 | David |  27 | Texas       |  85000
(2 rows)
```

## Sous-requêtes avec l'instruction INSERT

Les sous-requêtes peuvent également être utilisées avec les instructions INSERT. L'instruction INSERT utilise les données renvoyées par la sous-requête pour les insérer dans une autre table. Les données sélectionnées dans la sous-requête peuvent être modifiées à l'aide de n'importe quelle fonction de caractère, de date ou de nombre.

La syntaxe de base est la suivante :

```sql
INSERT INTO table_name [ (column1 [, column2 ]) ]
    SELECT [ *|column1 [, column2 ] ]
    FROM table1 [, table2 ]
    [ WHERE VALUE OPERATOR ]
```

### Example

Considérons une table COMPANY_BKP, dont la structure est similaire à celle de la table COMPANY et qui peut être créée à l'aide de la même procédure CREATE TABLE en utilisant COMPANY_BKP comme nom de table. Maintenant, pour copier la table COMPANY complète dans COMPANY_BKP, la syntaxe est la suivante :

```sql
testdb=# INSERT INTO COMPANY_BKP
    SELECT * FROM COMPANY
    WHERE ID IN (SELECT ID
        FROM COMPANY) ;
```

## Sous-requêtes avec l'instruction UPDATE

La sous-requête peut être utilisée conjointement avec l'instruction UPDATE. Une ou plusieurs colonnes d'une table peuvent être mises à jour lorsqu'une sous-requête est utilisée avec l'instruction UPDATE.

La syntaxe de base est la suivante :

```sql
UPDATE table
SET column_name = new_value
[ WHERE OPERATOR [ VALUE ]
    (SELECT COLUMN_NAME
    FROM TABLE_NAME)
    [ WHERE) ]
```

### Example

Supposons que nous disposions de la table COMPANY_BKP, qui est une sauvegarde de la table COMPANY.

L'exemple suivant met à jour le SALAIRE de 0,50 fois dans la table SOCIÉTÉ pour tous les clients dont l'âge est supérieur ou égal à 27 ans :

```sql
testdb=# UPDATE COMPANY
    SET SALARY = SALARY * 0.50
    WHERE AGE IN (SELECT AGE FROM COMPANY_BKP
        WHERE AGE >= 27 );
```

Cela affecterait deux lignes et finalement la table SOCIÉTÉ aurait les enregistrements suivants :

```bash
id | name  | age | address     | salary
----+-------+-----+-------------+--------
  2 | Allen |  25 | Texas       |  15000
  3 | Teddy |  23 | Norway      |  20000
  4 | Mark  |  25 | Rich-Mond   |  65000
  6 | Kim   |  22 | South-Hall  |  45000
  7 | James |  24 | Houston     |  10000
  1 | Paul  |  32 | California  |  10000
  5 | David |  27 | Texas       |  42500
(7 rows)
```

## Sous-requêtes avec l'instruction DELETE

La sous-requête peut être utilisée en conjonction avec l'instruction DELETE comme avec toutes les autres instructions mentionnées ci-dessus.

La syntaxe de base est la suivante :

```sql
DELETE FROM TABLE_NAME
[ WHERE OPERATOR [ VALUE ]
    (SELECT COLUMN_NAME
    FROM TABLE_NAME)
    [ WHERE) ]
```

### Exemple

En supposant que nous disposions de la table COMPANY_BKP, qui est une sauvegarde de la table COMPANY.

L'exemple suivant supprime les enregistrements de la table SOCIÉTÉ pour tous les clients dont l'âge est supérieur ou égal à 27 ans :

```sql
testdb=# DELETE FROM COMPANY
    WHERE AGE IN (SELECT AGE FROM COMPANY_BKP
        WHERE AGE > 27 );
```

Cela affecterait deux lignes et finalement la table SOCIÉTÉ aurait les enregistrements suivants :

```bash
id | name  | age | address     | salary
----+-------+-----+-------------+--------
  2 | Allen |  25 | Texas       |  15000
  3 | Teddy |  23 | Norway      |  20000
  4 | Mark  |  25 | Rich-Mond   |  65000
  6 | Kim   |  22 | South-Hall  |  45000
  7 | James |  24 | Houston     |  10000
  5 | David |  27 | Texas       |  42500
(6 rows)
```
