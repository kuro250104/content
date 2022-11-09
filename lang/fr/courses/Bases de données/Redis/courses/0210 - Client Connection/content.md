Redis accepte les connexions des clients sur le port TCP d'écoute configuré et sur le socket Unix, s'il est activé. Lorsqu'une nouvelle connexion client est acceptée, les opérations suivantes sont effectuées -

- Le socket client est mis dans un état non bloquant puisque Redis utilise le multiplexage et les E/S non bloquantes.
- L'option TCP_NODELAY est définie afin de s'assurer que nous n'avons pas de retard dans notre connexion.
- Un événement de fichier lisible est créé afin que Redis soit capable de collecter les requêtes du client dès que de nouvelles données sont disponibles pour être lues sur le socket.

## Maximum Number of Clients

Dans la configuration de Redis (redis.conf), il y a une propriété appelée maxclients, qui décrit le nombre maximum de clients qui peuvent se connecter à Redis.

Voici la syntaxe de base de la commande.

```bash
config get maxclients  

1) "maxclients" 
2) "10000" 
```

Par défaut, cette propriété est fixée à 10000 (en fonction de la limite du nombre maximum de descripteurs de fichiers du système d'exploitation), mais vous pouvez modifier cette propriété.

## Exemple

Dans l'exemple suivant, nous avons fixé le nombre maximum de clients à 100000, tout en démarrant le serveur.

```bash
redis-server --maxclients 100000 
```

## Commandes Client

**Command et Description**

- ```CLIENT LIST``` - Renvoie la liste des clients connectés au serveur Redis.
- ```CLIENT SETNAME``` - Attribue un nom à la connexion en cours
- ```CLIENT GETNAME``` - Renvoie le nom de la connexion actuelle tel que défini par CLIENT SETNAME
- ```CLIENT PAUSE``` - Il s'agit d'une commande de contrôle des connexions capable de suspendre tous les clients Redis pendant la durée spécifiée (en millisecondes).
- ```CLIENT KILL``` - Cette commande permet de fermer une connexion client donnée.