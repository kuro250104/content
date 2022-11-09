Les Redis Sorted Sets sont similaires aux Redis Sets avec la caractéristique unique de valeurs stockées dans un ensemble. La différence est que chaque membre d'un Sorted Set est associé à un score, qui est utilisé afin de prendre l'ensemble trié dans l'ordre, du plus petit au plus grand score.

Dans un ensemble trié Redis, ajouter, supprimer et tester l'existence de membres en O(1) (temps constant quel que soit le nombre d'éléments contenus dans l'ensemble). La longueur maximale d'une liste est de 232 - 1 éléments (4294967295, plus de 4 milliards d'éléments par ensemble).

## Exemple

```bash
redis 127.0.0.1:6379> ZADD tutorials 1 redis 
(integer) 1 
redis 127.0.0.1:6379> ZADD tutorials 2 mongodb 
(integer) 1 
redis 127.0.0.1:6379> ZADD tutorials 3 mysql 
(integer) 1 
redis 127.0.0.1:6379> ZADD tutorials 3 mysql 
(integer) 0 
redis 127.0.0.1:6379> ZADD tutorials 4 mysql 
(integer) 0 
redis 127.0.0.1:6379> ZRANGE tutorials 0 10 WITHSCORES  
1) "redis" 
2) "1" 
3) "mongodb" 
4) "2" 
5) "mysql" 
6) "4" 
```

Dans l'exemple ci-dessus, trois valeurs sont insérées avec leur score dans l'ensemble trié Redis nommé 'tutoriel' par la commande **ZADD**.

## Commandes de Redis Sorted Sets

Le tableau suivant présente quelques commandes de base liées aux ensembles triés.

**Commande et description**

- ```ZADD key score1 member1 [score2 member2]``` - Ajoute un ou plusieurs membres à un ensemble trié, ou met à jour son score, s'il existe déjà.
- ```ZCARD key``` - Obtient le nombre de membres dans un ensemble trié.
- ```ZCOUNT key min max``` - Compte les membres d'un ensemble trié dont les scores se situent dans les valeurs données.
- ```ZINCRBY key increment member``` - Augmente le score d'un membre dans un ensemble trié
- ```ZINTERSTORE destination numkeys key [key ...]``` - Intersecte plusieurs ensembles triés et stocke l'ensemble trié résultant dans une nouvelle clé.
- ```ZLEXCOUNT key min max``` - Compte le nombre de membres d'un ensemble trié entre une plage lexicographique donnée.
- ```ZRANGE key start stop [WITHSCORES]``` - Renvoie une plage de membres dans un ensemble trié, par index.
- ```ZRANGEBYLEX key min max [LIMIT offset count]``` - Renvoie une plage de membres dans un ensemble trié, par plage lexicographique.
- ```ZRANGEBYSCORE key min max [WITHSCORES] [LIMIT]``` - Renvoie une série de membres dans un ensemble trié, par score.
- ```ZRANK key member``` - Détermine l'indice d'un membre dans un ensemble trié.
- ```ZREM key member [member ...]``` - Supprime un ou plusieurs membres d'un ensemble trié.
- ```ZREMRANGEBYLEX key min max``` - Supprime tous les membres d'un ensemble trié compris dans l'intervalle lexicographique donné.
- ```ZREMRANGEBYRANK key start stop``` - Supprime tous les membres d'un ensemble trié dans les limites des index donnés.
- ```ZREMRANGEBYSCORE key min max``` - Supprime tous les membres d'un ensemble trié dans les limites des scores donnés.
- ```ZREVRANGE key start stop [WITHSCORES]``` - Renvoie une série de membres dans un ensemble trié, par index, avec des scores classés de haut en bas.
- ```ZREVRANGEBYSCORE key max min [WITHSCORES]``` - Renvoie une série de membres dans un ensemble trié, par score, les scores étant classés de haut en bas.
- ```ZREVRANK key member``` - Détermine l'indice d'un membre dans un ensemble trié, les scores étant classés de haut en bas.
- ```ZSCORE key member``` - Obtient le score associé au membre donné dans un ensemble trié.
- ```ZUNIONSTORE destination numkeys key [key ...]``` - Additionne plusieurs ensembles triés et stocke l'ensemble trié résultant dans une nouvelle clé.
- ```ZSCAN key cursor [MATCH pattern] [COUNT count]``` - Itère de façon incrémentielle les éléments des ensembles triés et les scores associés