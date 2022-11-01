Dans le domaine des réseaux informatiques, le mode d'adressage désigne le mécanisme d'hébergement d'une adresse sur le réseau. L'IPv6 offre plusieurs types de modes par lesquels un hôte unique peut être adressé. Plusieurs hôtes peuvent être adressés en même temps ou l'hôte le plus proche peut être adressé.

## Unicast

En mode d'adressage unicast, une interface IPv6 (hôte) est identifiée de manière unique dans un segment de réseau. Le paquet IPv6 contient les adresses IP source et destination. Lorsqu'un commutateur réseau ou un routeur reçoit un paquet IP unicast, destiné à un seul hôte, il envoie une de ses interfaces sortantes qui se connecte à cet hôte particulier.

![Unicast](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV6/courses/0030%20-%20Modes%20d'adressage/images/image1.jpg)

## Multicast

Le mode multicast d'IPv6 est le même que celui d'IPv4. Le paquet destiné à plusieurs hôtes est envoyé à une adresse de multidiffusion spéciale. Tous les hôtes intéressés par cette information multicast doivent d'abord rejoindre ce groupe multicast. Toutes les interfaces qui ont rejoint le groupe reçoivent le paquet multicast et le traitent, tandis que les autres hôtes non intéressés par les paquets multicast ignorent les informations multicast.

![Multicast](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV6/courses/0030%20-%20Modes%20d'adressage/images/image2.jpg)

## Anycast

L'IPv6 a introduit un nouveau type d'adressage, appelé adressage Anycast. Dans ce mode d'adressage, plusieurs interfaces (hôtes) se voient attribuer la même adresse IP Anycast. Lorsqu'un hôte souhaite communiquer avec un hôte équipé d'une adresse IP Anycast, il envoie un message Unicast. Grâce à un mécanisme de routage complexe, ce message Unicast est livré à l'hôte le plus proche de l'expéditeur en termes de coût de routage.

![Anycast](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV6/courses/0030%20-%20Modes%20d'adressage/images/image3.jpg)

Prenons l'exemple des serveurs Web de microlead.fr, situés sur tous les continents. Supposons qu'une adresse IP unique IPv6 Anycast soit attribuée à tous les serveurs Web. Maintenant, lorsqu'un utilisateur d'Europe veut atteindre microlead.fr, le DNS pointe vers le serveur qui est physiquement situé en Europe même. Si un utilisateur d'Inde essaie d'atteindre microlead.fr, le DNS pointera alors vers le serveur Web physiquement situé en Asie. Les termes Nearest ou Closest sont utilisés en termes de coût de routage.

Dans l'image ci-dessus, lorsqu'un ordinateur client essaie d'atteindre un serveur, la demande est transmise au serveur dont le coût d'acheminement est le plus faible.