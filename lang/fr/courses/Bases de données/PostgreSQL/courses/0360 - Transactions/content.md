Une transaction est une unité de travail qui est exécutée dans une base de données. Les transactions sont des unités ou des séquences de travail accomplies dans un ordre logique, que ce soit de manière manuelle par un utilisateur ou automatiquement par un programme de base de données.

Une transaction est la propagation d'une ou plusieurs modifications à la base de données. Par exemple, si vous créez un enregistrement, mettez à jour un enregistrement ou supprimez un enregistrement de la table, vous effectuez une transaction sur la table. Il est important de contrôler les transactions afin de garantir l'intégrité des données et de gérer les erreurs de base de données.

En pratique, vous regroupez plusieurs requêtes PostgreSQL et vous les exécutez toutes ensemble dans le cadre d'une transaction.

## Properties of Transactions

Les transactions possèdent les quatre propriétés standards suivantes, généralement désignées par l'acronyme ACID :

- **Atomicity** − S'assure que toutes les opérations de l'unité de travail se terminent avec succès ; sinon, la transaction est interrompue au point d'échec et les opérations précédentes sont ramenées à leur état antérieur.
- **Consistency** − Assure que la base de données change correctement d'état lors d'une transaction validée avec succès.
- **Isolation** − Permet aux transactions de fonctionner indépendamment les unes des autres et de manière transparente.
- **Durability** − Garantit que le résultat ou l'effet d'une transaction engagée persiste en cas de défaillance du système.

## Transaction Control

Les commandes suivantes sont utilisées pour contrôler les transactions.

- **BEGIN TRANSACTION** - Pour démarrer une transaction.
- **COMMIT** - Pour sauvegarder les modifications, vous pouvez également utiliser la commande **END TRANSACTION**.
- **ROLLBACK** - Pour annuler les modifications.

Transactional control commands are only used with the DML commands INSERT, UPDATE and DELETE only. They cannot be used while creating tables or dropping them because these operations are automatically committed in the database.

## The BEGIN TRANSACTION Command

Les transactions peuvent être lancées à l'aide de la commande **BEGIN TRANSACTION** ou simplement **BEGIN**. Ces transactions persistent généralement jusqu'à ce que la prochaine commande **COMMIT** ou **ROLLBACK** soit rencontrée. Cependant, une transaction peut également faire l'objet d'un **ROLLBACK** si la base de données est fermée ou si une erreur se produit.

Voici une syntaxe simple pour lancer une transaction :

```sql
BEGIN;

or

BEGIN TRANSACTION;
```

## The COMMIT Command

La commande **COMMIT** est la commande transactionnelle utilisée pour enregistrer les modifications invoquées par une transaction dans la base de données.

La commande **COMMIT** enregistre toutes les transactions dans la base de données depuis la dernière commande **COMMIT** ou **ROLLBACK**.

La syntaxe de la commande **COMMIT** est la suivante :

```sql
COMMIT;

or

END TRANSACTION;
```

## The ROLLBACK Command

La commande **ROLLBACK** est la commande transactionnelle utilisée pour annuler les transactions qui n'ont pas encore été enregistrées dans la base de données.

La commande **ROLLBACK** ne peut être utilisée que pour annuler les transactions effectuées depuis la dernière commande **COMMIT** ou **ROLLBACK**.

La syntaxe de la commande **ROLLBACK** est la suivante :

```sql
ROLLBACK;
```

## Exemple

Considérons que la table SOCIÉTÉ possède les enregistrements suivants :

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
```

Maintenant, commençons une transaction et supprimons les enregistrements de la table ayant ```age = 25``` et finalement nous utilisons la commande **ROLLBACK** pour annuler tous les changements.

```sql
testdb=# BEGIN;
DELETE FROM COMPANY WHERE AGE = 25;
ROLLBACK;
```

Si vous vérifiez la table COMPANY, vous trouverez toujours les enregistrements suivants :

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
```

Maintenant, commençons une autre transaction et supprimons les enregistrements de la table ayant ```age = 25``` et finalement nous utilisons la commande **COMMIT** pour valider tous les changements.

```sql
testdb=# BEGIN;
DELETE FROM COMPANY WHERE AGE = 25;
COMMIT;
```

Si vous vérifiez la table SOCIÉTÉ, elle contient toujours les enregistrements suivants :

```bash
id | name  | age | address    | salary
----+-------+-----+------------+--------
  1 | Paul  |  32 | California |  20000
  3 | Teddy |  23 | Norway     |  20000
  5 | David |  27 | Texas      |  85000
  6 | Kim   |  22 | South-Hall |  45000
  7 | James |  24 | Houston    |  10000
(5 rows)
```
