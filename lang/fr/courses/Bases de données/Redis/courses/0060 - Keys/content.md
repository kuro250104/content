Les commandes Redis keys sont utilisées pour gérer les clés dans Redis. Voici la syntaxe pour utiliser les commandes redis keys.

## Syntaxe


```bash
redis 127.0.0.1:6379> COMMAND KEY_NAME
```

## Exemple

```bash
redis 127.0.0.1:6379> SET microlead redis 
OK 
redis 127.0.0.1:6379> DEL microlead
(integer) 1
```

Dans l'exemple ci-dessus, **DEL** est la commande, tandis que **microlead** est la clé. Si la clé est supprimée, alors la sortie de la commande sera (entier) 1, sinon elle sera (entier) 0.

## Commandes de Redis Keys

Le tableau suivant énumère quelques commandes de base liées aux touches.

**Commande et description**

- **DEL key** - Cette commande supprime la clé, si elle existe.
- **DUMP key** - Cette commande renvoie une version sérialisée de la valeur stockée à la clé spécifiée.
- **EXISTS key** - Cette commande vérifie si la clé existe ou non.
- **EXPIRE key seconds** - Définit l'expiration de la clé après le temps spécifié.
- **EXPIREAT key timestamp** - Définit l'expiration de la clé après le temps spécifié. Ici, le temps est au format timestamp Unix.
- **PEXPIRE key milliseconds** - Définit l'expiration de la clé en millisecondes.
- **PEXPIREAT key milliseconds-timestamp** - Définit l'expiration de la clé en timestamp Unix spécifié en millisecondes.
- **KEYS pattern** - Recherche toutes les clés correspondant au motif spécifié.
- **MOVE key db** - Déplace une clé vers une autre base de données.
- **PERSIST key** - Supprimer l'expiration de la clé.
- **PTTL key** - Obtient le temps restant dans l'expiration des clés en millisecondes.
- **TTL key** - Obtient le temps restant dans l'expiration des clés.
- **RANDOMKEY** - Renvoie une clé aléatoire de Redis.
- **RENAME key newkey** - Change le nom de la clé.
- **RENAMENX key newkey** - Renomme la clé, si une nouvelle clé n'existe pas.
- **TYPE key** - Renvoie le type de données de la valeur stockée dans la clé.