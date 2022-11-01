IPv4 prend en charge trois types de modes d'adressage différents.

## Mode d'adressage unicast

Dans ce mode, les données ne sont envoyées qu'à un seul hôte de destination. Le champ Adresse de destination contient l'adresse IP à 32 bits de l'hôte de destination. Dans ce cas, le client envoie des données au serveur ciblé.

![Adressage unicast](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0050%20-%20Adressage/images/image2.png)

## Mode d'adressage par diffusion

Dans ce mode, le paquet est adressé à tous les hôtes d'un segment de réseau. Le champ Adresse de destination contient une adresse de diffusion spéciale, c'est-à-dire **255.255.255.255**. Lorsqu'un hôte voit ce paquet sur le réseau, il est tenu de le traiter. Ici, le client envoie un paquet qui est reçu par tous les serveurs.

![Adressage par diffusion](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0050%20-%20Adressage/images/image3.png)

## Mode d'adressage multicast

Ce mode est un mélange des deux modes précédents, c'est-à-dire que le paquet envoyé n'est ni destiné à un seul hôte ni à tous les hôtes du segment. Dans ce paquet, l'adresse de destination contient une adresse spéciale qui commence par 224.x.x.x et qui peut être accueillie par plus d'un hôte.

![Adressage par diffusion](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0050%20-%20Adressage/images/image3.png)

Ici, un serveur envoie des paquets qui sont accueillis par plusieurs serveurs. Chaque réseau possède une adresse IP réservée au numéro de réseau qui représente le réseau et une adresse IP réservée à l'adresse de diffusion, qui représente tous les hôtes de ce réseau.

## Schéma d'adressage hiérarchique

L'IPv4 utilise un schéma d'adressage hiérarchique. Une adresse IP, d'une longueur de 32 bits, est divisée en deux ou trois parties, comme illustré ci-dessous :

![Schéma d'adressage hiérarchique](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0050%20-%20Adressage/images/image4.jpg)

Une seule adresse IP peut contenir des informations sur le réseau et ses sous-réseaux et, en fin de compte, sur l'hôte. Ce schéma permet à l'adresse IP d'être hiérarchisée, un réseau pouvant avoir de nombreux sous-réseaux qui, à leur tour, peuvent avoir de nombreux hôtes.

## Masque de sous-réseau

L'adresse IP 32 bits contient des informations sur l'hôte et son réseau. Il est très nécessaire de distinguer les deux. Pour cela, les routeurs utilisent le masque de sous-réseau, qui est aussi long que la taille de l'adresse réseau dans l'adresse IP. Le masque de sous-réseau est également long de 32 bits. Si l'on fait un ET entre l'adresse IP en binaire et son masque de sous-réseau, le résultat donne l'adresse réseau. Par exemple, disons que l'adresse IP est 192.168.1.152 et que le masque de sous-réseau est 255.255.255.0 alors :

![Masque de sous-réseau](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0050%20-%20Adressage/images/image6.png)

De cette façon, le masque de sous-réseau permet d'extraire l'ID du réseau et l'hôte d'une adresse IP. On peut maintenant identifier que 192.168.1.0 est le numéro de réseau et que 192.168.1.152 est l'hôte sur ce réseau.

## Représentation binaire

La méthode de la valeur positionnelle est la forme la plus simple de conversion de la valeur décimale en binaire. L'adresse IP est une valeur de 32 bits qui est divisée en 4 octets. Un octet binaire contient 8 bits et la valeur de chaque bit peut être déterminée par la position de la valeur du bit '1' dans l'octet.

![Représentation binaire](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0050%20-%20Adressage/images/image1.png)

La valeur positionnelle des bits est déterminée par 2 élevé à la puissance (position - 1), c'est-à-dire que la valeur d'un bit 1 en position 6 est 2^(6-1) soit 2^5 soit 32. La valeur totale de l'octet est déterminée par l'addition des valeurs positionnelles des bits. La valeur de 11000000 est 128+64 = 192. Quelques exemples sont présentés dans le tableau ci-dessous :

![Représentation binaire](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0050%20-%20Adressage/images/image7.png)