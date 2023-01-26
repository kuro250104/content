Les verrous ou verrous exclusifs ou verrous d'écriture empêchent les utilisateurs de modifier une ligne ou une table entière. Les lignes modifiées par UPDATE et DELETE sont alors verrouillées de manière exclusive et automatique pour la durée de la transaction. Cela empêche les autres utilisateurs de modifier la ligne jusqu'à ce que la transaction soit validée ou annulée.

Le seul moment où les utilisateurs doivent attendre les autres utilisateurs est lorsqu'ils essaient de modifier la même ligne. S'ils modifient des lignes différentes, aucune attente n'est nécessaire. Les requêtes SELECT ne doivent jamais attendre.

La base de données effectue le verrouillage automatiquement. Dans certains cas, cependant, le verrouillage doit être contrôlé manuellement. Le verrouillage manuel peut être effectué à l'aide de la commande LOCK. Elle permet de spécifier le type et la portée du verrouillage d'une transaction.

## Syntaxe pour LOCK command

La syntaxe de base pour la commande LOCK est la suivante :

- **name** − Le nom (éventuellement qualifié de schéma) d'une table existante à verrouiller. Si ONLY est spécifié avant le nom de la table, seule cette table est verrouillée. Si ONLY n'est pas spécifié, la table et toutes ses tables descendantes (le cas échéant) sont verrouillées.
- **lock_mode** − Le mode de verrouillage indique avec quels verrous ce verrouillage entre en conflit. Si aucun mode de verrouillage n'est spécifié, le mode le plus restrictif, ACCESS EXCLUSIVE, est utilisé. Les valeurs possibles sont : ACCESS SHARE, ROW SHARE, ROW EXCLUSIVE, SHARE UPDATE EXCLUSIVE, SHARE, SHARE ROW EXCLUSIVE, EXCLUSIVE, ACCESS EXCLUSIVE.

Une fois obtenu, le verrou est maintenu pour le reste de la transaction en cours. Il n'existe pas de commande UNLOCK TABLE ; les verrous sont toujours libérés à la fin de la transaction.

## DeadLocks

Les blocages peuvent se produire lorsque deux transactions attendent que l'autre termine ses opérations. Bien que PostgreSQL puisse les détecter et les terminer avec un ROLLBACK, les deadlocks peuvent quand même être gênants. Pour éviter que vos applications ne rencontrent ce problème, assurez-vous de les concevoir de telle sorte qu'elles verrouillent les objets dans le même ordre.

## Advisory Locks

PostgreSQL fournit des moyens pour créer des verrous qui ont des significations définies par l'application. Ces verrous sont appelés verrous consultatifs. Comme le système n'impose pas leur utilisation, c'est à l'application de les utiliser correctement. Les verrous consultatifs peuvent être utiles pour les stratégies de verrouillage qui s'adaptent mal au modèle MVCC.

Par exemple, une utilisation courante des verrous consultatifs est d'émuler les stratégies de verrouillage pessimistes typiques des systèmes de gestion de données dits "fichiers plats". Alors qu'un indicateur stocké dans une table pourrait être utilisé dans le même but, les verrous consultatifs sont plus rapides, évitent le gonflement des tables et sont automatiquement nettoyés par le serveur à la fin de la session.

### Exemple

Considérons la table COMPANY dont les enregistrements sont les suivants :

```sql
testdb# select * from COMPANY;
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

L'exemple suivant verrouille la table COMPANY dans la base de données ```testdb``` en mode ACCESS EXCLUSIVE. L'instruction LOCK fonctionne uniquement en mode transactionnel.

```sql
testdb=#BEGIN;
LOCK TABLE company1 IN ACCESS EXCLUSIVE MODE;
```

L'instruction PostgreSQL ci-dessus produira le résultat suivant :

```sql
LOCK TABLE
```

Le message ci-dessus indique que la table est verrouillée jusqu'à la fin de la transaction et que pour terminer la transaction, vous devrez soit faire marche arrière, soit valider la transaction.
