La merveille d'IPv6 réside dans son en-tête. Une adresse IPv6 est 4 fois plus grande qu'IPv4, mais étonnamment, l'en-tête d'une adresse IPv6 n'est que 2 fois plus grand que celui d'IPv4. Les en-têtes IPv6 comportent un en-tête fixe et zéro ou plusieurs en-têtes optionnels (d'extension). Toutes les informations nécessaires et essentielles pour un routeur sont conservées dans l'en-tête fixe. L'en-tête d'extension contient des informations facultatives qui aident les routeurs à comprendre comment traiter un paquet/flux.

## En-tête fixe

![En-tête fixe](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV6/courses/0060%20-%20En-t%C3%AAtes/images/image1.jpg)

L'en-tête fixe IPv6 est long de 40 octets et contient les informations suivantes.

- **Version** (4 bits) : Elle représente la version du protocole Internet, c'est-à-dire 0110.
- **Classe de trafic** (8 bits) : Ces 8 bits sont divisés en deux parties. Les 6 bits les plus significatifs sont utilisés pour le Type de service afin de permettre au routeur de savoir quels services doivent être fournis à ce paquet. Les 2 bits les moins significatifs sont utilisés pour la notification explicite de congestion (ECN).
- **Étiquette de flux** (20 bits) : Ce label est utilisé pour maintenir le flux séquentiel des paquets appartenant à une communication. La source étiquette la séquence pour aider le routeur à identifier qu'un paquet particulier appartient à un flux d'information spécifique. Ce champ permet d'éviter le réordonnancement des paquets de données. Il est conçu pour les médias en streaming/temps réel.
- **Longueur de la charge utile** (16 bits) : Ce champ est utilisé pour indiquer aux routeurs la quantité d'informations qu'un paquet particulier contient dans sa charge utile. La charge utile est composée d'en-têtes d'extension et de données de couche supérieure. Avec 16 bits, on peut indiquer jusqu'à 65535 octets ; mais si les en-têtes d'extension contiennent l'en-tête d'extension Hop-by-Hop, la charge utile peut dépasser 65535 octets et ce champ est mis à 0.
- **En-tête suivant** (8 bits) : Ce champ est utilisé pour indiquer soit le type d'en-tête d'extension, soit, si l'en-tête d'extension n'est pas présent, l'UDP de la couche supérieure. Les valeurs pour le type de PDU de la couche supérieure sont les mêmes que celles de l'IPv4.
- **Hop Limit** (8 bits) : Ce champ est utilisé pour empêcher les paquets de tourner en boucle dans le réseau à l'infini. C'est le même que le TTL dans IPv4. La valeur du champ Hop Limit est décrémentée de 1 à chaque fois qu'il passe un lien (routeur/saut). Lorsque le champ atteint 0, le paquet est rejeté.
- **Adresse source** (128 bits) : Ce champ indique l'adresse de l'expéditeur du paquet.
- **Destination Address** (128-bits) : Ce champ fournit l'adresse du destinataire du paquet.

## En-têtes d'extension

En IPv6, l'en-tête fixe ne contient que les informations nécessaires, en évitant les informations qui ne sont pas nécessaires ou qui sont rarement utilisées. Toutes ces informations sont placées entre l'en-tête fixe et l'en-tête de la couche supérieure sous la forme d'en-têtes d'extension. Chaque en-tête d'extension est identifié par une valeur distincte.

Lorsque des en-têtes d'extension sont utilisés, le champ Next Header de l'en-tête fixe IPv6 pointe vers le premier en-tête d'extension. S'il y a un autre en-tête d'extension, le champ "Next-Header" du premier en-tête d'extension pointe vers le deuxième, et ainsi de suite. Le champ "Next-Header" du dernier en-tête d'extension pointe vers l'en-tête de la couche supérieure. Ainsi, tous les en-têtes pointent vers le suivant à la manière d'une liste liée.

Si le champ "Next Header" contient la valeur 59, cela indique qu'il n'y a pas d'en-tête après cet en-tête, pas même l'en-tête de couche supérieure.

Les en-têtes d'extension suivants doivent être pris en charge conformément à la RFC 2460 :

| **En-tête de l'extension** | **Valeur d'en-tête suivante** | **Description** |
| --- | --- | --- |
| En-tête des options point par point (*Hop-by-Hop Option header*) | 0 | Lu par tous les appareils du réseau de transit |
| En-tête de routage (*Routing header*) | 43 | Contient des méthodes d'aide à la prise de décision concernant le routage |
| En-tête de fragmentation (*Fragment header*) | 44 | Contient les paramètres de fragmentation des datagrammes |
| En-tête des options de destination (*Destination Options header*) | 60 | Lu par les systèmes de destination |
| En-tête d'authentification (*Authentication header*) | 51 | Informations concernant l'authenticité |
| En-tête d'encapsulation de la charge utile de sécurité (*Encapsulating Security Payload header*) | 50 | Informations de cryptage |

La séquence des en-têtes d'extension doit être :

- En-tête IPV6 (IPV6 Header)
- En-tête des options point par point (*Hop-by-Hop Option header*)
- En-tête des options de destination (*Destination Options header*)
- En-tête de routage (*Routing header*)
- En-tête de fragmentation (*Fragment header*)
- En-tête d'authentification (*Authentication header*)
- En-tête d'encapsulation de la charge utile de sécurité (*Encapsulating Security Payload header*)
- En-tête des options de destination (*Destination Options header*)
- En-tête de la couche supérieure (*Upper-layer header*)

Ces en-têtes :

- doivent être traités par la première destination et les destinations suivantes.
- doivent être traités par la destination finale.

Les en-têtes d'extension sont disposés l'un après l'autre à la manière d'une liste liée, comme le montre le schéma suivant :

![Disposition des en-têtes d'extension](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV6/courses/0060%20-%20En-t%C3%AAtes/images/image2.jpg)