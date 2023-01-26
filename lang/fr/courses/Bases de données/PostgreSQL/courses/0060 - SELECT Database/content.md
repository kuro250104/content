Ce chapitre explique les différentes méthodes d'accès à la base de données. Supposons que nous ayons déjà créé une base de données dans notre chapitre précédent. Vous pouvez sélectionner la base de données en utilisant l'une des méthodes suivantes :

- Base de données SQL Prompt
- Invite de commande OS

## Database SQL Prompt

Supposons que vous ayez déjà lancé votre client PostgreSQL et que vous ayez atterri à l'invite SQL suivante :

```sql
postgres=#
```

Vous pouvez vérifier la liste des bases de données disponibles à l'aide de la commande ```\l```, c'est-à-dire la commande backslash l, comme suit :

```sql
postgres-# \l
                             List of databases
   Name    |  Owner   | Encoding | Collate | Ctype |   Access privileges   
-----------+----------+----------+---------+-------+-----------------------
 postgres  | postgres | UTF8     | C       | C     | 
 template0 | postgres | UTF8     | C       | C     | =c/postgres          +
           |          |          |         |       | postgres=CTc/postgres
 template1 | postgres | UTF8     | C       | C     | =c/postgres          +
           |          |          |         |       | postgres=CTc/postgres
 testdb    | postgres | UTF8     | C       | C     | 
(4 rows)

postgres-#
```

Maintenant, tapez la commande suivante pour connecter/sélectionner une base de données souhaitée ; ici, nous allons nous connecter à la base de données ```testdb```.

```sql
postgres=# \c testdb;
psql (9.2.4)
Type "help" for help.
You are now connected to database "testdb" as user "postgres".
testdb=#
```

## OS Command Prompt

Vous pouvez sélectionner votre base de données à partir de l'invite de commande elle-même, au moment où vous vous connectez à votre base de données. Voici un exemple simple :

```sql
psql -h localhost -p 5432 -U postgress testdb
Password for user postgress: ****
psql (9.2.4)
Type "help" for help.
You are now connected to database "testdb" as user "postgres".
testdb=#
```

Vous êtes maintenant connecté à PostgreSQL ```testdb``` et prêt à exécuter vos commandes dans ```testdb```. Pour quitter la base de données, vous pouvez utiliser la commande ```\q```.
