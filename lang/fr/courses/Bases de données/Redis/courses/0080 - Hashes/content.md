Les hachages Redis sont des cartes entre les champs de chaînes de caractères et les valeurs de chaînes de caractères. Ils constituent donc le type de données idéal pour représenter des objets.

Dans Redis, chaque hachage peut stocker jusqu'à plus de 4 milliards de paires champ-valeur.

## Exemple

```bash
redis 127.0.0.1:6379> HMSET tutorialspoint name "redis tutorial" 
description "redis basic commands for caching" likes 20 visitors 23000 
OK 
redis 127.0.0.1:6379> HGETALL tutorialspoint  
1) "name" 
2) "redis tutorial" 
3) "description" 
4) "redis basic commands for caching" 
5) "likes" 
6) "20" 
7) "visitors" 
8) "23000"
```

Dans l'exemple ci-dessus, nous avons défini les détails des tutoriels Redis (nom, description, goûts, visiteurs) dans un hash nommé 'tutorialspoint'.

## Redis Hash Commands

Le tableau suivant liste quelques commandes de base liées au hachage.

**Command & Description**

- ```HDEL key field2 [field2]``` - Supprime un ou plusieurs champs de hachage.
- ```HEXISTS key field``` - Détermine si un champ de hachage existe ou non.
- ```HGET key field``` - Obtient la valeur d'un champ de hachage stocké à la clé spécifiée.
- ```HGETALL key``` - Récupère tous les champs et toutes les valeurs stockés dans un hachage à la clé spécifiée.
- ```HINCRBY key field increment``` - Augmente la valeur entière d'un champ de hachage par le nombre donné.
- ```HINCRBYFLOAT key field increment``` - Augmente la valeur flottante d'un champ de hachage de la quantité donnée.
- ```HKEYS key``` - Récupère tous les champs dans un hash
- ```HLEN key``` - Obtient le nombre de champs dans un hachage.
- ```HMGET key field1 [field2]``` - Récupère les valeurs de tous les champs de hachage donnés
- ```HMSET key field1 value1 [field2 value2 ]``` - Définit plusieurs champs de hachage à plusieurs valeurs
- ```HSET key field value``` - Définit la valeur de la chaîne d'un champ de hachage
- ```HSETNX key field value``` - Définit la valeur d'un champ de hachage, uniquement si le champ n'existe pas.
- ```HVALS key``` - Récupère toutes les valeurs d'un hachage
- ```HSCAN key cursor [MATCH pattern] [COUNT count]``` - Il intègre de manière incrémentielle les champs de hachage et les valeurs associées.