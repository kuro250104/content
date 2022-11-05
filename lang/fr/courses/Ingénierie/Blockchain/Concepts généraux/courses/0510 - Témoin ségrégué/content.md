## Qu'est-ce que SegWit ?

Témoin ségrégué (*SegWit - Segregated Witness*) est une mise à niveau du protocole développée en 2015. Le concept a été présenté comme une solution au problème de scalabilité auquel les réseaux blockchain étaient et sont encore confrontés aujourd'hui. 

En moyenne, le réseau Bitcoin valide un nouveau bloc toutes les 10 minutes, chacun contenant plusieurs transactions. En tant que telle, la taille du bloc affecte le nombre de transactions qui peuvent être confirmées dans chaque bloc. Actuellement, la blockchain Bitcoin peut traiter environ 7 transactions par seconde.

L'idée principale de SegWit est de réorganiser les données des blocs afin que les signatures ne soient plus placées avec les données de transaction. En d'autres termes, la mise à niveau SegWit consiste à séparer les témoins (signatures) des données de transaction. Cela permet de stocker davantage de transactions dans un seul bloc, ce qui augmente le débit de transactions du réseau.

En ne pouvant traiter qu'environ 7 transactions par seconde, une transaction Bitcoin peut parfois prendre beaucoup de temps à passer. C'est beaucoup plus lent que les solutions de paiement et les réseaux financiers classiques, qui peuvent traiter des milliers de transactions par seconde.

SegWit a été développé en 2015 par le développeur Bitcoin Pieter Wuille, avec d'autres contributeurs de Bitcoin Core. En août 2017, la mise à niveau SegWit a été mise en œuvre sous la forme d'un soft fork sur le réseau Bitcoin.

Aujourd'hui, plusieurs projets de crypto-monnaies utilisent SegWit, notamment Bitcoin et Litecoin. La mise à niveau du protocole a apporté de nombreux avantages, tels que l'amélioration de la vitesse des transactions et de la capacité des blocs. En outre, SegWit a permis de résoudre le bogue dit de "malléabilité des transactions" (voir ci-dessous).

## Quels sont les principaux avantages de SegWit ?

### Augmentation de la capacité

L'un des principaux avantages de SegWit est l'augmentation de la capacité des blocs. En supprimant les données de signature de l'entrée de la transaction, davantage de transactions peuvent être stockées dans un seul bloc.

Les transactions se composent de deux éléments principaux : les entrées et les sorties. Essentiellement, une entrée contient l'adresse publique de l'expéditeur, tandis que la sortie contient l'adresse publique du destinataire. Cependant, l'expéditeur doit prouver qu'il possède les fonds transférés, et il le fait au moyen d'une signature numérique.

Sans SegWit, les données de signature peuvent occuper jusqu'à 65 % d'un bloc. Avec SegWit, les données de signature sont éloignées de l'entrée de la transaction. La taille effective du bloc passe ainsi de 1 Mo à environ 4 Mo.

Notez que SegWit n'est pas une augmentation réelle de la taille des blocs. Il s'agit plutôt d'une solution technique permettant d'augmenter la taille effective des blocs sans avoir à augmenter la taille limite des blocs (ce qui nécessiterait un hard fork). Pour être plus précis, la taille réelle des blocs est toujours de 1 Mo, mais la taille limite effective des blocs est de 4 Mo.

SegWit a également introduit l'idée du poids des blocs. Nous pouvons considérer le poids des blocs comme un concept qui remplace l'idée de la taille des blocs. Essentiellement, le poids du bloc est une mesure qui inclut toutes les données du bloc, y compris les données de transaction (1 Mo) et les données de signature (jusqu'à 3 Mo), qui ne font plus partie du champ d'entrée.

### Augmentation de la vitesse des transactions

Avec un bloc qui peut stocker plus de transactions, SegWit a également la capacité d'augmenter la vitesse de transaction, puisqu'il peut y avoir une plus grande quantité de transactions se déplaçant dans la blockchain. Même si l'extraction d'un bloc prend le même temps, un plus grand nombre de transactions y sont traitées, de sorte que le taux de TPS est plus élevé.

L'augmentation de la vitesse des transactions a également contribué à réduire les coûts de transaction dans le réseau Bitcoin. Avant SegWit, il n'était pas rare de dépenser plus de 30 dollars par transaction. Cependant, SegWit a fait chuter ce coût de façon spectaculaire à moins d'un dollar par transaction.

### Correction de la falsification des transactions

L'un des problèmes majeurs du bitcoin était la possibilité d'altérer les signatures des transactions. Si une signature est altérée, une transaction entre deux parties peut être corrompue. Les données stockées sur les blockchains étant pratiquement immuables, les transactions invalides pouvaient être stockées de manière permanente sur la blockchain.

Avec SegWit, les signatures ne font plus partie des données de la transaction, ce qui supprime la possibilité d'altérer ces données. Cette correction a permis de nouvelles innovations au sein de la communauté blockchain, notamment des protocoles de deuxième couche et des contrats intelligents.

## SegWit et le réseau Lightning

Le développement de protocoles de deuxième couche a été partiellement rendu possible par la correction du bogue de la malléabilité des transactions. En termes simples, les protocoles de deuxième couche sont de nouvelles plateformes ou de nouveaux produits construits sur une blockchain, comme le bitcoin. L'un des protocoles de deuxième couche les plus populaires est le Lightning Network, un réseau de micropaiement hors chaîne.

Le Lightning Network est un protocole de deuxième couche qui fonctionne au-dessus du réseau Bitcoin. L'objectif principal du Lightning Network est de permettre la confirmation d'un plus grand nombre de transactions en un temps plus court, ce qui se traduit par des transactions plus rapides pour les utilisateurs. Les transactions sont collectées hors chaîne et mises en mémoire tampon pour être traitées par le réseau Bitcoin.

Le réseau Lightning a été initialement développé pour le bitcoin. Cependant, plusieurs autres projets de crypto-monnaies et de blockchain travaillent à la mise en œuvre de cette technologie pour leurs réseaux. Cela permettra non seulement de réduire le temps de confirmation des transactions, mais aussi de favoriser le développement de nouvelles solutions au problème de l'évolutivité.

## SegWit vs. SegWit2x

SegWit est une mise à jour "soft fork", ce qui signifie qu'elle est rétrocompatible. En d'autres termes, les nœuds Bitcoin qui ne sont pas mis à jour pour inclure SegWit sont toujours en mesure de traiter les transactions. Cependant, une autre implémentation de SegWit a été proposée, appelée SegWit2x (S2X), qui nécessiterait une mise à niveau par hard fork.

La principale différence entre SegWit et SegWit2x est que cette dernière n'aurait pas seulement inclus un changement dans le regroupement des transactions, mais aussi une augmentation de la taille des blocs (de 1MB à 2MB). Pourtant, une taille de bloc plus importante augmenterait la charge des opérateurs de nœuds et des mineurs, car il y aurait plus de données à traiter. 

Une autre différence notable est que la proposition SegWit a été soutenue et appliquée par la communauté Bitcoin. Cet épisode a donné naissance au concept d'UASF, qui signifie "user-activated soft fork".

En revanche, le SegWit2x proposait une modification substantielle de l'une des règles fondamentales régissant le bitcoin. Mais comme les développeurs n'ont pas pu parvenir à un consensus sur son adoption et sa mise en œuvre, le mouvement SegWit2x a finalement été suspendu.

## Nested SegWit vs. Native SegWit (bech32)

En bref, Native SegWit (également connu sous le nom de bech32) est une version actualisée de Nested SegWit. Le format bech32 offre une vitesse de transaction accrue, de meilleurs mécanismes de détection des erreurs et des frais de transaction encore plus bas. En outre, les adresses bech32 sont en minuscules, ce qui les rend plus faciles à lire.

Notez que les transactions de la blockchain entre des adresses non SegWit (Legacy), Nested SegWit et Native SegWit (bech32) sont entièrement compatibles. Cependant, tous les échanges et portefeuilles de crypto-monnaies ne prennent pas en charge SegWit. Il se peut donc que vous ne puissiez pas retirer des fonds directement sur une adresse SegWit.

## Conclusion

La mise en œuvre de SegWit a marqué la plus grande mise à niveau protocolaire de Bitcoin, et le fait qu'elle ait été soutenue et mise en œuvre par la communauté décentralisée la rend encore plus intéressante.

L'introduction de SegWit a constitué une avancée majeure dans la résolution de nombreux problèmes liés à Bitcoin et à d'autres réseaux blockchain - notamment en ce qui concerne la scalabilité. Grâce à la combinaison de SegWit et des protocoles de deuxième couche, les réseaux blockchain peuvent gérer un plus grand nombre de transactions, avec une efficacité accrue et des coûts réduits.

Bien qu'il s'agisse d'une solution puissante et innovante, SegWit n'a pas encore été pleinement adopté. Actuellement, le pourcentage d'adresses Bitcoin utilisant SegWit est d'environ 53 %.