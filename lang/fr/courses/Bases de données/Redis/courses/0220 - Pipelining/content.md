Redis est un serveur TCP et supporte le protocole demande/réponse. Dans Redis, une demande est accomplie avec les étapes suivantes -

- Le client envoie une requête au serveur, et lit dans le socket, généralement de manière bloquante, la réponse du serveur.
- Le serveur traite la commande et renvoie la réponse au client.

## Meaning of Pipelining

La signification de base du pipelining est que le client peut envoyer plusieurs requêtes au serveur sans attendre les réponses, et lire les réponses en une seule étape.

### Exemple

Pour vérifier le pipelining Redis, il suffit de démarrer l'instance Redis et de taper la commande suivante dans le terminal.

```bash
$(echo -en "PING\r\n SET tutorial redis\r\nGET tutorial\r\nINCR 
visitor\r\nINCR visitor\r\nINCR visitor\r\n"; sleep 10) | nc localhost 6379  
+PONG 
+OK 
redis 
:1 
:2 
:3 
```

Dans l'exemple ci-dessus, nous allons vérifier la connexion Redis en utilisant la commande **PING**. Nous avons défini une chaîne nommée **tutorial** avec la valeur **redis**. Plus tard, nous récupérons la valeur de cette clé et incrémentons le nombre de visiteurs trois fois. Dans le résultat, nous pouvons voir que toutes les commandes sont soumises à Redis une fois, et Redis fournit la sortie de toutes les commandes en une seule étape.

## Avantages du Pipelining

L'avantage de cette technique est une amélioration radicale des performances du protocole. L'accélération obtenue par le pipelining va d'un facteur cinq pour les connexions à l'hôte local à un facteur d'au moins cent pour les connexions Internet plus lentes.