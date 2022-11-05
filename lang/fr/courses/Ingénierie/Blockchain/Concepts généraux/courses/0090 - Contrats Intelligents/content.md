Nick Szabo a décrit pour la première fois les contrats intelligents dans les années 1990. À l'époque, il définissait un contrat intelligent comme un outil qui formalise et sécurise les réseaux informatiques en combinant des protocoles et des interfaces utilisateur.

Szabo a évoqué l'utilisation potentielle des contrats intelligents dans divers domaines impliquant des accords contractuels, tels que les systèmes de crédit, le traitement des paiements et la gestion des droits sur les contenus.

Dans le monde des crypto-monnaies, on peut définir un contrat intelligent comme une application ou un programme qui fonctionne sur une blockchain. Typiquement, ils fonctionnent comme un accord numérique qui est appliqué par un ensemble spécifique de règles. Ces règles sont prédéfinies par un code informatique, qui est répliqué et exécuté par tous les nœuds du réseau.

Les contrats intelligents de la blockchain permettent la création de protocoles sans confiance. Cela signifie que deux parties peuvent prendre des engagements via la blockchain, sans avoir à se connaître ou à se faire confiance. Elles peuvent être sûres que si les conditions ne sont pas remplies, le contrat ne sera pas exécuté. En outre, l'utilisation de contrats intelligents peut supprimer le besoin d'intermédiaires, ce qui réduit considérablement les coûts opérationnels.

Bien que le protocole Bitcoin prenne en charge les contrats intelligents depuis de nombreuses années, ceux-ci ont été popularisés par le créateur et cofondateur d'Ethereum, Vitalik Buterin. Il convient toutefois de noter que chaque blockchain peut présenter une méthode différente de mise en œuvre des smart contracts. 

Cet article se concentrera sur les contrats intelligents qui fonctionnent sur la machine virtuelle Ethereum (*EVM - Ethereum Virtual Machine*), qui est une partie essentielle de la blockchain Ethereum.

## Comment fonctionnent-ils ?

En termes simples, un contrat intelligent fonctionne comme un programme déterministe. Il exécute une tâche particulière lorsque certaines conditions sont remplies. En tant que tel, un système de contrat intelligent suit souvent des instructions du type "si... alors...". Mais malgré la terminologie populaire, les contrats intelligents ne sont pas des contrats légaux, ni intelligents. Ils ne sont qu'un morceau de code exécuté sur un système distribué (blockchain).

Sur le réseau Ethereum, les contrats intelligents sont chargés d'exécuter et de gérer les opérations de la blockchain qui ont lieu lorsque les utilisateurs (adresses) interagissent entre eux. Toute adresse qui n'est pas un contrat intelligent est appelée un compte appartenant à un tiers (EOA - Externally Owned Account). Ainsi, les contrats intelligents sont contrôlés par le code informatique, et les EOA sont contrôlés par les utilisateurs.

Fondamentalement, les contrats intelligents Ethereum sont constitués d'un code de contrat et de deux clés publiques. La première clé publique est celle fournie par le créateur du contrat. L'autre clé représente le contrat lui-même, agissant comme un identifiant numérique unique pour chaque contrat intelligent.

Le déploiement de tout contrat intelligent se fait par le biais d'une transaction blockchain, et ils ne peuvent être activés que lorsqu'ils sont appelés par une EOA (ou par d'autres contrats intelligents). Cependant, le premier déclenchement est toujours provoqué par une EOA (utilisateur).

## Caractéristiques principales

Un smart contract Ethereum présente souvent les caractéristiques suivantes :

- **Distribué**. Les smart contracts sont répliqués et distribués dans tous les nœuds du réseau Ethereum. C'est l'une des principales différences avec les autres solutions qui sont basées sur des serveurs centralisés.
- **Déterministes**. Les contrats intelligents n'effectuent que les actions pour lesquelles ils ont été conçus, à condition que les conditions soient remplies. En outre, le résultat sera toujours le même, quelle que soit la personne qui les exécute.
- **Autonomes**. Les contrats intelligents peuvent automatiser toutes sortes de tâches, fonctionnant comme un programme auto-exécutable. Dans la plupart des cas, cependant, si un contrat intelligent n'est pas déclenché, il reste "dormant" et n'effectue aucune action.
- **Immuable**. Les contrats intelligents ne peuvent pas être modifiés après leur déploiement. Ils ne peuvent être "supprimés" que si une fonction particulière a été mise en œuvre précédemment. Ainsi, nous pouvons dire que les contrats intelligents peuvent fournir un code inviolable.
- **Personnalisables**. Avant le déploiement, les contrats intelligents peuvent être codés de nombreuses façons différentes. Ainsi, ils peuvent être utilisés pour créer de nombreux types d'applications décentralisées (DApps). Ceci est lié au fait qu'Ethereum est une blockchain complète de Turing.
- **Sans confiance**. Deux parties ou plus peuvent interagir via des contrats intelligents sans se connaître ni se faire confiance. En outre, la technologie blockchain garantit l'exactitude des données.
- **Transparent**. Les contrats intelligents étant basés sur une blockchain publique, leur code source est non seulement immuable mais également visible par tous.

## Peut-on modifier ou supprimer un contrat intelligent ?

Il est impossible d'ajouter de nouvelles fonctions à un contrat intelligent Ethereum après son déploiement. Toutefois, si son créateur inclut une fonction appelée SELFDESTRUCT dans le code, il est en mesure de "supprimer" le contrat intelligent à l'avenir - et de le remplacer par un nouveau contrat. En revanche, si la fonction n'est pas incluse dans le code au préalable, il ne sera pas en mesure de le supprimer.

Les contrats intelligents évolutifs permettent notamment aux développeurs d'avoir plus de flexibilité quant à l'immuabilité des contrats. Il existe de nombreuses façons de créer des contrats intelligents évolutifs, avec des degrés de complexité variables.

Prenons un exemple simplifié : imaginons qu'un contrat intelligent soit divisé en plusieurs petits contrats. Certains d'entre eux sont conçus pour être immuables, tandis que d'autres ont la fonction "supprimer" activée. Cela signifie qu'une partie du code (contrats intelligents) peut être supprimée et remplacée, tandis que d'autres fonctionnalités restent intactes.

## Avantages et cas d'utilisation

En tant que code programmable, les contrats intelligents sont hautement personnalisables et peuvent être conçus de nombreuses manières différentes, offrant de nombreux types de services et de solutions.

En tant que programmes décentralisés et auto-exécutables, les contrats intelligents peuvent offrir une transparence accrue et réduire les coûts opérationnels. En fonction de leur mise en œuvre, ils peuvent également accroître l'efficacité et réduire les dépenses bureaucratiques.

Les contrats intelligents sont particulièrement utiles dans les situations qui impliquent le transfert ou l'échange de fonds entre deux ou plusieurs parties.

En d'autres termes, les contrats intelligents peuvent être conçus pour une grande variété de cas d'utilisation. Parmi les exemples, citons la création d'actifs tokenisés, de systèmes de vote, de portefeuilles de crypto-monnaies, d'échanges décentralisés, de jeux et d'applications mobiles. Ils peuvent également être déployés avec d'autres solutions blockchain qui s'attaquent aux domaines des soins de santé, de la charité, de la chaîne d'approvisionnement, de la gouvernance et de la finance décentralisée (DeFi).

## Limites

Les contrats intelligents sont constitués de code informatique écrit par des humains. Cela comporte de nombreux risques, car le code est sujet à des vulnérabilités et à des bogues. Idéalement, ils devraient être écrits et déployés par des programmeurs expérimentés, surtout lorsqu'ils impliquent des informations sensibles ou de grosses sommes d'argent.

Par ailleurs, certains affirment que les systèmes centralisés peuvent fournir la plupart des solutions et des fonctionnalités offertes par les contrats intelligents. La principale différence est que les contrats intelligents fonctionnent sur un réseau P2P distribué, plutôt que sur un serveur centralisé. Et comme ils sont basés sur un système de blockchain, ils ont tendance à être soit immuables, soit très difficiles à modifier.

Être immuable peut être génial dans certaines situations, mais très mauvais dans d'autres. Par exemple, lorsqu'une organisation autonome décentralisée (DAO - Decentralized Autonomous Organization) appelée "The DAO" a été piratée en 2016, des millions d'éther (ETH) ont été volés en raison de failles dans le code de leur contrat intelligent.

Comme leur smart contract était immuable, les développeurs étaient incapables de corriger le code. Cela a finalement conduit à un hard fork, donnant naissance à une deuxième chaîne Ethereum. En termes simples, une chaîne a "annulé" le piratage et rendu les fonds à leurs propriétaires légitimes (cela fait partie de la blockchain Ethereum actuelle). L'autre chaîne a décidé de ne pas intervenir dans le piratage, déclarant que les choses qui se produisent sur une blockchain ne devraient jamais être modifiées (cette chaîne est maintenant appelée Ethereum Classic).

Il est important de noter que le problème ne vient pas de la blockchain Ethereum. Il a plutôt été causé par une mise en œuvre défectueuse du contrat intelligent.

Une autre limite des contrats intelligents est liée à leur statut juridique incertain. Non seulement parce qu'il s'agit d'une zone grise dans la plupart des pays, mais aussi parce que les contrats intelligents ne sont pas adaptés au cadre juridique actuel.

Par exemple, de nombreux contrats exigent que les deux parties soient correctement identifiées et âgées de plus de 18 ans. Le pseudonymat fourni par la technologie blockchain, combiné à l'absence d'intermédiaires, peut menacer ces exigences. Bien qu'il existe des solutions potentielles à ce problème, l'applicabilité juridique des contrats intelligents est un véritable défi - surtout lorsqu'il s'agit de réseaux distribués et sans frontières.

## Critique

Certains enthousiastes de la blockchain voient dans les contrats intelligents une solution qui remplacera et automatisera bientôt une grande partie de nos systèmes commerciaux et bureaucratiques. Bien que ce soit une réalité possible, c'est probablement loin de devenir la norme.

Les contrats intelligents sont certainement un élément intéressant de la technologie. Mais le fait qu'ils soient distribués, déterministes, transparents et quelque peu immuables peut les rendre moins attrayants dans certaines situations.

La critique s'appuie essentiellement sur le fait que les contrats intelligents ne constituent pas une solution adaptée à de nombreux problèmes du monde réel. En fait, certaines organisations ont intérêt à utiliser des solutions conventionnelles basées sur des serveurs. 

Comparés aux contrats intelligents, les serveurs centralisés sont plus faciles et moins chers à entretenir, et tendent à présenter une plus grande efficacité en termes de vitesse et de communication inter-réseaux (interopérabilité).

## Conclusion

Il ne fait aucun doute que les contrats intelligents ont causé un grand impact dans le monde des crypto-monnaies, et ils ont certainement révolutionné l'espace blockchain. Bien que les utilisateurs finaux n'interagissent peut-être pas directement avec les contrats intelligents, ceux-ci sont susceptibles d'alimenter un large éventail d'applications à l'avenir, allant des services financiers à la gestion de la chaîne d'approvisionnement.

Ensemble, les contrats intelligents et la blockchain ont le potentiel de perturber presque tous les domaines de notre société. Mais seul le temps nous dira si ces technologies révolutionnaires parviendront à surmonter les nombreux obstacles à leur adoption à grande échelle.