Le protocole Internet est un protocole de couche 3 (OSI) qui prend des segments de données de la couche 4 (Transport) et les divise en paquets. Le paquet IP encapsule l'unité de données reçue de la couche supérieure et l'ajoute à ses propres informations d'en-tête.

![Encapsulation IP](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0040%20-%20Structure%20des%20paquets/images/image2.png)

Les données encapsulées sont appelées charge utile IP. L'en-tête IP contient toutes les informations nécessaires pour livrer le paquet à l'autre extrémité.

![Charge utile IP](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0040%20-%20Structure%20des%20paquets/images/image1.png)

L'en-tête IP comprend de nombreuses informations pertinentes, notamment le numéro de version qui, dans ce contexte, est 4. Les autres détails sont les suivants :

- **Version** (*Version*) - Numéro de version du protocole Internet utilisé (par exemple, IPv4).
- **IHL** (*Internet Header Length*) - longueur de l'en-tête IP complet.
- **DSCP** (*Differentiated Services Code Point*) - il s'agit du type de service.
- **ECN** (*Explicit Congestion Notification*) - il s'agit d'informations sur la congestion observée sur la route.
- **Total Length** (*Longueur totale*) - Longueur de l'ensemble du paquet IP (y compris l'en-tête IP et la charge utile IP).
- **Identification** (*Identification*) - Si un paquet IP est fragmenté pendant la transmission, tous les fragments contiennent le même numéro d'identification pour identifier le paquet IP d'origine auquel ils appartiennent.
- **Flags** (*Drapeaux*) - Selon les besoins des ressources du réseau, si le paquet IP est trop grand pour être traité, ces "drapeaux" indiquent s'ils peuvent être fragmentés ou non. Dans ce drapeau de 3 bits, le MSB est toujours réglé sur '0'.
- **Fragment Offset** (*Décalage des fragments*) - Ce décalage indique la position exacte du fragment dans le paquet IP d'origine.
- **Time** to Live (*Durée de vie*) - Pour éviter les boucles dans le réseau, chaque paquet est envoyé avec une valeur TTL définie, qui indique au réseau le nombre de routeurs (sauts) que ce paquet peut traverser. À chaque saut, sa valeur est décrémentée de un et lorsque la valeur atteint zéro, le paquet est rejeté.
- **Protocol** (*Protocole*) - Indique à la couche réseau de l'hôte de destination à quel protocole appartient ce paquet, c'est-à-dire le protocole de niveau suivant. Par exemple, le numéro de protocole de ICMP est 1, TCP est 6 et UDP est 17.
- **Header checksum** (*Somme de contrôle de l'en-tête*) - Ce champ est utilisé pour conserver la valeur de la somme de contrôle de tout l'en-tête, qui est ensuite utilisée pour vérifier si le paquet est reçu sans erreur.
- **Source Address** (*Adresse de la source*) - Adresse 32 bits de l'expéditeur (ou source) du paquet.
- **Destination Address** (*Adresse de destination*) - Adresse de 32 bits du récepteur (ou de la destination) du paquet.
- **Options** (*Options*) - Il s'agit d'un champ facultatif, qui est utilisé si la valeur de IHL est supérieure à 5. Ces options peuvent contenir des valeurs pour des options telles que Sécurité, Route d'enregistrement, Horodatage, etc.
