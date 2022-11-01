## Introduction

Une transaction est un groupe séquentiel d'opérations de manipulation de la base de données, qui est exécuté comme 
s'il s'agissait d'une seule unité de travail. En d'autres termes, une transaction ne sera jamais terminée si chaque 
opération individuelle du groupe n'est pas réussie. Si une opération de la transaction échoue, la transaction entière échoue.

En pratique, vous regroupez plusieurs requêtes SQL dans un groupe et vous les exécutez toutes ensemble dans le cadre
d'une transaction.

## Properties of Transactions

Les transactions possèdent les quatre propriétés standard suivantes, généralement désignées par l'acronyme **ACID**.

  - **Atomicity** − Cela garantit que toutes les opérations de l'unité de travail se terminent avec succès ; sinon, la transaction est interrompue au point d'échec et les opérations précédentes sont ramenées à leur état antérieur.
  - **Consistency** − Cela garantit que la base de données change correctement d'état lors d'une transaction validée avec succès.
  - **Isolation** − Cela permet aux transactions de fonctionner indépendamment les unes des autres et de manière transparente.
  - **Durability** - Elle garantit que le résultat ou l'effet d'une transaction engagée persiste en cas de défaillance du système.

Dans MySQL, les transactions commencent par l'instruction **BEGIN WORK** et se terminent par une instruction **COMMIT**
ou **ROLLBACK**. Les commandes SQL entre les instructions de début et de fin constituent l'essentiel de la transaction.

## COMMIT and ROLLBACK

Ces deux mots-clés **Commit** et **Rollback** sont principalement utilisés pour les transactions MySQL.

  - Lorsqu'une transaction réussie est terminée, la commande COMMIT doit être émise afin que les modifications apportées à toutes les tables concernées soient prises en compte.
  - En cas d'échec, une commande ROLLBACK doit être émise pour que chaque table référencée dans la transaction revienne à son état précédent.

Vous pouvez contrôler le comportement d'une transaction en définissant une variable de session appelée **AUTOCOMMIT**.
Si AUTOCOMMIT a la valeur 1 (valeur par défaut), chaque instruction SQL (dans une transaction ou non) est considérée 
comme une transaction complète et est validée par défaut lorsqu'elle se termine.

Lorsque AUTOCOMMIT est réglé sur 0, en émettant la commande **SET AUTOCOMMIT = 0**, la série d'instructions suivante
agit comme une transaction et aucune activité n'est engagée jusqu'à ce qu'une instruction COMMIT explicite soit émise.

Vous pouvez exécuter ces commandes SQL en PHP en utilisant la fonction **mysql_query()**.

## A Generic Example on Transaction

Cette séquence d'événements est indépendante du langage de programmation utilisé. Le chemin logique peut être créé dans
n'importe quel langage que vous utilisez pour créer votre application.

Vous pouvez exécuter ces commandes SQL en PHP en utilisant la fonction **mysql_query()**.

  - Commencez la transaction en émettant la commande SQL BEGIN WORK.
  - Émettre une ou plusieurs commandes SQL comme SELECT, INSERT, UPDATE ou DELETE.
  - Vérifiez qu'il n'y a pas d'erreur et que tout est conforme à vos exigences.
  - S'il y a une erreur, émettez une commande ROLLBACK, sinon émettez une commande COMMIT.


## Transaction-Safe Table Types in MySQL

Vous ne pouvez pas utiliser les transactions directement, mais vous pouvez le faire pour certaines exceptions. Cependant,
elles ne sont pas sûres et garanties. Si vous prévoyez d'utiliser les transactions dans votre programmation MySQL,
vous devez créer vos tables d'une manière spéciale. Il existe de nombreux types de tables qui supportent les transactions, 
mais le plus populaire est **InnoDB**.

Le support des tables InnoDB nécessite un paramètre de compilation spécifique lors de la compilation de MySQL à partir
de la source. Si votre version de MySQL ne prend pas en charge InnoDB, demandez à votre fournisseur de services Internet
de construire une version de MySQL prenant en charge les types de tables InnoDB ou téléchargez et installez 
la **distribution binaire MySQL-Max** pour Windows ou Linux/UNIX et travaillez avec le type de table dans un 
environnement de développement.

Si votre installation MySQL prend en charge les tables InnoDB, il suffit d'ajouter une définition **TYPE = InnoDB** à 
l'instruction de création de table.

Par exemple, le code suivant crée une table InnoDB appelée tcount_tbl :

``` sql
root@host# mysql -u root -p password;
Enter password:*******

mysql> use TUTORIALS;
Database changed

mysql> create table tcount_tbl
   -> (
   -> tutorial_author varchar(40) NOT NULL,
   -> tutorial_count  INT
   -> ) TYPE = InnoDB;
Query OK, 0 rows affected (0.05 sec)
```

Pour plus de détails sur InnoDB, vous pouvez cliquer sur le lien suivant -InnoDB

Vous pouvez utiliser d'autres types de tables comme **GEMINI** ou **BDB**, mais cela dépend de votre installation,
si elle supporte ces deux types de tables ou non.