Une attaque par éclipse est une attaque relativement simple qu'un acteur malveillant peut déployer pour perturber les nœuds d'un réseau. Comme son nom l'indique, l'attaque vise à obscurcir la vue d'un participant sur le réseau pair-à-pair, afin de provoquer une perturbation générale ou de préparer des attaques plus sophistiquées.

Les attaques Eclipse peuvent sembler similaires, à première vue, aux attaques Sybil. Si elles présentent certaines similitudes - l'acteur malveillant inondera le réseau de faux pairs - leur objectif final est finalement différent. Une attaque Eclipse vise un seul nœud (pour des raisons expliquées dans une section ultérieure), tandis qu'une attaque Sybil est une attaque à l'échelle du réseau conçue pour jouer le système de réputation du protocole.

Le concept est longuement discuté dans l'article de 2015 intitulé Eclipse Attacks on Bitcoin's Peer-to-Peer Network, dans lequel des chercheurs de l'université de Boston et de l'université hébraïque rapportent les résultats de leurs expériences de montage d'attaques par éclipse, ainsi que les contre-mesures possibles pour les combattre.

## Comment fonctionne une attaque par éclipse

Les mineurs de Bitcoin ont besoin d'un équipement spécialisé pour générer de nouveaux blocs, mais les nœuds non mineurs (ou complets) peuvent facilement fonctionner avec une puissance de calcul minimale. Cela favorise la décentralisation du bitcoin, car n'importe qui peut faire tourner un nœud sur un appareil de faible puissance. Le logiciel maintient une base de données des transactions qu'il synchronise avec ses pairs immédiats, afin de rester en phase avec le réseau.

La bande passante est un facteur limitant pour de nombreux nœuds. Bien qu'il y ait une quantité énorme de dispositifs exécutant le logiciel, le dispositif moyen est incapable de se connecter directement à la plupart d'entre eux en raison des limites fixées par le logiciel Bitcoin (qui ne permet qu'un maximum de 125 connexions).

Dans une attaque par éclipse, l'acteur malveillant veillera à ce que toutes les connexions de la cible soient établies vers des nœuds contrôlés par l'attaquant. L'entité inondera d'abord la cible de ses propres adresses IP, auxquelles la victime se connectera probablement au moment du redémarrage de son logiciel. Le redémarrage peut être forcé (par exemple, par une attaque DDoS sur la cible) ou l'attaquant peut simplement attendre qu'il se produise. 

Une fois que le redémarrage a eu lieu, la victime sans méfiance est à la merci des nœuds malveillants - sans vue sur le réseau plus large, ils peuvent recevoir des données incorrectes de la part de l'attaquant.

## Conséquences d'une attaque par éclipse

Si un attaquant dépense les ressources nécessaires pour écarter un pair du réseau, il a probablement un motif pour le faire. Il existe une poignée d'attaques successives qui peuvent être lancées plus facilement une fois qu'un nœud a été étouffé.

### Double dépense sans confirmation

Si une personne accepte une transaction sans confirmation, elle risque de faire une double dépense. La transaction peut avoir été diffusée, mais tant qu'elle n'a pas été incluse dans un bloc (et donc enregistrée sur la blockchain), l'expéditeur peut facilement créer une nouvelle transaction qui dépense les mêmes fonds ailleurs. Si la nouvelle transaction a des frais plus élevés, un mineur l'inclura probablement avant l'originale, invalidant ainsi la première. 

Certaines entreprises et certains particuliers acceptent ces transactions sans confirmation. Considérons un commerçant, Bob, qui vend des véhicules haut de gamme. Il ne sait pas qu'Alice a éclipsé son nœud, et ne se doute de rien lorsqu'elle passe une commande pour une voiture de sport de luxe. Elle crée une transaction, que Bob diffuse ensuite sur le réseau. Satisfait que le paiement soit en route, il remet les clés de la voiture et Alice démarre à toute vitesse.

Bien sûr, la transaction n'a pas été diffusée sur le réseau - Bob l'a simplement relayée aux nœuds malveillants d'Alice, qui ne la relaieront pas aux nœuds honnêtes. Pendant que cette transaction reste dans les limbes, Alice dépense les mêmes fonds sur le réseau (réel), que ce soit à une autre partie ou à une adresse qui lui appartient. Même si la transaction initiale vers Bob est finalement vue, elle sera rejetée car les pièces ont déjà été dépensées.

### Double dépense à N-confirmations

La double dépense à N-confirmations est similaire à celle à 0-confirmation, mais implique davantage de préparation. De nombreuses entreprises préfèrent attendre un certain nombre de confirmations avant de marquer un paiement comme valide. Pour contourner cela, l'attaquant doit éclipser à la fois les mineurs et le commerçant. Une fois que l'attaquant a établi la commande avec le commerçant, il diffuse une transaction aux mineurs (éclipsés). La transaction est confirmée et incluse dans la blockchain - mais cette blockchain n'est pas la chaîne que la majorité du réseau observe, puisque le mineur est éclipsé.

De là, l'attaquant relaie cette version de la blockchain au marchand, qui libère les marchandises en croyant que la transaction a été confirmée. Une fois que les nœuds éclipsés rejoignent le réseau réel, la blockchain qu'ils croient à tort être valide est rendue orpheline par celle sur laquelle le reste du réseau a travaillé (ceci présente certaines similitudes avec une attaque 51%).

### Affaiblir les mineurs concurrents

Un nœud éclipsé continuera à fonctionner, sans se rendre compte qu'il a été isolé du réseau. Les mineurs continueront à extraire des blocs en respectant les règles établies par le protocole, mais les blocs ajoutés seront rejetés lorsqu'ils se synchroniseront avec des pairs honnêtes. 

En théorie, une attaque par éclipse à grande échelle sur les principaux mineurs pourrait être utilisée pour faciliter une attaque à 51 %. En l'état actuel des choses, le coût de la prise de contrôle de la majorité de la puissance de hachage du bitcoin est tout simplement trop élevé, même pour les attaquants les plus ingénieux - à ~80TH/s, l'entité aurait besoin de plus de 40TH/s pour tenter une telle manœuvre. 

Dans un scénario hypothétique où cette puissance de hachage est répartie entre 10 parties (de sorte que chacune possède 8TH/s), l'attaquant peut réduire considérablement les exigences pour une attaque de 51% en coupant ces parties du réseau. Si cinq d'entre elles sont éclipsées, 40TH/s sont supprimés de la course pour trouver le prochain bloc, et l'attaquant n'a plus besoin que d'acquérir un peu plus de 20TH/s pour prendre le contrôle.

D'autres sabotages peuvent être réalisés en éclipsant des cibles, notamment la manipulation de nœuds pour le minage égoïste ou l'organisation de courses entre mineurs pour trouver le prochain bloc.

## Mesures d'atténuation

Avec suffisamment d'adresses IP, un attaquant peut éclipser n'importe quel nœud. La méthode la plus simple pour empêcher cela consiste pour un opérateur à bloquer les connexions entrantes et à n'établir des connexions sortantes qu'avec des nœuds spécifiques (tels que ceux qui ont été mis sur une liste blanche par d'autres pairs). Toutefois, comme le souligne le document de recherche, cette approche ne fonctionne pas à l'échelle : si tous les participants adoptent ces mesures, les nouveaux nœuds ne pourront pas rejoindre le réseau.

Les auteurs proposent une poignée de modifications du logiciel Bitcoin, dont certaines ont été intégrées depuis la publication de l'article. Celles-ci rendent les attaques par éclipse plus coûteuses grâce à des modifications mineures du code, comme la sélection aléatoire des nouvelles connexions et une plus grande capacité de stockage des adresses.

## Conclusion

Les attaques Eclipse sont menées au niveau du réseau peer-to-peer. Déployées en tant qu'attaque autonome, elles peuvent constituer une sorte de nuisance. Leur véritable efficacité réside dans la potentialisation d'autres attaques qui ont un impact financier sur les cibles ou qui donnent à l'attaquant un avantage sur le front de l'exploitation minière.

Dans la nature, il n'y a pas encore eu de conséquences graves résultant d'une attaque par éclipse, mais la menace existe toujours malgré les contre-mesures intégrées au réseau. Comme pour la plupart des vecteurs d'attaque qui existent pour le bitcoin et d'autres crypto-monnaies, la défense la plus solide sera celle qui rendra financièrement prohibitive toute tentative de la part de parties malveillantes.