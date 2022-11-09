Redis Pub/Sub implémente le système de messagerie où les expéditeurs (appelés éditeurs dans la terminologie Redis) envoient les messages tandis que les récepteurs (abonnés) les reçoivent. Le lien par lequel les messages sont transférés est appelé **canal**.

Dans Redis, un client peut s'abonner à un nombre quelconque de canaux.

## Exemple

L'exemple suivant explique le fonctionnement du concept de publication et d'abonnement. Dans l'exemple suivant, un client s'abonne à un canal nommé 'redisChat'.

```bash
redis 127.0.0.1:6379> SUBSCRIBE redisChat  
Reading messages... (press Ctrl-C to quit) 
1) "subscribe" 
2) "redisChat" 
3) (integer) 1 
```

Maintenant, deux clients publient les messages sur le même canal nommé 'redisChat' et le client abonné ci-dessus reçoit les messages.

```bash
redis 127.0.0.1:6379> PUBLISH redisChat "Redis is a great caching technique"  
(integer) 1  
redis 127.0.0.1:6379> PUBLISH redisChat "Learn redis by tutorials point"  
(integer) 1   
1) "message" 
2) "redisChat" 
3) "Redis is a great caching technique" 
1) "message" 
2) "redisChat" 
3) "Learn redis by tutorials point"
```

## Redis PubSub Commands

Le tableau suivant liste quelques commandes de base liées à Redis Pub/Sub.

**Commande et description**

- ```PSUBSCRIBE pattern [pattern ...]``` - S'abonner aux canaux correspondant aux modèles donnés.
- ```PUBSUB subcommand [argument [argument ...]]``` - Indique l'état du système Pub/Sub. Par exemple, quels clients sont actifs sur le serveur.
- ```PUBLISH channel message``` - Affiche un message sur un canal.
- ```PUNSUBSCRIBE [pattern [pattern ...]]``` - Arrête d'écouter les messages postés sur les canaux correspondant aux modèles donnés.
- ```SUBSCRIBE channel [channel ...]``` - Écouter les messages publiés sur les canaux donnés.
- ```UNSUBSCRIBE [channel [channel ...]]``` - Arrête d'écouter les messages postés sur les canaux donnés.