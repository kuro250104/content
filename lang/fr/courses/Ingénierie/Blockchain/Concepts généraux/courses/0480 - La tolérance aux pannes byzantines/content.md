Depuis la création du bitcoin en 2008, en tant que système de monnaie électronique de pair à pair, de nombreuses autres crypto-monnaies ont été créées, chacune avec un mécanisme particulier. Mais une chose que presque toutes les crypto-monnaies ont en commun est la blockchain, comme élément central de leur architecture.

À quelques exceptions près, les blockchains sont intentionnellement conçues pour être décentralisées, fonctionnant comme un grand livre numérique qui est maintenu par un réseau distribué de nœuds informatiques. Pour cette raison, la technologie blockchain a permis la création de systèmes économiques sans confiance, où des transactions financières transparentes et fiables peuvent être exécutées sans intermédiaire. Les crypto-monnaies sont adoptées comme une alternative viable aux systèmes bancaires et de paiement traditionnels, qui dépendent fortement de la confiance.

Tout comme la plupart des systèmes informatiques distribués, les participants d'un réseau de crypto-monnaies doivent régulièrement se mettre d'accord sur l'état actuel de la blockchain, et c'est ce que nous appelons la réalisation du consensus. Cependant, l'obtention d'un consensus sur les réseaux distribués, de manière sûre et efficace, est loin d'être une tâche facile.

Ainsi, comment un réseau distribué de nœuds informatiques peut-il se mettre d'accord sur une décision, si certains des nœuds sont susceptibles d'échouer ou d'agir de manière malhonnête ? C'est la question fondamentale du problème dit des généraux byzantins, qui a donné naissance au concept de tolérance aux pannes byzantines.

## Quel est le problème des généraux byzantins ?

En quelques mots, le problème des généraux byzantins a été conçu en 1982 comme un dilemme logique illustrant comment un groupe de généraux byzantins peut avoir des problèmes de communication lorsqu'il tente de se mettre d'accord sur leur prochaine action.

Le dilemme suppose que chaque général a sa propre armée et que chaque groupe est situé à différents endroits autour de la ville qu'il a l'intention d'attaquer. Les généraux doivent se mettre d'accord pour attaquer ou battre en retraite. Peu importe qu'ils attaquent ou qu'ils se retirent, tant que tous les généraux parviennent à un consensus, c'est-à-dire qu'ils se mettent d'accord sur une décision commune afin de l'exécuter de manière coordonnée.

Par conséquent, nous pouvons considérer les exigences suivantes :

- Chaque général doit décider : attaquer ou battre en retraite (oui ou non) ;
- Une fois la décision prise, elle ne peut plus être modifiée ;
- Tous les généraux doivent se mettre d'accord sur la même décision et l'exécuter de manière synchronisée.

Les problèmes de communication susmentionnés sont liés au fait qu'un général ne peut communiquer avec un autre que par le biais de messages, qui sont transmis par un coursier. Par conséquent, le défi central du problème des généraux byzantins est que les messages peuvent être en quelque sorte retardés, détruits ou perdus.

En outre, même si un message est délivré avec succès, un ou plusieurs généraux peuvent choisir (pour une raison quelconque) d'agir malicieusement et d'envoyer un message frauduleux pour confondre les autres généraux, conduisant à un échec total.

Si nous appliquons ce dilemme au contexte des blockchains, chaque général représente un nœud de réseau, et les nœuds doivent parvenir à un consensus sur l'état actuel du système. En d'autres termes, la majorité des participants d'un réseau distribué doivent se mettre d'accord et exécuter la même action afin d'éviter un échec total.

Par conséquent, la seule façon d'obtenir un consensus dans ces types de systèmes distribués est d'avoir au moins ⅔ ou plus des nœuds de réseau fiables et honnêtes. Cela signifie que si la majorité du réseau décide d'agir de manière malveillante, le système est susceptible d'échouer et de subir des attaques (comme l'attaque des 51%).

## Tolérance aux pannes byzantine (BFT)

En quelques mots, la tolérance aux pannes byzantines (BFT - Byzantine Fault Tolerance) est la propriété d'un système qui est capable de résister à la classe de pannes dérivée du problème des généraux byzantins. Cela signifie qu'un système BFT est capable de continuer à fonctionner même si certains des nœuds tombent en panne ou agissent de manière malveillante. 

Il existe plus d'une solution possible au problème des généraux byzantins et, par conséquent, plusieurs façons de construire un système BFT. De même, il existe différentes approches pour qu'une blockchain atteigne la tolérance de panne byzantine, ce qui nous amène aux algorithmes dits de consensus.

## Algorithmes de consensus des blockchains

Nous pouvons définir un algorithme de consensus comme le mécanisme par lequel un réseau de blockchain atteint un consensus. Les implémentations les plus courantes sont Proof of Work (PoW) et Proof of Stake (PoS). Mais prenons le cas de Bitcoin comme exemple.

Alors que le protocole Bitcoin prescrit les règles primaires du système, l'algorithme de consensus PoW définit la manière dont ces règles seront suivies afin d'atteindre le consensus (par exemple, pendant la vérification et la validation des transactions).

Bien que le concept de preuve de travail soit plus ancien que les crypto-monnaies, Satoshi Nakamoto en a développé une version modifiée en tant qu'algorithme qui a permis la création du Bitcoin en tant que système BFT.

Notez que l'algorithme PoW n'est pas tolérant à 100% aux failles byzantines, mais en raison du processus de minage coûteux et des techniques cryptographiques sous-jacentes, PoW s'est avéré être l'une des implémentations les plus sûres et les plus fiables pour les réseaux blockchain. En ce sens, l'algorithme de consensus Proof of Work, conçu par Satoshi Nakamoto, est considéré par beaucoup comme l'une des solutions les plus géniales aux failles byzantines.

## Conclusion

Le problème des généraux byzantins est un dilemme intriguant qui a finalement donné naissance aux systèmes BFT, qui sont largement appliqués dans divers scénarios. Au-delà de l'industrie de la blockchain, quelques cas d'utilisation des systèmes BFT incluent les industries de l'aviation, de l'espace et de l'énergie nucléaire.

Dans le contexte des crypto-monnaies, un réseau de communication efficace et un bon mécanisme de consensus sont essentiels à tout écosystème de blockchain. La sécurisation de ces systèmes est un effort continu, et les algorithmes de consensus existants doivent encore surmonter quelques limitations (comme l'évolutivité). Néanmoins, PoW et PoS sont des approches très intéressantes en tant que systèmes BFT, et les applications potentielles inspirent certainement une innovation généralisée.