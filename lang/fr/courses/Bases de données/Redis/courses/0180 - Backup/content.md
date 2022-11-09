La commande Redis **SAVE** est utilisée pour créer une sauvegarde de la base de données Redis actuelle.

## Syntaxe

Voici la syntaxe de base de la commande redis **SAVE**.

```bash
127.0.0.1:6379> SAVE 
```

## Exemple

L'exemple suivant crée une sauvegarde de la base de données actuelle.

```bash
127.0.0.1:6379> SAVE  
OK 
```

Cette commande va créer un fichier ```dump.rdb``` dans votre répertoire Redis.

## Restaurer les données Redis

Pour restaurer les données Redis, déplacez le fichier de sauvegarde Redis (dump.rdb) dans votre répertoire Redis et démarrez le serveur. Pour obtenir votre répertoire Redis, utilisez la commande **CONFIG** de Redis comme indiqué ci-dessous.

```bash
127.0.0.1:6379> CONFIG get dir  
1) "dir" 
2) "/user/microlead/redis-2.8.13/src" 
```

Dans la sortie de la commande ci-dessus, ```/user/microlead/redis-2.8.13/src``` est le répertoire où le serveur Redis est installé.

## Bgsave

Pour créer une sauvegarde de Redis, une commande alternative **BGSAVE** est également disponible. Cette commande lancera le processus de sauvegarde et l'exécutera en arrière-plan.

## Exemple

```bash
127.0.0.1:6379> BGSAVE  
Background saving started
```