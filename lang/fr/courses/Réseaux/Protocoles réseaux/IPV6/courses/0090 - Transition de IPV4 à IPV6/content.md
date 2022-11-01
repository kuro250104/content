La transition complète d'IPv4 à IPv6 peut ne pas être possible, car IPv6 n'est pas rétrocompatible. Il en résulte une situation dans laquelle soit un site est sous IPv6, soit il ne l'est pas. C'est différent de la mise en œuvre d'autres nouvelles technologies où la plus récente est rétrocompatible, de sorte que l'ancien système peut continuer à fonctionner avec la nouvelle version sans aucune modification supplémentaire.

Pour surmonter ce problème, nous disposons de quelques technologies qui peuvent être utilisées pour assurer une transition lente et en douceur d'IPv4 à IPv6.

## Routeurs à double pile

Un routeur peut être installé avec des adresses IPv4 et IPv6 configurées sur ses interfaces pointant vers le réseau du schéma IP pertinent.

![Routeurs à double pile](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV6/courses/0090%20-%20Transition%20de%20IPV4%20%C3%A0%20IPV6/images/image3.jpg)

Dans le schéma ci-dessus, un serveur ayant une adresse IPv4 et IPv6 configurée pour lui peut maintenant parler avec tous les hôtes sur les réseaux IPv4 et IPv6 à l'aide d'un routeur à double pile. Le routeur à double pile peut communiquer avec les deux réseaux. Il fournit un moyen pour les hôtes d'accéder à un serveur sans changer leurs versions IP respectives.

## Tunnellisation

Dans un scénario où différentes versions d'IP existent sur le chemin intermédiaire ou les réseaux de transit, la tunnellisation fournit une meilleure solution où les données de l'utilisateur peuvent passer par une version d'IP non supportée.

![Tunnellisation](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV6/courses/0090%20-%20Transition%20de%20IPV4%20%C3%A0%20IPV6/images/image1.jpg)

Le schéma ci-dessus montre comment deux réseaux IPv4 distants peuvent communiquer via un tunnel, lorsque le réseau de transit est en IPv6. L'inverse est également possible lorsque le réseau de transit est en IPv6 et que les sites distants qui veulent communiquer sont en IPv4.

## Traduction de protocole NAT

Il s'agit d'une autre méthode importante de transition vers IPv6 au moyen d'un dispositif NAT-PT (Network Address Translation - Protocol Translation). Avec l'aide d'un dispositif NAT-PT, il est possible de passer des paquets IPv4 aux paquets IPv6 et vice versa. Voir le schéma ci-dessous :

![Traduction de protocole NAT](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV6/courses/0090%20-%20Transition%20de%20IPV4%20%C3%A0%20IPV6/images/image2.jpg)

Un hôte doté d'une adresse IPv4 envoie une requête à un serveur Internet compatible IPv6 qui ne comprend pas l'adresse IPv4. Dans ce scénario, le dispositif NAT-PT peut les aider à communiquer. Lorsque l'hôte IPv4 envoie un paquet de requête au serveur IPv6, le dispositif NAT-PT/routeur dépouille le paquet IPv4, supprime l'en-tête IPv4, ajoute l'en-tête IPv6 et le fait passer par Internet. Lorsqu'une réponse du serveur IPv6 arrive pour l'hôte IPv4, le routeur fait l'inverse.