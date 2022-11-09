Le Sharding est le processus de stockage des enregistrements de données sur plusieurs machines et c'est l'approche de MongoDB pour répondre aux exigences de la croissance des données. Au fur et à mesure que la taille des données augmente, une seule machine peut ne pas être suffisante pour stocker les données et fournir un débit de lecture et d'écriture acceptable. Le sharding résout le problème de la mise à l'échelle horizontale. Avec le sharding, vous ajoutez des machines supplémentaires pour prendre en charge la croissance des données et les demandes d'opérations de lecture et d'écriture.

## Pourquoi Sharding ?

- Dans la réplication, toutes les écritures vont vers le nœud maître.
- Les requêtes sensibles à la latence vont toujours au maître
- Un seul ensemble de répliques est limité à 12 nœuds.
- La mémoire n'est pas assez grande lorsque le jeu de données actif est important.
- Le disque local n'est pas assez grand
- La mise à l'échelle verticale est trop coûteuse

## Sharding dans MongoDB

Dans le Sharding dans MonggoDB, il y a trois composants principaux -

- **Shards** − Les shards sont utilisés pour stocker les données. Ils assurent la haute disponibilité et la cohérence des données. Dans un environnement de production, chaque shard est un jeu de répliques distinct.
- **Config Servers** − Les serveurs de configuration stockent les métadonnées du cluster. Ces données contiennent un mappage de l'ensemble des données du cluster vers les shards. Le routeur de requêtes utilise ces métadonnées pour cibler les opérations sur des shards spécifiques. Dans un environnement de production, les clusters sharded ont exactement 3 serveurs de configuration.
- **Query Routers** − Les routeurs de requêtes sont essentiellement des instances mongo, qui s'interfacent avec les applications clientes et dirigent les opérations vers le shard approprié. Le routeur de requêtes traite et cible les opérations vers les shards, puis renvoie les résultats aux clients. Un cluster sharded peut contenir plus d'un routeur de requêtes pour diviser la charge des demandes des clients. Un client envoie des demandes à un routeur de requêtes. Généralement, un cluster sharded possède de nombreux routeurs de requêtes.