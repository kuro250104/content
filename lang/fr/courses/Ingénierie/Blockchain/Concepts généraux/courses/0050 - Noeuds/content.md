La définition d'un nœud (*Node*) peut varier en fonction du contexte. Lorsqu'il s'agit de réseaux informatiques ou de télécommunications, les nœuds peuvent agir soit comme un point de redistribution, soit comme un point final de communication. En général, un nœud consiste en un dispositif de réseau physique, mais il existe des cas où des nœuds virtuels sont utilisés.

Un nœud de réseau est un point où un message peut être créé, reçu ou transmis. Nous aborderons ici les différents types de nœuds Bitcoin : les nœuds complets, les super-nœuds, les nœuds mineurs et les clients SPV.

## Nœuds Bitcoin

Dans le contexte des blockchains, qui sont conçues comme des systèmes distribués, le réseau de nœuds informatiques est ce qui permet au bitcoin d'être utilisé comme une monnaie numérique décentralisée de pair à pair (P2P). En tant que telle, elle est résistante à la censure et ne nécessite pas d'intermédiaire pour les transactions entre utilisateurs (quelle que soit la distance qui les sépare dans le monde).

Par conséquent, les nœuds de la blockchain sont chargés d'agir comme un point de communication qui peut remplir différentes fonctions. Tout ordinateur ou appareil qui se connecte à l'interface Bitcoin peut être considéré comme un nœud dans le sens où il communique d'une manière ou d'une autre avec les autres. Ces nœuds sont également capables de transmettre des informations sur les transactions et les blocs au sein du réseau distribué d'ordinateurs en utilisant le protocole Bitcoin peer-to-peer. Cependant, chaque nœud informatique est défini en fonction de ses fonctions particulières, il existe donc différents types de nœuds Bitcoin.

## Noeuds complets

Les nœuds complets sont ceux qui soutiennent et assurent réellement la sécurité de Bitcoin, et ils sont indispensables au réseau. Ces nœuds peuvent également être appelés nœuds de validation complète car ils s'engagent dans le processus de vérification des transactions et des blocs par rapport aux règles de consensus du système. En outre, les nœuds complets sont capables de relayer les nouvelles transactions et les nouveaux blocs vers la blockchain. 

Habituellement, un nœud complet télécharge une copie de la blockchain Bitcoin avec chaque bloc et chaque transaction, mais ce n'est pas une obligation pour être considéré comme un nœud complet (une copie réduite de la blockchain peut être utilisée à la place).

Un nœud Bitcoin complet peut être établi par différentes implémentations logicielles, mais la plus utilisée et la plus populaire est le Bitcoin Core. Voici la configuration minimale requise pour faire fonctionner un nœud complet Bitcoin Core :

- Ordinateur de bureau ou portable avec une version récente de Windows, Mac OS X ou Linux.
- 200 Go d'espace disque disponible.
- 2 Go de mémoire (RAM).
- Une connexion Internet à haut débit avec une vitesse de téléchargement d'au moins 50 kB/s.
- Une connexion non mesurée ou une connexion avec des limites de téléchargement élevées. Les nœuds complets en ligne peuvent atteindre ou dépasser une utilisation en amont de 200 Go/mois et une utilisation en aval de 20 Go/mois. Vous devrez également télécharger ~200 Go lorsque vous démarrez votre nœud complet.
- Votre nœud complet doit fonctionner au moins 6 heures par jour. Encore mieux si vous le faites fonctionner en continu (24/7).

De nombreuses organisations et utilisateurs bénévoles font fonctionner des nœuds Bitcoin complets afin d'aider l'écosystème Bitcoin. En 2018, il y a environ 9 700 nœuds publics fonctionnant sur le réseau Bitcoin. Notez que ce nombre ne comprend que les nœuds publics, qui font référence aux nœuds Bitcoin visibles et accessibles (alias nœuds d'écoute). 

Outre les nœuds publics, il existe de nombreux autres nœuds cachés qui ne sont pas visibles (nœuds non écoutants). Ces nœuds fonctionnent généralement derrière un pare-feu, via des protocoles cachés comme Tor, ou simplement parce qu'ils ont été configurés pour ne pas écouter les connexions.

## Nœuds d'écoute (super-nœuds)

Essentiellement, un nœud d'écoute ou super nœud est un nœud complet qui est publiquement visible. Il communique et fournit des informations à tout autre nœud qui décide d'établir une connexion avec lui. Par conséquent, un super nœud est essentiellement un point de redistribution qui peut agir à la fois comme une source de données et comme un pont de communication. 

Un super nœud fiable fonctionne généralement 24 heures sur 24 et 7 jours sur 7 et possède plusieurs connexions établies, transmettant l'historique de la blockchain et les données des transactions à plusieurs nœuds dans le monde. Pour cette raison, un super nœud nécessitera probablement une plus grande puissance de calcul et une meilleure connexion Internet par rapport à un nœud complet qui est caché.

## Nœuds de mineurs

Pour pouvoir extraire des bitcoins dans le contexte concurrentiel actuel, il faut investir dans du matériel et des programmes miniers spécialisés. Ces programmes miniers (logiciels) ne sont pas directement liés au Bitcoin Core et sont exécutés en parallèle pour tenter de miner des blocs de bitcoins. Un mineur peut choisir de travailler seul (mineur solo) ou en groupe (mineur en pool). 

Alors que les nœuds complets des mineurs solo utilisent leur propre copie de la blockchain, les mineurs en pool travaillent ensemble, chacun contribuant à ses propres ressources de calcul (hashpower). Dans un pool minier, seul l'administrateur du pool est tenu de faire fonctionner un nœud complet - que l'on peut appeler le nœud complet d'un mineur de pool.

## Clients légers ou SPV

Également connus sous le nom de clients de vérification de paiement simplifié (*SPV - Simplified Payment Verification*), les clients légers sont ceux qui utilisent le réseau Bitcoin mais n'agissent pas vraiment comme un nœud à part entière. Par conséquent, les clients SPV ne contribuent pas à la sécurité du réseau car ils ne conservent pas de copie de la blockchain et ne participent pas au processus de vérification et de validation des transactions. 

En bref, le SPV est la méthode par laquelle un utilisateur peut vérifier si certaines transactions ont été incluses ou non dans un bloc, sans avoir à télécharger l'ensemble des données du bloc. Ainsi, les clients SPV s'appuient sur les informations fournies par d'autres nœuds complets (supernodes). Les clients légers fonctionnent comme des points de terminaison de communication et sont utilisés par de nombreux portefeuilles de crypto-monnaies.

## Client et nœuds d'extraction

Il est important de noter que l'exécution d'un nœud complet n'est pas la même chose que l'exécution d'un nœud minier complet. Alors que les mineurs doivent investir dans du matériel et des logiciels de minage coûteux, n'importe qui est capable de faire fonctionner un nœud de validation complet. 

Avant d'essayer de miner un bloc, un mineur doit rassembler les transactions en attente qui ont été précédemment acceptées comme valides par les nœuds complets. Ensuite, le mineur crée un bloc candidat (avec un groupe de transactions) et tente d'exploiter ce bloc. Si un mineur parvient à trouver une solution valide pour son bloc candidat, il la diffuse sur le réseau afin que les autres nœuds complets puissent vérifier la validité du bloc. Par conséquent, les règles de consensus sont déterminées et sécurisées par le réseau distribué de nœuds de validation et non par les mineurs.

## Conclusion

Les nœuds Bitcoin communiquent entre eux par le biais du protocole de réseau P2P Bitcoin et, ce faisant, ils garantissent l'intégrité du système. Un nœud qui se comporte mal ou qui tente de propager des informations incorrectes est rapidement reconnu par les nœuds honnêtes et est déconnecté du réseau.

Bien que l'exécution d'un nœud de validation complète ne fournisse pas de récompenses financières, elle est fortement recommandée car elle apporte confiance, sécurité et confidentialité aux utilisateurs. Les nœuds complets garantissent que les règles sont respectées. Ils protègent la blockchain contre les attaques et les fraudes (telles que les doubles dépenses). En outre, un nœud complet n'a pas besoin de faire confiance aux autres, et il permet à l'utilisateur d'avoir un contrôle total sur son argent.