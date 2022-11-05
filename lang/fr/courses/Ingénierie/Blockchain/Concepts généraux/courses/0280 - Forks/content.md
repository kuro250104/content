Lorsque vous êtes invité à mettre à jour votre application bancaire numérique sur votre smartphone, vous n'y pensez probablement pas à deux fois. Peut-être que votre téléphone se met automatiquement à jour sans même que vous vous en rendiez compte. C'est un processus nécessaire, après tout - si vous n'installez pas la dernière version du logiciel, vous courez le risque de vous voir refuser l'accès à ses services.

Dans les crypto-monnaies à code source ouvert, les choses sont très différentes. Vous n'avez pas besoin de lire chaque ligne de code qui sous-tend le bitcoin pour l'utiliser, mais il est important d'avoir le choix de le faire. Vous voyez, il n'y a pas de hiérarchie ici, ni de banque qui peut simplement pousser des mises à jour et changer les choses à sa guise. Par conséquent, la mise en œuvre de nouvelles fonctionnalités dans les réseaux de blockchain peut être un défi.

Dans ce cours, nous allons explorer comment les réseaux de crypto-monnaies peuvent être mis à niveau, malgré l'absence d'une autorité centrale. Pour ce faire, ils utilisent deux mécanismes différents : les hard forks et les soft forks. 

## Qui prend les décisions dans un réseau blockchain ?

Pour comprendre le fonctionnement des forks, il est important de connaître d'abord les participants impliqués dans le processus de décision (ou gouvernance) du réseau.

Dans le cas de Bitcoin, on peut distinguer trois sous-ensembles de participants : les développeurs, les mineurs et les utilisateurs de nœuds complets. Ce sont les parties qui contribuent réellement au réseau. Les nœuds légers (c'est-à-dire les portefeuilles sur vos téléphones, ordinateurs portables, etc.) sont largement utilisés, mais ils ne sont pas vraiment des "participants" en ce qui concerne le réseau.

### Développeurs

Les développeurs sont responsables de la création et de la mise à jour du code. Pour votre pièce de monnaie typique, n'importe qui peut contribuer à ce processus. Le code est accessible au public, ce qui permet aux développeurs de soumettre des modifications à l'examen des autres développeurs. 

### Mineurs

Les mineurs sont ceux qui sécurisent le réseau. Ils exécutent le code de la crypto-monnaie et consacrent des ressources à l'ajout de nouveaux blocs à la blockchain. Dans le réseau Bitcoin, par exemple, ils le font par preuve de travail. Ils sont récompensés pour leurs efforts sous la forme d'une récompense par bloc.

### Utilisateurs de nœuds complets

Les nœuds complets sont l'épine dorsale du réseau de crypto-monnaies. Ils valident, envoient et reçoivent des blocs et des transactions et conservent une copie de la blockchain.

Vous trouverez souvent des chevauchements dans ces catégories. Vous pouvez, par exemple, être un développeur et un utilisateur de nœuds complets, ou un mineur et un utilisateur de nœuds complets. Vous pouvez être les trois ou aucun. En fait, beaucoup de ceux que nous considérons comme des utilisateurs de crypto-monnaies n'assument aucun de ces rôles. Au lieu de cela, ils choisissent d'utiliser des nœuds légers ou des services centralisés.

En regardant les descriptions ci-dessus, vous pourriez faire de solides arguments pour que les développeurs et les mineurs prennent les décisions pour le réseau. Les développeurs créent le code - sans eux, vous n'auriez pas de logiciel à exécuter et personne pour corriger les bugs ou ajouter de nouvelles fonctionnalités. Les mineurs sécurisent le réseau - sans une saine concurrence minière, la chaîne pourrait être détournée ou s'arrêter.

Toutefois, si ces deux catégories tentaient de forcer le reste du réseau à suivre leur volonté, cela ne se terminerait pas très bien. Pour beaucoup, le véritable pouvoir est concentré dans les nœuds complets. Cela est dû en grande partie au fait que le réseau est opt-in, ce qui signifie que les utilisateurs peuvent choisir les logiciels qu'ils utilisent. 

Les développeurs ne s'introduisent pas chez vous pour vous forcer à télécharger les binaires Bitcoin Core sous la menace d'une arme. Si les mineurs adoptent une attitude de type "c'est moi ou l'autoroute" pour imposer un changement non désiré aux utilisateurs, eh bien, les utilisateurs prendront l'autoroute. 

Ces parties ne sont pas des seigneurs tout-puissants, ce sont des fournisseurs de services. Si les gens décident de ne pas utiliser le réseau, la pièce perdra de sa valeur. Cette perte de valeur a un impact direct sur les mineurs (leurs récompenses ont moins de valeur lorsqu'elles sont libellées en dollars). Quant aux développeurs, ils peuvent simplement être ignorés par les utilisateurs.

Vous voyez, ce n'est pas comme si le logiciel était propriétaire. Vous pouvez faire les modifications que vous voulez et, si d'autres utilisent votre logiciel modifié, vous pouvez tous communiquer. Dans ce cas, vous bifurquez le logiciel et créez un nouveau réseau dans le processus.

## Qu'est-ce qu'un fork ?

Une bifurcation (*fork*) de logiciel se produit à un moment où le logiciel est copié et modifié. Le projet d'origine continue de vivre, mais il est désormais séparé du nouveau projet, qui prend une direction différente. Supposons que l'équipe de votre site Web de contenu sur les crypto-monnaies préféré ait un désaccord majeur sur la façon de procéder. Une partie de l'équipe pourrait répliquer le site sur un domaine différent. Mais à l'avenir, ils publieraient des types de contenu différents de ceux de l'original.

Les projets reposent sur un terrain commun et partagent une histoire. À l'instar d'une route unique qui se divise ensuite en deux, il existe désormais une divergence permanente entre leurs chemins.

Notez que ce genre de choses arrive souvent dans les projets open-source, et ce depuis longtemps, avant l'apparition du Bitcoin ou de l'Ethereum. Cependant, la distinction entre hard forks et soft forks est presque exclusive à l'espace blockchain. Nous allons en parler un peu plus.

## Hard forks vs. soft forks

Bien qu'elles portent des noms similaires et qu'elles aient le même objectif, les hard forks et les soft forks sont très différentes. Jetons un coup d'œil à chacune d'elles.

### Qu'est-ce qu'un hard fork ?

Les hard forks sont des mises à jour logicielles incompatibles avec le passé. Ils se produisent généralement lorsque des nœuds ajoutent de nouvelles règles d'une manière qui entre en conflit avec les règles des anciens nœuds. Les nouveaux nœuds ne peuvent communiquer qu'avec ceux qui exploitent la nouvelle version. En conséquence, la blockchain se divise, créant deux réseaux distincts : un avec les anciennes règles et un avec les nouvelles.

Il y a donc maintenant deux réseaux fonctionnant en parallèle. Ils continueront tous deux à propager des blocs et des transactions, mais ils ne travaillent plus sur la même blockchain. Tous les nœuds avaient une blockchain identique jusqu'au moment de la bifurcation (et cet historique est conservé), mais ils auront des blocs et des transactions différents par la suite.

En raison de cet historique partagé, vous vous retrouverez avec des pièces sur les deux réseaux si vous les déteniez avant le fork. Supposons que vous possédiez 5 BTC lorsqu'une bifurcation se produit au bloc 600 000. Vous avez pu dépenser ces 5 BTC sur l'ancienne chaîne dans le bloc 600 001, mais ils n'ont pas été dépensés dans le bloc 600 001 de la nouvelle blockchain. En supposant que la cryptographie n'ait pas changé, vos clés privées contiennent toujours cinq pièces sur le réseau bifurqué. 

Un exemple de hard fork est la bifurcation de 2017 qui a vu le bitcoin se fragmenter en deux chaînes distinctes - la chaîne originale, le bitcoin (BTC), et une nouvelle, le bitcoin cash (BCH). Le fork s'est produit après de nombreuses discussions sur la meilleure approche de la mise à l'échelle. Les partisans de Bitcoin Cash voulaient augmenter la taille des blocs, tandis que les partisans de Bitcoin s'opposaient à ce changement.

Une augmentation de la taille des blocs nécessite une modification des règles. C'était avant le soft fork SegWit (nous y reviendrons bientôt), les nœuds n'acceptaient donc que les blocs inférieurs à 1 Mo. Si vous créiez un bloc de 2 Mo qui était par ailleurs valide, les autres nœuds le rejetteraient quand même.

Seuls les nœuds ayant modifié leur logiciel pour autoriser les blocs de plus de 1 Mo pourraient accepter ces blocs. Bien entendu, cela les rendrait incompatibles avec la version précédente, de sorte que seuls les nœuds ayant subi les mêmes modifications de protocole pourraient communiquer.

### Qu'est-ce qu'un soft fork ?

Un soft fork est une mise à niveau rétrocompatible, ce qui signifie que les nœuds mis à niveau peuvent toujours communiquer avec les nœuds non mis à niveau. Ce que vous voyez généralement dans un soft fork est l'ajout d'une nouvelle règle qui n'entre pas en conflit avec les anciennes règles.

Par exemple, une diminution de la taille des blocs peut être mise en œuvre par soft-forking. Prenons une fois de plus l'exemple du bitcoin pour illustrer ce point : bien qu'il y ait une limite à la taille d'un bloc, il n'y a pas de limite à sa taille. Si vous souhaitez n'accepter que les blocs inférieurs à une certaine taille, il vous suffit de rejeter les blocs plus grands.

Cependant, cela ne vous déconnecte pas automatiquement du réseau. Vous communiquez toujours avec les nœuds qui n'appliquent pas ces règles, mais vous filtrez certaines des informations qu'ils vous transmettent.

Un bon exemple concret d'un soft fork est le fork Segregated Witness (SegWit) mentionné plus haut, qui s'est produit peu de temps après la séparation Bitcoin/Bitcoin Cash. SegWit était une mise à jour qui modifiait le format des blocs et des transactions, mais elle était habilement conçue. Les anciens nœuds pouvaient toujours valider les blocs et les transactions (le formatage n'enfreignait pas les règles), mais ils ne les comprenaient pas. Certains champs ne sont lisibles que lorsque les nœuds passent au logiciel le plus récent, qui leur permet d'analyser des données supplémentaires.

Même deux ans après l'activation de SegWit, tous les nœuds n'ont pas été mis à niveau. Il y a des avantages à le faire, mais il n'y a pas vraiment d'urgence puisqu'il n'y a pas de changement qui casse le réseau.

## Quelle est la meilleure solution ?

Fondamentalement, ces deux types de bifurcations ont des objectifs différents. Les bifurcations dures controversées peuvent diviser une communauté, mais les bifurcations planifiées offrent la liberté de modifier le logiciel avec l'accord de tous.

Les soft forks sont une option plus douce. En général, vous êtes plus limité dans ce que vous pouvez faire, car vos nouvelles modifications ne peuvent pas entrer en conflit avec les anciennes règles. Cela dit, si votre mise à jour peut être conçue de manière à rester compatible, vous n'avez pas à craindre de fragmenter le réseau.

## Conclusion

Les hard forks et soft forks sont essentiels au succès à long terme des réseaux blockchain. Ils nous permettent d'apporter des changements et des mises à niveau dans les systèmes décentralisés, malgré l'absence d'une autorité centrale.

Les forks permettent aux blockchains et aux crypto-monnaies d'intégrer de nouvelles fonctionnalités au fur et à mesure de leur développement. Sans ces mécanismes, nous aurions besoin d'un système centralisé avec un contrôle descendant. Sinon, nous serions coincés avec les mêmes règles pendant toute la durée de vie du protocole.