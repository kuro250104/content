Les commandes du serveur Redis sont essentiellement utilisées pour gérer le serveur Redis.

## Exemple

L'exemple suivant explique comment nous pouvons obtenir toutes les statistiques et informations sur le serveur.

```bash
redis 127.0.0.1:6379> INFO  

# Server 
redis_version:2.8.13 
redis_git_sha1:00000000 
redis_git_dirty:0 
redis_build_id:c2238b38b1edb0e2 
redis_mode:standalone 
os:Linux 3.5.0-48-generic x86_64 
arch_bits:64 
multiplexing_api:epoll 
gcc_version:4.7.2 
process_id:3856 
run_id:0e61abd297771de3fe812a3c21027732ac9f41fe 
tcp_port:6379 
uptime_in_seconds:11554 
uptime_in_days:0 hz:10 
lru_clock:16651447 
config_file:  

# Clients 
connected_clients:1
client_longest_output_list:0 
client_biggest_input_buf:0 
blocked_clients:0  

# Memory 
used_memory:589016 
used_memory_human:575.21K 
used_memory_rss:2461696 
used_memory_peak:667312 
used_memory_peak_human:651.67K 
used_memory_lua:33792 
mem_fragmentation_ratio:4.18 
mem_allocator:jemalloc-3.6.0  

# Persistence 
loading:0 
rdb_changes_since_last_save:3 
rdb_bgsave_in_progress:0 
rdb_last_save_time:1409158561 
rdb_last_bgsave_status:ok 
rdb_last_bgsave_time_sec:0 
rdb_current_bgsave_time_sec:-1 
aof_enabled:0 
aof_rewrite_in_progress:0 
aof_rewrite_scheduled:0 
aof_last_rewrite_time_sec:-1 
aof_current_rewrite_time_sec:-1 
aof_last_bgrewrite_status:ok 
aof_last_write_status:ok  

# Stats 
total_connections_received:24 
total_commands_processed:294 
instantaneous_ops_per_sec:0 
rejected_connections:0 
sync_full:0 
sync_partial_ok:0 
sync_partial_err:0 
expired_keys:0 
evicted_keys:0 
keyspace_hits:41
keyspace_misses:82 
pubsub_channels:0 
pubsub_patterns:0 
latest_fork_usec:264  

# Replication 
role:master 
connected_slaves:0 
master_repl_offset:0 
repl_backlog_active:0 
repl_backlog_size:1048576 
repl_backlog_first_byte_offset:0 
repl_backlog_histlen:0  

# CPU 
used_cpu_sys:10.49 
used_cpu_user:4.96 
used_cpu_sys_children:0.00 
used_cpu_user_children:0.01  

# Keyspace 
db0:keys = 94,expires = 1,avg_ttl = 41638810 
db1:keys = 1,expires = 0,avg_ttl = 0 
db3:keys = 1,expires = 0,avg_ttl = 0 
```

## Commandes de Redis Server

Le tableau suivant liste quelques commandes de base liées au serveur Redis.

**Commande et description**

- ```BGREWRITEAOF``` - Réécrit de manière asynchrone le fichier "append-only".
- ```BGSAVE``` - Sauvegarde asynchrone de l'ensemble de données sur le disque.
- ```CLIENT KILL [ip:port] [ID client-id]``` - Tue la connexion d'un client
- ```CLIENT LIST``` - Obtient la liste des connexions du client au serveur.
- ```CLIENT GETNAME``` - Obtient le nom de la connexion actuelle
- ```CLIENT PAUSE timeout``` - Arrête de traiter les commandes des clients pendant une durée déterminée.
- ```CLIENT SETNAME connection-name``` - Définit le nom de la connexion actuelle
- ```CLUSTER SLOTS``` - Obtient un tableau de correspondance entre les nœuds et les emplacements de cluster.
- ```COMMAND``` - Obtient un tableau des détails de la commande Redis
- ```COMMAND COUNT``` - Obtient le nombre total de commandes Redis
- ```COMMAND GETKEYS``` - Extraction des clés à partir d'une commande Redis complète.
- ```BGSAVE``` - Sauvegarde asynchrone de l'ensemble de données sur le disque.
- ```COMMAND INFO command-name [command-name ...]``` - Obtient un tableau de détails de commandes Redis spécifiques.
- ```CONFIG GET parameter``` - Obtient la valeur d'un paramètre de configuration
- ```CONFIG REWRITE``` - Réécrit le fichier de configuration avec la configuration en mémoire.
- ```CONFIG SET parameter value``` - Définit un paramètre de configuration à la valeur donnée
- ```CONFIG RESETSTAT``` - Réinitialiser les statistiques retournées par INFO
- ```DBSIZE``` - Renvoie le nombre de clés dans la base de données sélectionnée.
- ```DEBUG OBJECT key``` - Obtient des informations de débogage sur une clé
- ```DEBUG SEGFAULT``` - Fait planter le serveur
- ```FLUSHALL``` - Supprime toutes les clés de toutes les bases de données
- ```FLUSHDB``` - Supprime toutes les clés de la base de données actuelle
- ```INFO [section]``` - Obtient des informations et des statistiques sur le serveur
- ```LASTSAVE``` - Obtient l'horodatage UNIX de la dernière sauvegarde réussie sur le disque.
- ```MONITOR``` - Écoute de toutes les demandes reçues par le serveur en temps réel.
- ```ROLE``` - Retourne le rôle de l'instance dans le contexte de la réplication.
- ```SAVE``` - Sauvegarde synchrone de l'ensemble de données sur le disque.
- ```SHUTDOWN [NOSAVE] [SAVE]``` - Enregistre de manière synchrone le jeu de données sur le disque et ferme ensuite le serveur.
- ```SLAVEOF host port``` - Makes the server a slave of another instance, or promotes it as a master
- ```SLOWLOG subcommand [argument]``` - Gère le journal des requêtes lentes de Redis
- ```SYNC``` - Commande utilisée pour la réplication
- ```TIME``` - Renvoie l'heure actuelle du serveur