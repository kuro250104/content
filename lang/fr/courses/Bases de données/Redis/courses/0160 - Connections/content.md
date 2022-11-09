Les commandes de connexion Redis sont essentiellement utilisées pour gérer les connexions des clients avec le serveur Redis.

## Exemple

L'exemple suivant explique comment un client s'authentifie auprès du serveur Redis et vérifie si le serveur fonctionne ou non.

```bash
redis 127.0.0.1:6379> AUTH "password" 
OK 
redis 127.0.0.1:6379> PING 
PONG 
```

## Commandes de Redis Connections

Le tableau suivant énumère quelques commandes de base liées aux connexions Redis.

**Commande et description**

- ```AUTH password``` - S'authentifie auprès du serveur avec le mot de passe donné.
- ```ECHO message``` - Imprime la chaîne de caractères donnée
- ```PING``` - Vérifie si le serveur est en cours d'exécution ou non
- ```QUIT``` - Ferme la connexion en cours
- ```SELECT index``` - Change la base de données sélectionnée pour la connexion actuelle