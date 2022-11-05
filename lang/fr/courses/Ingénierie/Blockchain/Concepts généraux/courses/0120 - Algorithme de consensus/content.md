Un algorithme de consensus est un mécanisme qui permet aux utilisateurs ou aux machines de se coordonner dans un cadre distribué. Il doit garantir que tous les agents du système peuvent se mettre d'accord sur une source unique de vérité, même si certains agents font défaut. En d'autres termes, le système doit être tolérant aux pannes (voir également : La tolérance aux pannes byzantine expliquée).

Dans une configuration centralisée, une seule entité a le pouvoir sur le système. Dans la plupart des cas, elle peut apporter des modifications à sa guise - il n'y a pas de système de gouvernance complexe pour parvenir à un consensus entre de nombreux administrateurs. 

Mais dans une configuration décentralisée, c'est une toute autre histoire. Imaginons que nous travaillions avec une base de données distribuée : comment parvenir à un accord sur les entrées à ajouter ?

Surmonter ce défi dans un environnement où les étrangers ne se font pas confiance a peut-être été le développement le plus crucial ouvrant la voie aux blockchains. Dans cet article, nous allons voir comment les algorithmes de consensus sont essentiels au fonctionnement des crypto-monnaies et des grands livres distribués.

## Algorithmes de consensus et crypto-monnaies

Dans les crypto-monnaies, les soldes des utilisateurs sont enregistrés dans une base de données - la blockchain. Il est essentiel que chacun (ou plus précisément, chaque nœud) conserve une copie identique de la base de données. Sinon, on se retrouverait rapidement avec des informations contradictoires, ce qui compromettrait l'objectif même du réseau de crypto-monnaies.

La cryptographie à clé publique garantit que les utilisateurs ne peuvent pas dépenser les pièces des autres. Mais il faut quand même une source unique de vérité à laquelle les participants au réseau se fient pour déterminer si les fonds ont déjà été dépensés.

Satoshi Nakamoto, le créateur de Bitcoin, a proposé un système de preuve de travail pour coordonner les participants. Nous verrons bientôt comment fonctionne le PoW. Pour l'instant, nous allons identifier certains traits communs aux nombreux algorithmes de consensus existants.

Tout d'abord, nous demandons aux utilisateurs qui veulent ajouter des blocs (nous les appellerons les validateurs) de fournir un enjeu. L'enjeu est une sorte de valeur qu'un validateur doit mettre en avant, ce qui le dissuade d'agir de manière malhonnête. S'il triche, il perd son enjeu. Il peut s'agir par exemple de puissance de calcul, de crypto-monnaies ou même de réputation. 

Pourquoi se donneraient-ils la peine de risquer leurs propres ressources ? Eh bien, il y a aussi une récompense disponible. Il s'agit généralement de la crypto-monnaie native du protocole et elle est constituée de frais payés par d'autres utilisateurs, d'unités de crypto-monnaie fraîchement générées, ou des deux.

La dernière chose dont nous avons besoin est la transparence. Nous devons être en mesure de détecter si quelqu'un triche. Idéalement, il devrait être coûteux pour eux de produire des blocs, mais peu coûteux pour quiconque de les valider. Cela garantit que les validateurs sont contrôlés par les utilisateurs réguliers.

## Types d'algorithmes de consensus

### Preuve de travail (PoW - Proof of Work)

La preuve de travail (PoW) est le parrain des algorithmes de consensus de la blockchain. Il a été mis en œuvre pour la première fois dans le bitcoin, mais le concept actuel existe depuis un certain temps. Dans Proof of Work, les validateurs (appelés mineurs) hachent les données qu'ils veulent ajouter jusqu'à ce qu'ils produisent une solution spécifique.

Un hachage est une chaîne de lettres et de chiffres apparemment aléatoire qui est créée lorsque vous faites passer des données par une fonction de hachage. Mais si vous réintroduisez les mêmes données dans la fonction, vous obtiendrez toujours le même résultat. Mais si vous changez ne serait-ce qu'un détail, votre hachage sera complètement différent.

En regardant la sortie, vous ne pouvez pas savoir quelles informations ont été introduites dans la fonction. Elles sont donc utiles pour prouver que vous connaissiez une donnée avant un certain moment. Vous pouvez donner à quelqu'un son hash, et lorsque vous révélez les données plus tard, cette personne peut les exécuter par la fonction pour s'assurer que le résultat est le même.

Dans Proof of Work, le protocole définit les conditions de validité d'un bloc. Il peut dire, par exemple, que seul un bloc dont le hash commence par 00 sera valide. La seule façon pour le mineur de créer un bloc qui correspond à cette combinaison est d'utiliser la force brute. Il peut modifier un paramètre dans ses données pour produire un résultat différent à chaque fois qu'il essaie de deviner jusqu'à ce qu'il obtienne le bon hachage. 

Avec les principales blockchains, la barre est placée incroyablement haut. Pour rivaliser avec les autres mineurs, il vous faut un entrepôt rempli de matériel de hachage spécial (ASIC) pour avoir une chance de produire un bloc valide.

Votre enjeu, lors du minage, est le coût de ces machines et l'électricité nécessaire à leur fonctionnement. Les ASIC sont construits dans un seul but, ils n'ont donc aucune utilité dans des applications autres que le minage de crypto-monnaies. La seule façon de récupérer votre investissement initial est de procéder au minage, qui rapporte une récompense importante si vous réussissez à ajouter un nouveau bloc à la blockchain.

Il est trivial pour le réseau de vérifier que vous avez bien créé le bon bloc. Même si vous avez essayé des billions de combinaisons pour obtenir le bon hachage, il suffit de faire passer vos données par une fonction une seule fois. Si vos données produisent un hachage valide, elles seront acceptées et vous recevrez une récompense. Dans le cas contraire, le réseau les rejettera, et vous aurez perdu du temps et de l'électricité pour rien.

### Preuve d'enjeu (PoS - Proof of Stake)

Proof of Stake (PoS) a été proposé dès les premiers jours de Bitcoin comme une alternative à Proof of Work. Dans un système PoS, il n'y a pas de concept de mineurs, de matériel spécialisé ou de consommation massive d'énergie. Tout ce dont vous avez besoin est un PC ordinaire.

Enfin, pas tout. Vous devez quand même vous impliquer dans le jeu. En PoS, vous ne mettez pas en avant une ressource externe (comme l'électricité ou le matériel), mais une ressource interne - la cryptocurrency. Les règles diffèrent d'un protocole à l'autre, mais il y a généralement un montant minimum de fonds que vous devez détenir pour être éligible au jalonnement.

À partir de là, vous verrouillez vos fonds dans un portefeuille (ils ne peuvent pas être déplacés pendant le jalonnement). Vous vous mettez généralement d'accord avec d'autres validateurs sur les transactions qui seront intégrées au bloc suivant. En un sens, vous pariez sur le bloc qui sera sélectionné, et le protocole en choisira un.

Si votre bloc est sélectionné, vous recevrez une partie des frais de transaction, en fonction de votre mise. Plus vous avez de fonds bloqués, plus vous avez de chances de gagner. Mais si vous tentez de tricher en proposant des transactions non valides, vous perdrez une partie (ou la totalité) de votre mise. Par conséquent, nous avons un mécanisme similaire au PoW - agir honnêtement est plus rentable qu'agir malhonnêtement.

En général, il n'y a pas de pièces fraîchement créées dans le cadre de la récompense pour les validateurs. La monnaie native de la blockchain doit donc être émise d'une autre manière. Cela peut se faire par le biais d'une distribution initiale (c'est-à-dire une ICO ou une IEO) ou en lançant le protocole avec PoW avant de passer ultérieurement à PoS.

À ce jour, la preuve d'enjeu pure n'a vraiment été déployée que dans les petites cryptomonnaies. Il n'est donc pas certain qu'elle puisse constituer une alternative viable au PoW. Bien qu'elle semble théoriquement solide, elle sera très différente dans la pratique. 

Une fois que le PoS est déployé sur un réseau avec une grande quantité de valeur, le système devient un terrain de jeu de la théorie des jeux et des incitations financières. Toute personne ayant le savoir-faire nécessaire pour "pirater" un système de PoS ne le fera probablement que si elle peut en tirer un avantage - par conséquent, la seule façon de savoir si le système est réalisable est de le faire sur un réseau réel.

Nous verrons bientôt le PoS testé à grande échelle - Casper sera mis en œuvre dans le cadre d'une série de mises à niveau du réseau Ethereum (collectivement connu sous le nom d'Ethereum 2.0).

### Autres algorithmes de consensus

Proof of Work et Proof of Stake sont les algorithmes de consensus les plus discutés. Mais il en existe une grande variété d'autres, qui ont tous leurs propres avantages et inconvénients. Consultez les articles suivants :

- La preuve de travail différée
- Le consensus de la preuve d'enjeu loué
- Preuve d'autorité
- Preuve de combustion
- Preuve d'Enjeu Déléguée
- Consensus hybride PoW/PoS

## Conclusion

Les mécanismes permettant de parvenir à un consensus sont essentiels au fonctionnement des systèmes distribués. Beaucoup pensent que la plus grande innovation du bitcoin a été l'utilisation de la preuve de travail pour permettre aux utilisateurs de se mettre d'accord sur un ensemble partagé de faits.

Aujourd'hui, les algorithmes de consensus sous-tendent non seulement les systèmes de monnaie numérique, mais aussi les blockchains, qui permettent aux développeurs d'exécuter du code sur un réseau distribué. Ils sont désormais la pierre angulaire de la technologie blockchain et sont essentiels à la viabilité à long terme des différents réseaux existants.

De tous les algorithmes de consensus, le Proof of Work reste l'offre dominante. Une alternative plus fiable et plus sûre n'a pas encore été proposée. Cela dit, il y a une quantité énorme de recherche et de développement dans les remplacements de PoW, et nous sommes susceptibles de voir plus d'entre eux faire surface dans les années à venir.