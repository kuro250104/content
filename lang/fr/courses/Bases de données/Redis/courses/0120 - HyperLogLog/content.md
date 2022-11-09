Redis HyperLogLog est un algorithme qui utilise la randomisation afin de fournir une approximation du nombre d'éléments uniques dans un ensemble en utilisant seulement une constante et une petite quantité de mémoire.

HyperLogLog fournit une très bonne approximation de la cardinalité d'un ensemble même en utilisant une très petite quantité de mémoire autour de 12 kbytes par clé avec une erreur standard de 0,81%. Il n'y a pas de limite au nombre d'éléments que vous pouvez compter, sauf si vous approchez les 264 éléments.

## Exemple

L'exemple suivant explique le fonctionnement de Redis HyperLogLog.

```bash
redis 127.0.0.1:6379> PFADD tutorials "redis"  
1) (integer) 1  
redis 127.0.0.1:6379> PFADD tutorials "mongodb"  
1) (integer) 1  
redis 127.0.0.1:6379> PFADD tutorials "mysql"  
1) (integer) 1  
redis 127.0.0.1:6379> PFCOUNT tutorials  
(integer) 3 
```

## Commandes de Redis HyperLogLog

Le tableau suivant liste quelques commandes de base liées à Redis HyperLogLog.

**Commande et description**

- ```PFADD key element [element ...]``` - Ajoute les éléments spécifiés au HyperLogLog spécifié.
- ```PFCOUNT key [key ...]``` - Renvoie la cardinalité approximative du ou des ensembles observés par le HyperLogLog à la ou aux clés.
- ```PFMERGE destkey sourcekey [sourcekey ...]``` - Fusionne N HyperLogLogs différents en un seul.