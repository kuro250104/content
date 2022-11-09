Les transactions Redis permettent l'exécution d'un groupe de commandes en une seule étape. Voici les deux propriétés des transactions.

- Toutes les commandes d'une transaction sont exécutées séquentiellement comme une seule opération isolée. Il est impossible qu'une requête émise par un autre client soit servie au milieu de l'exécution d'une transaction Redis.
- La transaction Redis est également atomique. Atomique signifie que soit toutes les commandes, soit aucune ne sont traitées.

# Sample

La transaction Redis est initiée par la commande **MULTI** et ensuite vous devez passer une liste de commandes qui doivent être exécutées dans la transaction, après quoi la transaction entière est exécutée par la commande **EXEC**.

```bash
redis 127.0.0.1:6379> MULTI 
OK 
List of commands here 
redis 127.0.0.1:6379> EXEC
```

### Exemple

L'exemple suivant explique comment une transaction Redis peut être initiée et exécutée.

```bash
redis 127.0.0.1:6379> MULTI 
OK 
redis 127.0.0.1:6379> SET tutorial redis 
QUEUED 
redis 127.0.0.1:6379> GET tutorial 
QUEUED 
redis 127.0.0.1:6379> INCR visitors 
QUEUED 
redis 127.0.0.1:6379> EXEC  
1) OK 
2) "redis" 
3) (integer) 1
```

## Commandes de Redis Transactions

Le tableau suivant montre quelques commandes de base liées aux transactions Redis.

**Commande et description**

- ```DISCARD``` - Ignore toutes les commandes émises après MULTI
- ```EXEC``` - Exécute toutes les commandes émises après MULTI
- ```MULTI``` - Marque le début d'un bloc de transaction
- ```UNWATCH``` - Oublie toutes les clés surveillées
- ```WATCH key [key ...]``` - Surveille les clés données pour déterminer l'exécution du bloc MULTI/EXEC.