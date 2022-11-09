Redis benchmark est un utilitaire permettant de vérifier les performances de Redis en exécutant n commandes simultanément.

## Syntaxe

Voici la syntaxe de base du benchmark Redis.

```bash
redis-benchmark [option] [option value] 
```

## Exemple

Following example checks Redis by calling 100000 commands.

```bash
redis-benchmark -n 100000  

PING_INLINE: 141043.72 requests per second 
PING_BULK: 142857.14 requests per second 
SET: 141442.72 requests per second 
GET: 145348.83 requests per second 
INCR: 137362.64 requests per second 
LPUSH: 145348.83 requests per second 
LPOP: 146198.83 requests per second 
SADD: 146198.83 requests per second 
SPOP: 149253.73 requests per second 
LPUSH (needed to benchmark LRANGE): 148588.42 requests per second 
LRANGE_100 (first 100 elements): 58411.21 requests per second 
LRANGE_300 (first 300 elements): 21195.42 requests per second 
LRANGE_500 (first 450 elements): 14539.11 requests per second 
LRANGE_600 (first 600 elements): 10504.20 requests per second 
MSET (10 keys): 93283.58 requests per second 
```

Voici une liste des options disponibles dans le benchmark Redis.

| **Option** | **Description** | **Valeur par défaut** |
| --- | --- | --- |
| ```-h``` | Spécifie le nom d'hôte du serveur | ```127.0.0.1``` |
| ```-p``` | Spécifie le port du serveur | ```6379``` |
| ```-s``` | Spécifie le socket du serveur |  |
| ```-c``` | Spécifie le nombre de connexions parallèles | ```50``` |
| ```-n``` | Spécifie le nombre total de demandes | ```10000``` |
| ```-d``` | Spécifie la taille des données de la valeur SET/GET en octets. | ```2``` |
| ```-k``` | 1=maintien en vie, 0=reconnexion | ```1``` |
| ```-r``` | Utilisez des touches aléatoires pour SET/GET/INCR et des valeurs aléatoires pour SADD. |  |
| ```-p``` | Pipeline ```<numreq>``` demandes | ```1``` |
| ```-h``` | Spécifie le nom d'hôte du serveur |  |
| ```-q``` | Force le silence à Redis. Montre seulement les valeurs de requête/sec |  |
| ```--csv``` | Sortie en format CSV |  |
| ```-l``` | Génère une boucle, exécute les tests à l'infini |  |
| ```-t``` | Exécute uniquement la liste de tests séparés par des virgules. |  |
| ```-I``` | Mode inactif. Ouvre juste N connexions inactives et attend |  |

## Exemple

L'exemple suivant montre les multiples options d'utilisation de l'utilitaire de référence Redis.

```bash
redis-benchmark -h 127.0.0.1 -p 6379 -t set,lpush -n 100000 -q  

SET: 146198.83 requests per second 
LPUSH: 145560.41 requests per second
```