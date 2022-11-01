On dit de cette époque qu'elle est l'ère des ordinateurs. Les ordinateurs ont considérablement changé notre mode de vie. Un appareil informatique, lorsqu'il est connecté à un ou plusieurs autres appareils informatiques, nous permet de partager des données et des informations à la vitesse de l'éclair.

## Qu'est-ce qu'un réseau ?

Dans le monde de l'informatique, un réseau est un ensemble d'hôtes interconnectés, via un support partagé qui peut être câblé ou sans fil. Un réseau informatique permet à ses hôtes de partager et d'échanger des données et des informations sur le support. Le réseau peut être un réseau local couvrant un bureau, un réseau métropolitain couvrant une ville ou un réseau étendu couvrant des villes et des provinces.

Un réseau informatique peut être aussi simple que deux PC reliés entre eux par un simple câble en cuivre ou peut atteindre une complexité telle que tous les ordinateurs du monde sont reliés entre eux, ce qu'on appelle l'Internet. Un réseau comprend alors de plus en plus de composants pour atteindre son objectif ultime d'échange de données. Voici une brève description des composants impliqués dans un réseau informatique :

- **Hôtes** (*Hosts*) - On dit que les hôtes sont situés à l'extrémité ultime du réseau, c'est-à-dire qu'un hôte est une source d'information et qu'un autre hôte en sera la destination. Les informations circulent de bout en bout entre les hôtes. Un hôte peut être le PC d'un utilisateur, un serveur Internet, un serveur de base de données, etc.
- **Support** (*Media*) - Si le réseau est câblé, il peut s'agir d'un câble en cuivre, d'un câble en fibre optique ou d'un câble coaxial. S'il est sans fil, il peut s'agir d'une fréquence radio libre ou d'une bande sans fil spéciale. Les fréquences sans fil peuvent également être utilisées pour interconnecter des sites distants.
- **Concentrateur** (*Hub*) - Un concentrateur est un répéteur multiport et il est utilisé pour connecter les hôtes dans un segment de réseau local. En raison des faibles débits, les concentrateurs sont désormais rarement utilisés. Le concentrateur fonctionne sur la couche 1 (couche physique) du modèle OSI.
- **Commutateur** (*Switch*) - Un commutateur est un pont multiport utilisé pour connecter les hôtes d'un segment de réseau local. Les commutateurs sont beaucoup plus rapides que les concentrateurs et fonctionnent à la vitesse du fil. Les commutateurs fonctionnent sur la couche 2 (couche liaison de données), mais des commutateurs de la couche 3 (couche réseau) sont également disponibles.
- **Routeur** (*Router*) - Un routeur est un dispositif de la couche 3 (couche réseau) qui prend des décisions de routage pour les données/informations envoyées vers une destination distante. Les routeurs constituent le cœur de tout réseau interconnecté et de l'Internet.
- **Passerelles** (*Gateways*) - Un logiciel ou une combinaison de logiciels et de matériels mis ensemble, fonctionne pour échanger des données entre des réseaux qui utilisent différents protocoles pour partager des données.
- **Pare**-feu (*Firewall*) - Logiciel ou combinaison de logiciels et de matériel, utilisé pour protéger les données des utilisateurs contre les destinataires involontaires sur le réseau/Internet.

__Remarques__ : Tous les composants d'un réseau servent en fin de compte les hôtes.

## Adressage des hôtes

La communication entre les hôtes ne peut avoir lieu que s'ils peuvent s'identifier sur le réseau. Dans un domaine de collision unique (où chaque paquet envoyé sur le segment par un hôte est entendu par tous les autres hôtes), les hôtes peuvent communiquer directement via l'adresse MAC.

L'adresse MAC est une adresse matérielle de 48 bits codée en usine qui peut également identifier un hôte de manière unique. Mais si un hôte veut communiquer avec un hôte distant, c'est-à-dire qui ne se trouve pas dans le même segment ou qui n'est pas logiquement connecté, il faut un moyen d'adressage pour identifier l'hôte distant de manière unique. Une adresse logique est attribuée à tous les hôtes connectés à Internet et cette adresse logique est appelée **adresse de protocole Internet** (*Internet Protocol Address*).