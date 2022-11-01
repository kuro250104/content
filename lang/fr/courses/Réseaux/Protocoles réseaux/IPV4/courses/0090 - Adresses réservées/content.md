Il existe quelques espaces d'adresses IPv4 réservés qui ne peuvent pas être utilisés sur l'internet. Ces adresses ont une fonction particulière et ne peuvent pas être acheminées en dehors du réseau local.

## Adresses IP privées

Chaque classe d'IP (A, B et C) comporte des adresses réservées en tant qu'adresses IP privées. Ces adresses IP peuvent être utilisées au sein d'un réseau, d'un campus, d'une entreprise et lui sont privées. Ces adresses ne peuvent pas être acheminées sur Internet, les paquets contenant ces adresses privées sont donc rejetés par les routeurs.

![Adresses IP privées](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0090%20-%20Adresses%20r%C3%A9serv%C3%A9es/images/image1.png)

Afin de communiquer avec le monde extérieur, ces adresses IP doivent être traduites en adresses IP publiques à l'aide d'un processus NAT ou d'un serveur proxy Web.

La création d'une gamme distincte d'adresses privées a pour seul but de contrôler l'attribution du pool d'adresses IPv4 déjà limité. L'utilisation d'une plage d'adresses privées au sein d'un réseau local a permis de réduire considérablement le besoin d'adresses IPv4 au niveau mondial. Cela a également permis de retarder l'épuisement des adresses IPv4.

La classe IP, lors de l'utilisation de la gamme d'adresses privées, peut être choisie en fonction de la taille et des besoins de l'organisation. Les grandes organisations peuvent choisir une gamme d'adresses IP privées de classe A, tandis que les petites organisations peuvent opter pour la classe C. Ces adresses IP peuvent être réparties en sous-réseaux et attribuées aux départements d'une organisation.

## Adresses IP de bouclage (loopback)

La plage d'adresses IP 127.0.0.0 - 127.255.255.255 est réservée au bouclage, c'est-à-dire à l'auto-adresse d'un hôte, également appelée adresse localhost. Cette adresse IP de bouclage est entièrement gérée par et dans le système d'exploitation. Les adresses de bouclage permettent aux processus serveur et client d'un même système de communiquer entre eux. Lorsqu'un processus crée un paquet dont l'adresse de destination est l'adresse de bouclage, le système d'exploitation le renvoie en boucle vers lui-même sans aucune interférence de la carte réseau.

Les données envoyées sur le loopback sont transmises par le système d'exploitation à une interface réseau virtuelle au sein du système d'exploitation. Cette adresse est principalement utilisée à des fins de test, comme l'architecture client-serveur sur une seule machine. En outre, si une machine hôte peut envoyer avec succès un ping à 127.0.0.1 ou à toute autre adresse IP de la plage de bouclage, cela signifie que la pile logicielle TCP/IP de la machine est chargée et fonctionne correctement.

## Adresses Link-local

Dans le cas où un hôte n'est pas en mesure d'acquérir une adresse IP auprès du serveur DHCP et qu'aucune adresse IP ne lui a été attribuée manuellement, l'hôte peut s'attribuer une adresse IP à partir d'une plage d'adresses Link-local réservées. Les adresses locales de liaison vont de 169.254.0.0 à 169.254.255.255.

Supposons un segment de réseau où tous les systèmes sont configurés pour acquérir des adresses IP à partir d'un serveur DHCP connecté au même segment de réseau. Si le serveur DHCP n'est pas disponible, aucun hôte du segment ne sera en mesure de communiquer avec un autre. Windows (98 ou version ultérieure) et Mac OS (8.0 ou version ultérieure) prennent en charge cette fonctionnalité d'autoconfiguration de l'adresse IP locale de liaison. En l'absence d'un serveur DHCP, chaque machine hôte choisit au hasard une adresse IP dans la plage mentionnée ci-dessus et vérifie ensuite, au moyen du protocole ARP, si un autre hôte ne s'est pas configuré avec la même adresse IP. Une fois que tous les hôtes utilisent des adresses locales de la même gamme, ils peuvent communiquer entre eux.

Ces adresses IP ne peuvent pas aider les systèmes à communiquer lorsqu'ils n'appartiennent pas au même segment physique ou logique. Ces adresses IP ne sont pas non plus routables.