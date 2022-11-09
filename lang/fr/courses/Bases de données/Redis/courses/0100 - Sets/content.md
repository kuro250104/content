Les ensembles Redis sont une collection non ordonnée de chaînes uniques. Unique signifie que les ensembles ne permettent pas la répétition des données dans une clé.

Dans l'ensemble Redis ajouter, enlever, et tester l'existence de membres en O(1) (temps constant quel que soit le nombre d'éléments contenus dans l'ensemble). La longueur maximale d'une liste est de 232 - 1 éléments (4294967295, plus de 4 milliards d'éléments par ensemble).

## Exemple

```bash
redis 127.0.0.1:6379> SADD tutorials redis 
(integer) 1 
redis 127.0.0.1:6379> SADD tutorials mongodb 
(integer) 1 
redis 127.0.0.1:6379> SADD tutorials mysql 
(integer) 1 
redis 127.0.0.1:6379> SADD tutorials mysql 
(integer) 0 
redis 127.0.0.1:6379> SMEMBERS tutorials  
1) "mysql" 
2) "mongodb" 
3) "redis"
```

Dans l'exemple ci-dessus, trois valeurs sont insérées dans l'ensemble Redis nommé 'tutoriel' par la commande **SADD**.

## Redis Sets Commands

Le tableau suivant liste quelques commandes de base liées aux ensembles.

**Commande et description**

- ```SADD key member1 [member2]``` - Ajoute un ou plusieurs membres à un ensemble
- ```SCARD key``` - Obtient le nombre de membres dans un ensemble
- ```SDIFF key1 [key2]``` - Soustraire des ensembles multiples
- ```SDIFFSTORE destination key1 [key2]``` - Soustraire plusieurs ensembles et stocker l'ensemble résultant dans une clé
- ```SINTER key1 [key2]``` - Intersection de plusieurs ensembles
- ```SINTERSTORE destination key1 [key2]``` - Intersecte plusieurs ensembles et stocke l'ensemble résultant dans une clé
- ```SISMEMBER key member``` - Détermine si une valeur donnée est membre d'un ensemble.
- ```SMEMBERS key``` - Récupère tous les membres d'un ensemble
- ```SMOVE source destination member``` - Déplace un membre d'un ensemble à un autre
- ```SPOP key``` - Supprime et renvoie un membre aléatoire d'un ensemble.
- ```SRANDMEMBER key [count]``` - Obtient un ou plusieurs membres aléatoires d'un ensemble.
- ```SREM key member1 [member2]``` - Supprime un ou plusieurs membres d'un ensemble
- ```SUNION key1 [key2]``` - Ajoute des ensembles multiples
- ```SUNIONSTORE destination key1 [key2]``` - Additionne plusieurs ensembles et stocke l'ensemble résultant dans une clé
- ```SSCAN key cursor [MATCH pattern] [COUNT count]``` - Itère de façon incrémentielle les éléments de l'ensemble