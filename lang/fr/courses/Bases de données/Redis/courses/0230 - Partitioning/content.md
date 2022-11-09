Le partitionnement est le processus qui consiste à diviser vos données en plusieurs instances Redis, de sorte que chaque instance ne contienne qu'un sous-ensemble de vos clés.

## Avantages du Partitioning

- Il permet de créer des bases de données beaucoup plus importantes, en utilisant la somme de la mémoire de plusieurs ordinateurs. Sans partitionnement, vous êtes limité à la quantité de mémoire qu'un seul ordinateur peut supporter.
- Il permet de faire évoluer la puissance de calcul vers plusieurs cœurs et plusieurs ordinateurs, et la bande passante du réseau vers plusieurs ordinateurs et adaptateurs de réseau.

## Inconvénients du Partitioning

- Les opérations impliquant plusieurs clés ne sont généralement pas prises en charge. Par exemple, vous ne pouvez pas effectuer l'intersection entre deux ensembles s'ils sont stockés dans les clés qui sont mappées à des instances Redis différentes.
- Les transactions Redis impliquant des clés multiples ne peuvent pas être utilisées.
- Le granulat de partitionnement est la clé, il n'est donc pas possible de partager un ensemble de données avec une seule clé énorme comme un très grand ensemble trié.
- Lorsque le partitionnement est utilisé, la manipulation des données est plus complexe. Par exemple, vous devez gérer plusieurs fichiers RDB/AOF, et pour obtenir une sauvegarde de vos données, vous devez agréger les fichiers de persistance de plusieurs instances et hôtes.
- L'ajout et la suppression de la capacité peuvent être complexes. Par exemple, Redis Cluster prend en charge le rééquilibrage le plus souvent transparent des données avec la possibilité d'ajouter et de supprimer des nœuds au moment de l'exécution. Cependant, d'autres systèmes comme le partitionnement côté client et les proxies ne prennent pas en charge cette fonctionnalité. Une technique appelée Presharding aide à cet égard.

## Types de Partitioning

Il y a deux types de partitionnement disponibles dans Redis. Supposons que nous ayons quatre instances Redis, R0, R1, R2, R3 et de nombreuses clés représentant des utilisateurs comme user:1, user:2, ... et ainsi de suite.

### Range Partitioning

Le partitionnement des plages est réalisé en faisant correspondre des plages d'objets à des instances Redis spécifiques. Supposons que dans notre exemple, les utilisateurs de l'ID 0 à l'ID 10000 iront dans l'instance R0, tandis que les utilisateurs de l'ID 10001 à l'ID 20000 iront dans l'instance R1 et ainsi de suite.

### Hash Partitioning

Dans ce type de partitionnement, une fonction de hachage (par exemple, la fonction modulus) est utilisée pour convertir la clé en un nombre, puis les données sont stockées dans des instances Redis différentes.