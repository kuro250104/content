Une transaction est une unité de travail qui est exécutée dans une base de données. Les transactions sont des unités ou des séquences de travail accomplies dans un ordre logique, que ce soit de manière manuelle par un utilisateur ou automatiquement par un programme de base de données.

Une transaction est la propagation d'une ou plusieurs modifications à la base de données. Par exemple, si vous créez, mettez à jour ou supprimez un enregistrement de la table, vous effectuez une transaction sur la table. Il est important de contrôler les transactions afin de garantir l'intégrité des données et de gérer les erreurs de base de données.

En pratique, vous regroupez plusieurs requêtes SQLite et vous les exécutez toutes ensemble dans le cadre d'une transaction..

## Properties of Transactions

Les transactions possèdent les quatre propriétés standard suivantes, généralement désignées par l'acronyme ACID.

- **Atomicity** − S'assure que toutes les opérations de l'unité de travail se terminent avec succès ; sinon, la transaction est interrompue au point d'échec et les opérations précédentes sont ramenées à leur état antérieur.
- **Consistency** − Assure que la base de données change correctement d'état lors d'une transaction validée avec succès.
- **Isolation** − Permet aux transactions de fonctionner indépendamment les unes des autres et de manière transparente.
- **Durability** − Garantit que le résultat ou l'effet d'une transaction engagée persiste en cas de défaillance du système.

## Transaction Control

Les commandes suivantes sont utilisées pour contrôler les transactions :

- **BEGIN TRANSACTION** − Pour commencer une transaction.
- **COMMIT** − Pour sauvegarder les changements, vous pouvez également utiliser la commande END TRANSACTION.
- **ROLLBACK** − Pour annuler les changements.

Les commandes de contrôle transactionnel sont uniquement utilisées avec les commandes DML INSERT, UPDATE et DELETE. Elles ne peuvent pas être utilisées lors de la création de tables ou de leur suppression car ces opérations sont automatiquement validées dans la base de données.

## BEGIN TRANSACTION Command

Les transactions peuvent être lancées à l'aide de la commande BEGIN TRANSACTION ou simplement BEGIN. Ces transactions persistent généralement jusqu'à ce que la prochaine commande COMMIT ou ROLLBACK soit rencontrée. Toutefois, une transaction peut également se retourner si la base de données est fermée ou si une erreur se produit. Voici la syntaxe simple pour lancer une transaction.

```sql
BEGIN;
or 
BEGIN TRANSACTION;
```

## COMMIT Command

La commande COMMIT est la commande transactionnelle utilisée pour sauvegarder les modifications invoquées par une transaction dans la base de données.

La commande COMMIT enregistre toutes les transactions dans la base de données depuis la dernière commande COMMIT ou ROLLBACK.

La syntaxe de la commande COMMIT est la suivante.

```sql
COMMIT;
or
END TRANSACTION;
```

## ROLLBACK Command

La commande **ROLLBACK** est la commande transactionnelle utilisée pour annuler les transactions qui n'ont pas encore été enregistrées dans la base de données.

La commande **ROLLBACK** ne peut être utilisée que pour annuler les transactions effectuées depuis la dernière commande COMMIT ou **ROLLBACK**.

Voici la syntaxe de la commande **ROLLBACK**.

```sql
ROLLBACK;
```

Exemple

Considérons une table de l'entreprise avec les enregistrements suivants.

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

Maintenant, démarrons une transaction et supprimons les enregistrements de la table ayant age = 25. Ensuite, utilisez la commande ROLLBACK pour annuler tous les changements.

```sql
sqlite> BEGIN;
sqlite> DELETE FROM COMPANY WHERE AGE = 25;
sqlite> ROLLBACK;
```

Maintenant, si vous vérifiez la table COMPANY, elle a toujours les enregistrements suivants -

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

Commençons une autre transaction et supprimons les enregistrements de la table ayant age = 25 et finalement nous utilisons la commande COMMIT pour valider tous les changements.

```sql
sqlite> BEGIN;
sqlite> DELETE FROM COMPANY WHERE AGE = 25;
sqlite> COMMIT;
```

Si vous vérifiez maintenant la table COMPANY, elle contient toujours les enregistrements suivants -

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
3           Teddy       23          Norway      20000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
```