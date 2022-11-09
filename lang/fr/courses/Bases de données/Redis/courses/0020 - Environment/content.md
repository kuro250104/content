Dans ce cours, vous apprendrez à configurer l'environnement de Redis.

## Installer Redis sur Ubuntu

Pour installer Redis sur Ubuntu, allez au terminal et tapez les commandes suivantes -

```bash
$sudo apt-get update 
$sudo apt-get install redis-server
```

Cela va installer Redis sur votre machine.

### Démarrer Redis

La commande pour démarrer Redis est :

```bash
$redis-server
```

### Vérifier le bon fonctionnement

Pour vérifier le bon fonctionnement de Redis, vous pouvez utiliser la commande suivante : 

```bash
$redis-cli 
```

Cela ouvrira une invite redis.

```bash
redis 127.0.0.1:6379>
```

Dans l'invite ci-dessus, 127.0.0.1 est l'adresse IP de votre machine et 6379 est le port sur lequel le serveur Redis fonctionne. Maintenant, tapez la commande ```PING``` suivante.

```bash
redis 127.0.0.1:6379> ping 
PONG
```

Cela montre que Redis est installé avec succès sur votre machine.

## Installer Redis Desktop Manager sur Ubuntu

Pour installer le gestionnaire de bureau Redis sur Ubuntu, il suffit de télécharger le paquet à partir de <a href="https://redisdesktop.com/download" target="_blank" title="téléchargement de Redis Desktop Manager">https://redisdesktop.com/download</a>

Ouvrez le paquet téléchargé et installez-le.

Le gestionnaire de bureau Redis vous donnera une interface utilisateur pour gérer vos clés et données Redis.

## Installation pour les autres OS

Si vous êtes sous Winows ou Mac, réferrez-vous à la documentation officielle de Redis pour l'installation : <a href="https://redis.io/" target="_blank" title="Site officiel de Redis">https://redis.io/</a>