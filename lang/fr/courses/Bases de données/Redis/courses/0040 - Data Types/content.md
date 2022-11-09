Redis supporte 5 types de données.

## Strings

La chaîne de Redis est une séquence d'octets. Les chaînes dans Redis sont binaires, ce qui signifie qu'elles ont une longueur connue qui n'est pas déterminée par des caractères spéciaux de fin de chaîne. Ainsi, vous pouvez stocker n'importe quoi jusqu'à 512 mégaoctets dans une chaîne.

### Exemple

```bash
redis 127.0.0.1:6379> SET name "microlead " 
OK 
redis 127.0.0.1:6379> GET name 
"microlead "
```

Dans l'exemple ci-dessus, **SET** et **GET** sont des commandes Redis, **name** est la clé utilisée dans Redis et **microlead** est la valeur de la chaîne qui est stockée dans Redis.

__Remarque__ − Une chaîne de caractères peut avoir une longueur maximale de 512 mégaoctets.

## Hashes

Un hachage Redis est une collection de paires clé-valeur. Les hachages Redis sont des cartes entre des champs de chaînes de caractères et des valeurs de chaînes de caractères. Ils sont donc utilisés pour représenter des objets.

### Exemple

```bash
redis 127.0.0.1:6379> HMSET user:1 username microlead password 
tutorialspoint points 200 
OK 
redis 127.0.0.1:6379> HGETALL user:1  
1) "username" 
2) "microlead" 
3) "password" 
4) "microlead" 
5) "points" 
6) "200"
```

Dans l'exemple ci-dessus, le type de données hash est utilisé pour stocker l'objet de l'utilisateur qui contient les informations de base de l'utilisateur. Ici, **HMSET**, **HGETALL** sont des commandes pour Redis, tandis que user - 1 est la clé.

Chaque hachage peut stocker jusqu'à 232 - 1 paires champ-valeur (plus de 4 milliards).

## Lists

Les listes Redis sont simplement des listes de chaînes de caractères, triées par ordre d'insertion. Vous pouvez ajouter des éléments à une liste Redis en tête ou en queue de liste.

### Exemple

```bash
redis 127.0.0.1:6379> lpush microlist redis 
(integer) 1 
redis 127.0.0.1:6379> lpush microlist mongodb 
(integer) 2 
redis 127.0.0.1:6379> lpush tutoriallist rabitmq 
(integer) 3 
redis 127.0.0.1:6379> lrange microlist 0 10  

1) "rabitmq" 
2) "mongodb" 
3) "redis"
```

La longueur maximale d'une liste est de 232 - 1 éléments (4294967295, soit plus de 4 milliards d'éléments par liste).

## Sets

Les ensembles Redis sont une collection non ordonnée de chaînes de caractères. Dans Redis, vous pouvez ajouter, supprimer, et tester l'existence des membres en une complexité de temps O(1).

### Exemple

```bash
redis 127.0.0.1:6379> sadd microlist redis 
(integer) 1 
redis 127.0.0.1:6379> sadd microlist mongodb 
(integer) 1 
redis 127.0.0.1:6379> sadd microlist rabitmq 
(integer) 1 
redis 127.0.0.1:6379> sadd microlist rabitmq 
(integer) 0 
redis 127.0.0.1:6379> smembers microlist  

1) "rabitmq" 
2) "mongodb" 
3) "redis" 
```

__Remarque__ − Dans l'exemple ci-dessus, **rabitmq** est ajouté deux fois, mais en raison de la propriété unique de l'ensemble, il n'est ajouté qu'une fois.

Le nombre maximal de membres dans un ensemble est de 232 - 1 (4294967295, soit plus de 4 milliards de membres par ensemble).

## Sorted Sets

Les Redis Sorted Sets sont similaires aux Redis Sets, des collections non répétitives de chaînes de caractères. La différence est que chaque membre d'un **Sorted Set** est associé à un score, qui est utilisé afin de prendre l'ensemble trié dans l'ordre, du plus petit au plus grand score. Bien que les membres soient uniques, les scores peuvent être répétés.

### Exemple

```bash
redis 127.0.0.1:6379> zadd microlist 0 redis 
(integer) 1 
redis 127.0.0.1:6379> zadd microlist 0 mongodb 
(integer) 1 
redis 127.0.0.1:6379> zadd microlist 0 rabitmq 
(integer) 1 
redis 127.0.0.1:6379> zadd microlist 0 rabitmq 
(integer) 0 
redis 127.0.0.1:6379> ZRANGEBYSCORE microlist 0 1000  

1) "redis" 
2) "mongodb" 
3) "rabitmq"
```