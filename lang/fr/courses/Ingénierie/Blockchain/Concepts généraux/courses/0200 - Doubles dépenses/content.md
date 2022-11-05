La double dépense est un problème potentiel dans un système d'argent numérique où les mêmes fonds sont dépensés à deux destinataires en même temps. Sans contre-mesures adéquates, un protocole qui ne résout pas le problème est fondamentalement miné - les utilisateurs n'ont aucun moyen de vérifier que les fonds qu'ils ont reçus n'ont pas déjà été dépensés ailleurs.

Lorsqu'il s'agit d'argent numérique, il est primordial de s'assurer que les unités spécifiques ne peuvent pas être dupliquées. L'ensemble du système serait mis à mal si Alice pouvait recevoir 10 unités, les copier-coller 10 fois et se retrouver en possession de 100 unités. De même, un tel système ne peut pas fonctionner si elle peut envoyer les mêmes 10 unités à Bob et Carol simultanément. Ainsi, pour que la monnaie numérique fonctionne, des mécanismes doivent être mis en place pour empêcher ce comportement.

## Comment éviter la double dépense ?

### L'approche centralisée

La voie centralisée est considérablement plus facile à mettre en œuvre que les alternatives décentralisées. Elle implique généralement un superviseur qui gère le système et contrôle l'émission et la distribution des unités. Un bon exemple de solution centralisée au problème de la double dépense est celui de l'eCash de David Chaum. 

Pour délivrer aux utilisateurs un actif numérique imitant l'argent liquide (capable d'être échangé de manière anonyme et de pair à pair), une banque peut utiliser des signatures aveugles - comme l'a expliqué le cryptographe David Chaum dans son article de 1982 intitulé Blind Signatures for Untraceable Payments.

Dans un tel contexte, si un utilisateur (appelons-le Dan) souhaite recevoir 100 dollars en espèces numériques, il doit d'abord en informer la banque. S'il dispose du solde de son compte, il générera alors un nombre aléatoire (ou plusieurs, pour les petites coupures). Supposons qu'il produise cinq numéros, chacun ayant une valeur de 20 dollars. Pour empêcher la banque de repérer des unités spécifiques, Dan obscurcit les nombres aléatoires en ajoutant un facteur d'aveuglement à chacun d'entre eux.

Il remet ensuite ces données à la banque, qui débite son compte de 100 dollars et signe des messages certifiant que chacun des cinq éléments d'information est échangeable contre 20 dollars. Dan peut maintenant dépenser les fonds émis par la banque. Il se rend au restaurant d'Erin et achète un repas qui lui coûte 40 $. 

Dan peut retirer le facteur d'aveuglement pour exposer le numéro aléatoire associé à chaque "billet" numérique, qui sert d'identifiant unique pour chaque unité (un peu comme un numéro de série). Il en révèle deux à Erin, qui doit maintenant les échanger immédiatement avec la banque pour empêcher Dan de les dépenser chez un autre commerçant. La banque vérifiera que les signatures sont valides, et si tout semble correct, elle créditera le compte d'Erin de 40 dollars.

Les billets utilisés sont maintenant essentiellement brûlés, et d'autres doivent être émis si Erin souhaite dépenser son nouveau solde de la même manière.

Le système Chaumian eCash pourrait être utile pour les transferts privés. Mais, il échoue dans la résilience parce que la banque est un point central de défaillance. Un billet émis n'a aucune valeur en soi, car sa valeur provient uniquement de la volonté de la banque de l'échanger contre des dollars. Les clients sont à la merci de la banque, et doivent compter sur sa bonne volonté pour que l'argent fonctionne. C'est précisément le problème auquel les crypto-monnaies visent à remédier.

### L'approche décentralisée

Il est plus difficile de s'assurer que les fonds ne peuvent pas être dépensés deux fois dans un écosystème sans superviseur. Des participants de même puissance doivent se coordonner autour d'un ensemble de règles qui empêchent la fraude et incitent tous les utilisateurs à agir honnêtement.

La plus grande innovation présentée dans le livre blanc sur le bitcoin était une solution au problème de la double dépense. Bien qu'il ne soit pas mentionné en tant que tel, Satoshi a proposé la structure de données désormais largement connue sous le nom de blockchain.

Une blockchain n'est en fait qu'une base de données dotée de certaines propriétés uniques. Les participants au réseau (appelés "nœuds") exécutent un logiciel spécialisé qui leur permet de synchroniser leur copie de la base de données avec leurs pairs. Le résultat est que l'ensemble du réseau peut vérifier l'historique des transactions remontant au bloc de genèse. Comme la blockchain est accessible au public, il est facile de détecter et d'empêcher les activités frauduleuses, comme les transactions qui tentent de doubler les dépenses.

Lorsqu'un utilisateur diffuse une transaction, celle-ci n'est pas immédiatement ajoutée à la blockchain - elle doit d'abord être incluse dans un bloc par le biais du minage. En tant que telle, le destinataire ne doit considérer la transaction comme valide qu'après l'ajout de son bloc à la chaîne. Sinon, il risque de perdre les fonds, car l'expéditeur pourrait dépenser les mêmes pièces ailleurs. 

Une fois la transaction confirmée, les pièces ne peuvent pas être dépensées deux fois, car la propriété est attribuée à un nouvel utilisateur - et tout le réseau peut le vérifier. C'est pour cette raison que beaucoup recommandent d'attendre plusieurs confirmations avant d'accepter un paiement comme valide. Chaque bloc suivant augmente considérablement l'effort nécessaire pour modifier ou réécrire la chaîne (ce qui peut se produire lors d'une attaque à 51 %).

Reprenons le scénario du restaurant. Dan retourne au restaurant et remarque cette fois un autocollant "Bitcoin Accepted Here" sur la vitrine. Il a apprécié le repas qu'il a pris la dernière fois et le commande à nouveau. Cela lui coûte 0,005 BTC. 

Erin lui présente une adresse publique à laquelle il doit envoyer les fonds. Dan diffuse la transaction, qui est essentiellement un message signé indiquant que les 0,005 BTC qui étaient en possession de Dan sont maintenant en possession d'Erin. Sans entrer dans les détails, toute personne à qui l'on présente la transaction signée de Dan peut vérifier qu'il était bien en possession des pièces et qu'il avait donc le droit de les envoyer.

Cependant, comme nous l'avons mentionné, la transaction n'est valable que si elle est incluse dans un bloc qui est confirmé. Accepter des transactions non confirmées, c'est un peu comme accepter les 40 dollars en eCash de l'exemple précédent, sans les encaisser immédiatement à la banque - cela permet à l'expéditeur de les dépenser ailleurs. Il est donc recommandé qu'Erin attende au moins 6 confirmations de bloc (environ une heure) avant d'accepter le paiement de Dan.

## Double dépense en bitcoin

Bitcoin est soigneusement conçu pour empêcher les attaques par double dépense, du moins lorsque le protocole est utilisé comme prévu. En effet, si les personnes attendent que les transactions soient confirmées dans un bloc, il n'existe aucun moyen facile pour l'expéditeur de les annuler. Pour ce faire, il devrait "inverser" la blockchain, ce qui nécessite une quantité irréaliste de puissance de hachage.

Cependant, il existe une poignée d'attaques de double dépense qui visent les parties qui acceptent des transactions non confirmées. Pour les achats de faible valeur, par exemple, un commerçant peut ne pas vouloir attendre que les transactions soient incluses dans un bloc. Un fast-food très fréquenté ne peut probablement pas se permettre d'attendre que le réseau traite chaque achat. Ainsi, si une entreprise permet les paiements "instantanés", elle s'expose à des doubles dépenses. Quelqu'un pourrait commander un hamburger, le payer, puis envoyer immédiatement les mêmes fonds à sa propre adresse. Avec des frais plus élevés, cette nouvelle transaction a des chances d'être confirmée en premier, et donc d'invalider la précédente.

Il existe trois méthodes courantes pour effectuer un double paiement :

- **Les attaques à 51 %** : lorsqu'une seule entité ou organisation parvient à contrôler plus de 50 % du taux de hachage, ce qui lui permet d'exclure ou de modifier l'ordre des transactions. Une telle attaque est hautement improbable sur Bitcoin, mais s'est produite dans d'autres réseaux.
- **Les attaques de course** : deux transactions contradictoires sont diffusées successivement, en utilisant les mêmes fonds - mais une seule transaction est confirmée. L'objectif de l'attaquant est d'invalider le paiement en ne validant que la transaction qui lui profite (par exemple, en envoyant les mêmes fonds à une adresse qu'il contrôle). Les attaques de type "race" exigent que le destinataire accepte une transaction non confirmée comme paiement.
- **Attaques Finney** : un attaquant pré-mine une transaction dans un bloc sans la diffuser immédiatement au réseau. Au lieu de cela, il dépense les mêmes pièces dans une autre transaction et ne diffuse qu'ensuite son bloc précédemment miné, ce qui peut invalider le paiement. Les attaques Finney nécessitent une séquence spécifique d'événements pour se produire et sont également subordonnées à l'acceptation par le destinataire de transactions non confirmées.

Comme on peut le voir, un commerçant qui attend les confirmations de blocage réduira considérablement les risques d'être victime de doubles dépenses.

## Conclusion

La double dépense permet à un utilisateur de jouer un système de monnaie électronique à des fins de gain financier, en utilisant les mêmes fonds plus d'une fois. Traditionnellement, l'absence de solutions adéquates à ce problème a fait obstacle aux progrès dans ce domaine.

Heureusement, l'utilisation de signatures aveugles a proposé une solution intéressante pour les systèmes financiers centralisés. Plus tard, la création de mécanismes de preuve de travail et la technologie blockchain ont donné naissance au bitcoin, une forme puissante de monnaie décentralisée - qui, à son tour, a inspiré des milliers d'autres projets de crypto-monnaies.