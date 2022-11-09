Redis est une source ouverte, un magasin avancé de valeurs clés et une solution appropriée pour la création d'applications web performantes et évolutives.

Redis a trois particularités principales qui le distinguent.

- Redis conserve sa base de données entièrement dans la mémoire, n'utilisant le disque que pour la persistance.
- Redis dispose d'un ensemble relativement riche de types de données par rapport à de nombreux magasins de données clé-valeur.
- Redis peut répliquer les données vers un nombre quelconque d'esclaves.

## Avantages de Redis

Voici certains avantages de Redis.

- **Exceptionnellement rapide** - Redis est très rapide et peut effectuer environ 110000 SETs par seconde, environ 81000 GETs par seconde.
- **Prise en charge de types de données riches** - Redis prend en charge de manière native la plupart des types de données que les développeurs connaissent déjà, tels que les listes, les ensembles, les ensembles triés et les hachages. Cela facilite la résolution d'une variété de problèmes, car nous savons quel problème peut être mieux traité par quel type de données.
- **Les opérations sont atomiques** - Toutes les opérations Redis sont atomiques, ce qui garantit que si deux clients accèdent simultanément, le serveur Redis recevra la valeur mise à jour.
- **Outil multi-utilité** - Redis est un outil multi-utilité et peut être utilisé dans un certain nombre de cas d'utilisation tels que la mise en cache, les files d'attente de messagerie (Redis supporte nativement le Publish/Subscribe), toutes les données à courte durée de vie dans votre application, telles que les sessions d'applications web, le nombre de hits de pages web, etc....

## Redis vs autres systèmes clé-valeur

- Redis représente un chemin d'évolution différent dans les bases de données clés-valeurs, où les valeurs peuvent contenir des types de données plus complexes, avec des opérations atomiques définies sur ces types de données.
- Redis est une base de données en mémoire mais persistante sur disque, ce qui représente un compromis différent où une très grande vitesse d'écriture et de lecture est atteinte avec la limitation des ensembles de données qui ne peuvent pas être plus grands que la mémoire.
- Un autre avantage des bases de données en mémoire est que la représentation en mémoire de structures de données complexes est beaucoup plus simple à manipuler que la même structure de données sur disque. Ainsi, Redis peut faire beaucoup avec peu de complexité interne.