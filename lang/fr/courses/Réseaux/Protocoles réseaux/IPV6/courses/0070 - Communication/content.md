En IPv4, un hôte qui souhaite communiquer avec un autre hôte sur le réseau doit disposer d'une adresse IP acquise soit au moyen du DHCP, soit par configuration manuelle. Dès qu'un hôte est doté d'une adresse IP valide, il peut parler à n'importe quel hôte du sous-réseau. Pour communiquer sur la couche 3, un hôte doit également connaître l'adresse IP de l'autre hôte. La communication sur une liaison est établie au moyen d'adresses MAC intégrées au matériel. Pour connaître l'adresse MAC d'un hôte dont l'adresse IP est connue, un hôte envoie une diffusion ARP et en retour, l'hôte visé renvoie son adresse MAC.

En IPv6, il n'y a pas de mécanismes de diffusion. Un hôte compatible IPv6 n'est pas obligé d'obtenir une adresse IP par DHCP ou configurée manuellement, mais il peut auto-configurer sa propre IP.

ARP a été remplacé par ICMPv6 Neighbor Discovery Protocol.

## Neighbor Discovery Protocol (Protocole de découverte des voisins)

Un hôte dans un réseau IPv6 est capable de s'auto-configurer avec une adresse locale unique. Dès qu'un hôte obtient une adresse IPv6, il rejoint un certain nombre de groupes de multidiffusion. Toutes les communications liées à ce segment ont lieu uniquement sur ces adresses de multidiffusion. Un hôte passe par une série d'états en IPv6 :

- **Neighbor Solicitation** (*Sollicitation de voisinage*) : Après avoir configuré toutes les adresses IPv6, soit manuellement, soit par le serveur DHCP, soit par auto-configuration, l'hôte envoie un message de sollicitation de voisinage à l'adresse de multidiffusion FF02::1/16 pour toutes ses adresses IPv6 afin de savoir si personne d'autre n'occupe les mêmes adresses.
- **DAD - Duplicate Address Detection** (*Détection des doublons d'adresses*) : Lorsque l'hôte ne reçoit aucune réponse du segment concernant son message de sollicitation de voisinage, il suppose qu'aucune adresse en double n'existe sur le segment.
- **Neighbor Advertisement** (*Annonce de voisinage*) : Après avoir attribué les adresses à ses interfaces et les avoir rendues opérationnelles, l'hôte envoie à nouveau un message de publicité de voisinage indiquant à tous les autres hôtes du segment qu'il a attribué ces adresses IPv6 à ses interfaces.

Une fois qu'un hôte a terminé la configuration de ses adresses IPv6, il fait les choses suivantes :

- **Router Solicitation** (*Sollicitation de routeur*) : Un hôte envoie un paquet multicast de sollicitation de routeur (FF02::2/16) sur son segment pour connaître la présence d'un routeur sur ce segment. Cela aide l'hôte à configurer le routeur comme sa passerelle par défaut. Si le routeur de sa passerelle par défaut tombe en panne, l'hôte peut passer à un nouveau routeur et en faire sa passerelle par défaut.
- **Router Advertisement** (*Annonce de routeur*) : Lorsqu'un routeur reçoit un message de sollicitation de routeur, il répond à l'hôte en annonçant sa présence sur ce lien.
- **Redirect** (*Redirection*) : il peut arriver qu'un routeur reçoive une demande de sollicitation de routeur mais qu'il sache qu'il n'est pas la meilleure passerelle pour l'hôte. Dans ce cas, le routeur renvoie un message de redirection indiquant à l'hôte qu'il existe un meilleur routeur "next-hop". La prochaine étape est l'endroit où l'hôte enverra ses données destinées à un hôte qui n'appartient pas au même segment.