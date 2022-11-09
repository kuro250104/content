Les listes Redis sont simplement des listes de chaînes de caractères, triées par ordre d'insertion. Vous pouvez ajouter des éléments dans les listes Redis en tête ou en queue de liste.

La longueur maximale d'une liste est de 232 - 1 éléments (4294967295, soit plus de 4 milliards d'éléments par liste).

## Exemple

```bash
redis 127.0.0.1:6379> LPUSH tutorials redis 
(integer) 1 
redis 127.0.0.1:6379> LPUSH tutorials mongodb 
(integer) 2 
redis 127.0.0.1:6379> LPUSH tutorials mysql 
(integer) 3 
redis 127.0.0.1:6379> LRANGE tutorials 0 10  
1) "mysql" 
2) "mongodb" 
3) "redis"
```

Dans l'exemple ci-dessus, trois valeurs sont insérées dans la liste Redis nommée 'tutoriels' par la commande **LPUSH**.

## Commandes de Redis Lists

Le tableau suivant présente quelques commandes de base liées aux listes.

**Command & Description**

- ```BLPOP key1 [key2 ] timeout``` - Supprime et récupère le premier élément d'une liste, ou bloqué jusqu'à ce qu'un élément soit disponible.
- ```BRPOP key1 [key2 ] timeout``` - Supprime et récupère le dernier élément d'une liste, ou bloque jusqu'à ce qu'un élément soit disponible.
- ```BRPOPLPUSH source destination timeout``` - Extrait une valeur d'une liste, la place dans une autre liste et la renvoie ; ou bloque jusqu'à ce qu'une valeur soit disponible.
- ```LINDEX key index``` - Obtient un élément d'une liste par son index.
- ```LINSERT key BEFORE|AFTER pivot value``` - Insère un élément avant ou après un autre élément dans une liste
- ```LLEN key``` - Obtient la longueur d'une liste
- ```LPOP key``` - Supprime et récupère le premier élément d'une liste
- ```LPUSH key value1 [value2]``` - Ajoute une ou plusieurs valeurs à une liste.
- ```LPUSHX key value``` - Ajoute une valeur à une liste, uniquement si la liste existe.
- ```LRANGE key start stop``` - Récupère une plage d'éléments dans une liste
- ```LREM key count value``` - Supprime les éléments d'une liste
- ```LSET key index value``` - Définit la valeur d'un élément d'une liste par son indice
- ```LTRIM key start stop``` - Ajuster une liste à l'intervalle spécifié
- ```RPOP key``` - Supprime et récupère le dernier élément d'une liste
- ```RPOPLPUSH source destination``` - Supprime le dernier élément d'une liste, l'ajoute à une autre liste et la renvoie.
- ```RPUSH key value1 [value2]``` - Ajoute une ou plusieurs valeurs à une liste
- ```RPUSHX key value``` - Ajoute une valeur à une liste, uniquement si la liste existe.