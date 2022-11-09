Les commandes Redis sont utilisées pour effectuer certaines opérations sur le serveur Redis.

Pour exécuter des commandes sur le serveur Redis, vous avez besoin d'un client Redis. Le client Redis est disponible dans le paquet Redis, que nous avons installé précédemment.

### Syntaxe

Voici la syntaxe de base du client Redis.

```bash
$redis-cli 
```

### Exemple

L'exemple suivant explique comment nous pouvons démarrer le client Redis.

Pour démarrer le client Redis, ouvrez le terminal et tapez la commande redis-cli. Cela vous permettra de vous connecter à votre serveur local et vous pourrez alors exécuter n'importe quelle commande.

```bash
$redis-cli 
redis 127.0.0.1:6379> 
redis 127.0.0.1:6379> PING  
PONG
```

Dans l'exemple ci-dessus, nous nous connectons au serveur Redis fonctionnant sur la machine locale et exécutons une commande **PING**, qui vérifie si le serveur fonctionne ou non.

## Exécuter des commandes sur le serveur distant

Pour exécuter des commandes sur le serveur distant de Redis, vous devez vous connecter au serveur par le même client redis-cli

### Syntaxe

```bash
$ redis-cli -h host -p port -a password
```

### Exemple

L'exemple suivant montre comment se connecter au serveur distant Redis, fonctionnant sur l'hôte 127.0.0.1, sur le port 6379 et avec le mot de passe mypass.

```bash
$redis-cli -h 127.0.0.1 -p 6379 -a "mypass" 
redis 127.0.0.1:6379> 
redis 127.0.0.1:6379> PING  
PONG
```