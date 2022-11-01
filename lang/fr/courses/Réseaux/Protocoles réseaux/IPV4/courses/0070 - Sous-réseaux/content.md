Chaque classe IP est équipée de son propre masque de sous-réseau par défaut qui limite cette classe IP à un nombre prédéterminé de réseaux et à un nombre prédéterminé d'hôtes par réseau. L'adressage IP par classe ne permet pas d'avoir moins d'hôtes par réseau ou plus de réseaux par classe IP.

Le **CIDR** ou **Classless Inter Domain Routing** offre la possibilité d'emprunter des bits de la partie "hôte" de l'adresse IP et de les utiliser comme réseau dans le réseau, appelé sous-réseau. En utilisant le sous-réseau, une seule adresse IP de classe A peut être utilisée pour avoir des sous-réseaux plus petits, ce qui permet une meilleure gestion du réseau.

## Sous-réseaux de classe A
Dans la classe A, seul le premier octet est utilisé comme identifiant du réseau et le reste des trois octets est utilisé pour être attribué aux hôtes (c'est-à-dire 16777214 hôtes par réseau). Pour créer plus de sous-réseaux dans la classe A, les bits de la partie hôte sont empruntés et le masque de sous-réseau est modifié en conséquence.

Par exemple, si un MSB (Most Significant Bit) est emprunté aux bits d'hôte du deuxième octet et ajouté à l'adresse réseau, cela crée deux sous-réseaux (21=2) avec (223-2) 8388606 hôtes par sous-réseau.

Le masque de sous-réseau est modifié en conséquence pour refléter le sous-réseau. Vous trouverez ci-dessous une liste de toutes les combinaisons possibles de sous-réseaux de classe A :

![Sous-réseaux de classe A](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0070%20-%20Sous-r%C3%A9seaux/images/image3.png)

Dans le cas du sous-réseau également, la toute première et la dernière adresse IP de chaque sous-réseau sont utilisées respectivement pour le numéro de sous-réseau et l'adresse IP de diffusion de sous-réseau. Comme ces deux adresses IP ne peuvent pas être attribuées aux hôtes, le sous-réseau ne peut pas être mis en œuvre en utilisant plus de 30 bits comme bits de réseau, ce qui fournit moins de deux hôtes par sous-réseau.

## Sous-réseaux de classe B

Par défaut, en utilisant la mise en réseau par classe, 14 bits sont utilisés comme bits de réseau fournissant (2^14) 16384 réseaux et (2^16-2) 65534 hôtes. Les adresses IP de classe B peuvent être sous-réservées de la même manière que les adresses de classe A, en empruntant des bits aux bits de l'hôte. Ci-dessous, vous trouverez toutes les combinaisons possibles de sous-réseau de classe B.

![Sous-réseaux de classe B](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0070%20-%20Sous-r%C3%A9seaux/images/image2.png)

## Sous-réseaux de classe C

Les adresses IP de classe C sont normalement attribuées à un réseau de très petite taille car elles ne peuvent compter que 254 hôtes dans un réseau. Vous trouverez ci-dessous une liste de toutes les combinaisons possibles d'une adresse IP de classe B sous-réservée.

![Sous-réseaux de classe C](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0070%20-%20Sous-r%C3%A9seaux/images/image1.png)