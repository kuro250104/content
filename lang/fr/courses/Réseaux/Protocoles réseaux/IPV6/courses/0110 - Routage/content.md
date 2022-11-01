Les concepts de routage restent les mêmes dans le cas d'IPv6, mais presque tous les protocoles de routage ont été redéfinis en conséquence. Nous avons discuté précédemment de la façon dont un hôte parle à sa passerelle. Le routage est un processus visant à transmettre des données routables en choisissant la meilleure route parmi plusieurs routes ou chemins disponibles vers la destination. Un routeur est un dispositif qui transmet les données qui ne lui sont pas explicitement destinées.

Il existe deux formes de protocoles de routage :

- **Distance Vector Routing Protocol** (*Le protocole de routage à vecteur de distance*) : Un routeur exécutant le protocole à vecteur de distance annonce ses routes connectées et apprend de nouvelles routes de ses voisins. Le coût de routage pour atteindre une destination est calculé en fonction du nombre de sauts entre la source et la destination. Un routeur se fie généralement à son voisin pour la sélection du meilleur chemin, également connu sous le nom de "routage par rumeurs". RIP et BGP sont des protocoles à vecteur de distance.
- **Link-State Routing Protocol** (*Protocole de routage à état de liaison*) : Ce protocole reconnaît l'état d'un lien et l'annonce à ses voisins. Les informations sur les nouveaux liens sont apprises des routeurs homologues. Une fois que toutes les informations de routage ont convergé, le protocole de routage par état de liaison utilise son propre algorithme pour calculer le meilleur chemin vers tous les liens disponibles. OSPF et IS-IS sont des protocoles de routage à l'état de liens et tous deux utilisent l'algorithme du plus court chemin de Dijkstra.

Les protocoles de routage peuvent être divisés en deux catégories :

- **Interior routing Protocol** (*Protocole de routage intérieur*) : Les protocoles de cette catégorie sont utilisés au sein d'un système autonome ou d'une organisation pour distribuer les routes entre tous les routeurs à l'intérieur de sa frontière. Exemples : RIP, OSPF.
- **Exterior Routing Protocol** (*Protocole de routage extérieur*) : Un protocole de routage extérieur distribue les informations de routage entre deux systèmes autonomes ou organisations différents. Exemples : BGP : BGP.

## Protocoles de routage

### RIPng

**RIPng** est l'abréviation de **Routing Information Protocol Next Generation**. Il s'agit d'un protocole de routage intérieur et d'un protocole à vecteur de distance. RIPng a été mis à niveau pour prendre en charge IPv6.

### OSPFv3

**Open Shortest Path First version 3** est un protocole de routage intérieur qui a été modifié pour prendre en charge IPv6. Il s'agit d'un protocole à état de liaison qui utilise l'algorithme du plus court chemin de Djikrasta pour calculer le meilleur chemin vers toutes les destinations.

### BGPv4

**BGP** est l'abréviation de **Border Gateway Protocol**. Il s'agit du seul protocole de passerelle extérieure standard ouvert disponible. BGP est un protocole à vecteur de distance qui prend le système autonome comme métrique de calcul, au lieu du nombre de routeurs comme saut. BGPv4 est une mise à niveau de **BGP** pour prendre en charge le routage IPv6.

## Protocoles modifiés pour IPv6

### ICMPv6

**Internet Control Message Protocol version 6** est une mise à jour de l'ICMP pour répondre aux exigences de l'IPv6. Ce protocole est utilisé pour les fonctions de diagnostic, les messages d'erreur et d'information, ainsi qu'à des fins statistiques. Le protocole de découverte des voisins d'ICMPv6 remplace le protocole ARP et permet de découvrir les voisins et les routeurs sur le lien.

### DHCPv6

Le protocole de configuration dynamique des hôtes version 6 est une mise en œuvre du DHCP. Les hôtes compatibles IPv6 n'ont pas besoin d'un serveur DHCPv6 pour acquérir une adresse IP, car ils peuvent être auto-configurés. Ils n'ont pas non plus besoin de DHCPv6 pour localiser le serveur DNS, car celui-ci peut être découvert et configuré via le protocole ICMPv6 Neighbor Discovery. Pourtant, le serveur DHCPv6 peut être utilisé pour fournir ces informations.

### DNS

Il n'y a pas eu de nouvelle version du DNS, mais il est maintenant équipé d'extensions pour fournir un support pour l'interrogation des adresses IPv6. Un nouvel enregistrement AAAA (quad-A) a été ajouté pour répondre aux messages d'interrogation IPv6. Le DNS peut maintenant répondre aux deux versions IP (4 et 6) sans changer le format de la requête.