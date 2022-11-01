La hiérarchie du protocole Internet contient plusieurs classes d'adresses IP à utiliser efficacement dans diverses situations en fonction des besoins des hôtes par réseau. En gros, le système d'adressage IPv4 est divisé en cinq classes d'adresses IP. Ces cinq classes sont identifiées par le premier octet de l'adresse IP.

__Remarque__ : **L'Internet Corporation for Assigned Names and Numbers (ICAN)** est responsable de l'attribution des adresses IP.

Le premier octet mentionné ici est le plus à gauche de tous. Les octets sont numérotés comme suit, selon la notation décimale en pointillés de l'adresse IP.

![Décomposition d'une adresse IP](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0060%20-%20Classes%20d'adresse/images/image5.png)

Le nombre de réseaux et le nombre d'hôtes par classe peuvent être déduits par la formule suivante :

![Formule de déduction de nombre d'hôtes et de réseaux par classe](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0060%20-%20Classes%20d'adresse/images/image6.png)

Lors du calcul des adresses IP des hôtes, 2 adresses IP sont diminuées car elles ne peuvent pas être attribuées aux hôtes, c'est-à-dire que la première IP d'un réseau est le numéro du réseau et la dernière IP est réservée à l'IP de diffusion.

## Adresse de classe A

Le premier bit du premier octet est toujours fixé à 0 (zéro). Ainsi, le premier octet va de 1 à 127, soit :

![Premier bit du premier octet fixé à 0](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0060%20-%20Classes%20d'adresse/images/image4.png)

Les adresses de classe A comprennent uniquement les IP commençant par 1.x.x.x à 126.x.x.x uniquement. La plage IP 127.x.x.x est réservée aux adresses IP de bouclage.

Le masque de sous-réseau par défaut pour une adresse IP de classe A est 255.0.0.0, ce qui implique que l'adressage de classe A peut avoir 126 réseaux (27-2) et 16777214 hôtes (224-2).

Le format de l'adresse IP de classe A est donc ```0NNNNN.HHHHHHHH.HHHHHHH.HHHHHHHHH```

## Adresse de classe B

Une adresse IP qui appartient à la classe B a les deux premiers bits du premier octet fixés à 10, c'est-à-dire qu'il s'agit de la classe B.

![Adrese IP de classe B](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0060%20-%20Classes%20d'adresse/images/image1.png)

Les adresses IP de classe B vont de 128.0.x.x à 191.255.x.x. Le masque de sous-réseau par défaut pour la classe B est 255.255.x.x.

La classe B compte 16384 (2^14) adresses réseau et 65534 (2^16-2) adresses hôte.

Le format des adresses IP de classe B est le suivant : ```10NNNN.NNNNNNNN.HHHHHHH.HHHHHHHH```

## Adresse de classe C

Le premier octet de l'adresse IP de classe C a ses 3 premiers bits définis à 110, c'est-à-dire :

![Adrese IP de classe C](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0060%20-%20Classes%20d'adresse/images/image2.png)

Les adresses IP de classe C vont de 192.0.0.x à 223.255.255.x. Le masque de sous-réseau par défaut pour la classe C est 255.255.255.x.

La classe C donne 2097152 (2^21) adresses réseau et 254 (2^8-2) adresses hôte.

Le format des adresses IP de classe C est le suivant : ```110NNNNN.NNNNNNNN.NNNNNNNN.HHHHHHHH```

## Adresse de classe D

Les quatre premiers bits du premier octet des adresses IP de classe D sont réglés sur 1110, ce qui donne une plage de -10% :

![Adrese IP de classe D](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0060%20-%20Classes%20d'adresse/images/image3.png)

La classe D a une plage d'adresses IP allant de 224.0.0.0 à 239.255.255.255. La classe D est réservée à la multidiffusion. Dans la multidiffusion, les données ne sont pas destinées à un hôte particulier, c'est pourquoi il n'est pas nécessaire d'extraire l'adresse de l'hôte de l'adresse IP, et la classe D n'a pas de masque de sous-réseau.

## Adresse de classe E

Cette classe IP est réservée à des fins expérimentales uniquement pour la R&D ou l'étude. Les adresses IP de cette classe vont de 240.0.0.0 à 255.255.255.254. Comme la classe D, cette classe n'est pas non plus dotée d'un masque de sous-réseau.