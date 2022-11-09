Redis scripting est utilisé pour évaluer les scripts en utilisant l'interpréteur Lua. Il est intégré à Redis à partir de la version 2.6.0. La commande utilisée pour le scripting est la commande **EVAL**.

## Syntaxe

Voici la syntaxe de base de la commande **EVAL**.

```bash
redis 127.0.0.1:6379> EVAL script numkeys key [key ...] arg [arg ...]
```

## Exemple

L'exemple suivant explique le fonctionnement du script Redis.

```bash
redis 127.0.0.1:6379> EVAL "return {KEYS[1],KEYS[2],ARGV[1],ARGV[2]}" 2 key1 
key2 first second  
1) "key1" 
2) "key2" 
3) "first" 
4) "second"
```

## Commandes de Redis Scripting

Le tableau suivant énumère quelques commandes de base liées à Redis Scripting.

**Commande et description**

- ```EVAL script numkeys key [key ...] arg [arg ...]``` - Exécute un script Lua.
- ```EVALSHA sha1 numkeys key [key ...] arg [arg ...]``` - Exécute un script Lua.
- ```SCRIPT EXISTS script [script ...]``` - Vérifie l'existence de scripts dans le cache des scripts.
- ```SCRIPT FLUSH``` - Supprime tous les scripts du cache des scripts.
- ```SCRIPT KILL``` - Tue le script en cours d'exécution.
- ```SCRIPT LOAD script``` - Charge le script Lua spécifié dans le cache des scripts.