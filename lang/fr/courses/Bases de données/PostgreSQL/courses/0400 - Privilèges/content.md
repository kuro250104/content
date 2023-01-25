Chaque fois qu'un objet est créé dans une base de données, un propriétaire lui est attribué. Le propriétaire est généralement celui qui a exécuté l'instruction de création. Pour la plupart des types d'objets, l'état initial est que seul le propriétaire (ou un superutilisateur) peut modifier ou supprimer l'objet. Pour permettre à d'autres rôles ou utilisateurs de l'utiliser, des privilèges ou des autorisations doivent être accordés.

Les différents types de privilèges dans PostgreSQL sont :

- SELECT,
- INSERT,
- UPDATE,
- DELETE,
- TRUNCATE,
- REFERENCES,
- TRIGGER,
- CREATE,
- CONNECT,
- TEMPORARY,
- EXECUTE, and
- USAGE

En fonction du type d'objet (table, fonction, etc.), des privilèges sont appliqués à l'objet. Pour attribuer des privilèges aux utilisateurs, on utilise la commande GRANT.

## Syntaxe pour GRANT

La syntaxe de base de la commande GRANT est la suivante :

```sql
GRANT privilege [, ...]
ON object [, ...]
TO { PUBLIC | GROUP group | username }
```

- **privilege** − Les valeurs peuvent être : SELECT, INSERT, UPDATE, DELETE, RULE, ALL.
- **object** − Le nom d'un objet auquel il faut accorder l'accès. Les objets possibles sont : table, vue, séquence.
- **PUBLIC** − Un formulaire court représentant tous les utilisateurs.
- **GROUP group** − Un groupe à qui accorder des privilèges.
- **username** − Le nom d'un utilisateur à qui accorder des privilèges. PUBLIC est une forme abrégée représentant tous les utilisateurs.

Les privilèges peuvent être révoqués à l'aide de la commande REVOKE.

## Syntaxe pour REVOKE

La syntaxe de base de la commande REVOKE est la suivante :

```sql
REVOKE privilege [, ...]
ON object [, ...]
FROM { PUBLIC | GROUP groupname | username }
```

- **privilege** − Les valeurs peuvent être : SELECT, INSERT, UPDATE, DELETE, RULE, ALL.
- **object** − Le nom d'un objet auquel il faut accorder l'accès. Les objets possibles sont : table, vue, séquence.
- **PUBLIC** − Un formulaire court représentant tous les utilisateurs.
- **GROUP group** − Un groupe à qui accorder des privilèges.
- **username** − Le nom d'un utilisateur à qui accorder des privilèges. PUBLIC est une forme abrégée représentant tous les utilisateurs.

## Exemple

Pour comprendre les privilèges, créons tout d'abord un USER comme suit :

```sql
testdb=# CREATE USER manisha WITH PASSWORD 'password';
CREATE ROLE
```

Le message CREATE ROLE indique que l'USER "manisha" est créé.

Considérons la table COMPANY contenant les enregistrements suivants :

```bash
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

Ensuite, accordons tous les privilèges sur une table SOCIÉTÉ à l'utilisateur "manisha" comme suit :

```sql
testdb=# GRANT ALL ON COMPANY TO manisha;
GRANT
```

Le message GRANT indique que tous les privilèges sont attribués à l'UTILISATEUR.

Ensuite, révoquons les privilèges de l'UTILISATEUR "manisha" de la manière suivante :

```sql
testdb=# REVOKE ALL ON COMPANY FROM manisha;
REVOKE
```

Le message REVOKE indique que tous les privilèges sont retirés à l'UTILISATEUR.

Vous pouvez même supprimer l'utilisateur comme suit :

```sql
testdb=# DROP USER manisha;
DROP ROLE
```

Le message DROP ROLE indique que l'USER 'Manisha' est supprimé de la base de données.
