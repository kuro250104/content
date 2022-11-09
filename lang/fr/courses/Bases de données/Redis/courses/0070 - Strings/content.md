Les commandes de chaînes de Redis sont utilisées pour gérer les valeurs de chaînes dans Redis. Voici la syntaxe pour utiliser les commandes de chaînes de Redis.

## Syntaxe

```bash
redis 127.0.0.1:6379> COMMAND KEY_NAME 
```

## Exemple

```bash
redis 127.0.0.1:6379> SET microlead redis 
OK 
redis 127.0.0.1:6379> GET microlead
"redis" 
```

Dans l'exemple ci-dessus, **SET** et **GET** sont les commandes, tandis que **microlead** est la clé.

## Redis Strings Commands

Le tableau suivant liste quelques commandes de base pour gérer les chaînes de caractères dans Redis.

**Command & Description**

- **SET key value** - Cette commande définit la valeur de la touche spécifiée.
- **GET key** - Obtient la valeur d'une clé.
- **GETRANGE key start end** - Obtient une sous-chaîne de la chaîne stockée à une clé.
- **GETSET key value** - Définit la valeur de la chaîne de caractères d'une clé et retourne son ancienne valeur.
- **GETBIT key offset** - Renvoie la valeur du bit à l'offset dans la valeur de la chaîne stockée à la clé.
- **MGET key1 [key2..]** - Récupère les valeurs de toutes les clés données
- **SETBIT key offset value** - Règle ou efface le bit à l'offset dans la valeur de la chaîne stockée à la clé.
- **SETEX key seconds value** - Définit la valeur avec l'expiration d'une clé
- **SETNX key value** - Définit la valeur d'une clé, uniquement si la clé n'existe pas.
- **SETRANGE key offset value** - Écrase la partie d'une chaîne de caractères à la clé commençant à l'offset spécifié
- **STRLEN key** - Obtient la longueur de la valeur stockée dans une clé
- **MSET key value [key value ...]** - Définit des clés multiples à des valeurs multiples
- **MSETNX key value [key value ...]** - Définit des clés multiples en valeurs multiples, uniquement si aucune des clés n'existe.
- **PSETEX key milliseconds value** - Définit la valeur et l'expiration en millisecondes d'une clé
- **INCR key** - Augmente de un la valeur entière d'une clé
- **INCRBY key increment** - Augmente la valeur entière d'une clé par la quantité donnée.
- **INCRBYFLOAT key increment** - Augmente la valeur flottante d'une clé de la quantité donnée.
- **DECR key** - Diminue de un la valeur entière d'une clé
- **DECRBY key decrement** - Diminue la valeur entière d'une clé par le nombre donné.
- **APPEND key value** - Ajoute une valeur à une clé