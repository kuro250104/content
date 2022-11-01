Les fournisseurs de services Internet peuvent être confrontés à une situation où ils doivent allouer des sous-réseaux IP de différentes tailles en fonction des besoins des clients. Un client peut demander un sous-réseau de classe C de 3 adresses IP et un autre peut demander 10 IP. Pour un fournisseur d'accès à Internet, il n'est pas possible de diviser les adresses IP en sous-réseaux de taille fixe, mais il peut souhaiter diviser les sous-réseaux de manière à réduire au minimum le gaspillage d'adresses IP.

Par exemple, un administrateur a le réseau 192.168.1.0/24. Le suffixe /24 (prononcé comme "slash 24") indique le nombre de bits utilisés pour l'adresse réseau. Dans cet exemple, l'administrateur a trois départements différents avec un nombre différent d'hôtes. Le département des ventes a 100 ordinateurs, le département des achats a 50 ordinateurs, la comptabilité a 25 ordinateurs et la gestion a 5 ordinateurs. En CIDR, les sous-réseaux sont de taille fixe. En utilisant la même méthodologie, l'administrateur ne peut pas répondre à toutes les exigences du réseau.

La procédure suivante montre comment utiliser le VLSM afin d'allouer des adresses IP par département comme indiqué dans l'exemple :

## Étape 1

Faites une liste des sous-réseaux possibles.

![liste des sous-réseaux possibles](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/R%C3%A9seaux/Protocoles%20r%C3%A9seaux/IPV4/courses/0080%20-%20VLSM/images/image1.png)

## Étape 2

Trier les besoins des IPs par ordre décroissant (du plus élevé au plus bas).

- **Ventes** : 100
- **Achats** : 50
- **Comptes** : 25
- **Gestion** : 5

## Étape 3

Attribuez la gamme d'adresses IP la plus élevée à la demande la plus importante. Ainsi, attribuons 192.168.1.0 /25 (255.255.255.128) au service **Ventes**. Ce sous-réseau IP avec le numéro de réseau 192.168.1.0 possède 126 adresses IP d'hôtes valides qui répondent aux besoins du département **Ventes**. Le masque de sous-réseau utilisé pour ce sous-réseau a 10000000 comme dernier octet.

## Étape 4

Attribuez la plage suivante la plus élevée, donc attribuons 192.168.1.128 /26 (255.255.255.192) au service **Achats**. Ce sous-réseau IP avec le numéro de réseau 192.168.1.128 possède 62 adresses IP d'hôte valides qui peuvent être facilement attribuées à tous les PC du service **Achats**. Le masque de sous-réseau utilisé comporte 11000000 dans le dernier octet.

## Étape 5

Attribuez la plage suivante la plus élevée, c'est-à-dire **Comptes**. Le besoin de 25 IP peut être satisfait avec le sous-réseau 192.168.1.192 /27 (255.255.255.224), qui contient 30 IP hôtes valides. Le numéro de réseau du département **Comptes** sera 192.168.1.192. Le dernier octet du masque de sous-réseau est 11100000.

## Étape 6

Attribuez la plage suivante la plus élevée à la direction. Le service de gestion ne contient que 5 ordinateurs. Le sous-réseau 192.168.1.224 /29 avec le masque 255.255.255.248 a exactement 6 adresses IP d'hôte valides. Il peut donc être attribué à la **Direction**. Le dernier octet du masque de sous-réseau contient 11111000.

En utilisant le VLSM, l'administrateur peut subdiviser le sous-réseau IP de manière à gaspiller le moins d'adresses IP possible. Même après avoir attribué des adresses IP à chaque département, l'administrateur, dans cet exemple, dispose encore d'un grand nombre d'adresses IP, ce qui n'était pas possible s'il avait utilisé le CIDR.
