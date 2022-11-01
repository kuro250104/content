Dans l'IPv4, les adresses ont été créées par classes. Les adresses IPv4 classful définissent clairement les bits utilisés pour les préfixes de réseau et les bits utilisés pour les hôtes sur ce réseau. Pour créer un sous-réseau en IPv4, nous jouons avec le masque de réseau par défaut qui nous permet d'emprunter des bits d'hôtes pour les utiliser comme bits de sous-réseau. Cela permet d'obtenir plusieurs sous-réseaux, mais moins d'hôtes par sous-réseau. En d'autres termes, lorsque nous empruntons des bits d'hôte pour créer un sous-réseau, cela nous coûte moins de bits à utiliser pour les adresses d'hôte.

Les adresses IPv6 utilisent 128 bits pour représenter une adresse, y compris les bits utilisés pour le sous-réseau. La seconde moitié de l'adresse (64 bits les moins significatifs) est toujours utilisée pour les hôtes uniquement. Par conséquent, il n'y a aucun compromis si l'on met le réseau en sous-réseau.

- **Routing Prefix** (*Préfixe de routage*) : 48 Bits
- **Subnet ID** (*Identifiant de sous-réseau*) : 16 Bits
- **Interface ID** (*Identifiant de l'interface*) : 64 Bits

Les 16 bits de sous-réseau sont équivalents au réseau de classe B d'IPv4. En utilisant ces bits de sous-réseau, une organisation peut avoir 65 000 autres sous-réseaux, ce qui est de loin plus que suffisant.

Ainsi, le préfixe de routage est /64 et la partie hôte est de 64 bits. Il est possible d'étendre le sous-réseau au-delà des 16 bits de l'ID de sous-réseau, en empruntant des bits d'hôte ; mais il est recommandé de toujours utiliser 64 bits pour les adresses d'hôtes, car l'autoconfiguration requiert 64 bits.

Le sous-réseau IPv6 fonctionne selon le même concept que le masquage de sous-réseau à longueur variable en IPv4.

Un préfixe /48 peut être attribué à une organisation, ce qui lui permet d'avoir jusqu'à /64 préfixes de sous-réseau, soit 65535 sous-réseaux, chacun ayant 264 hôtes. Un préfixe /64 peut être attribué à une connexion point à point où il n'y a que deux hôtes (ou dispositifs compatibles IPv6) sur une liaison.