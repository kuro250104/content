## Principes fondamentaux d'Ethereum

### Qu'est-ce que l'Ethereum ?

Ethereum est une plateforme informatique décentralisée. Vous pouvez l'imaginer comme un ordinateur portable ou un PC, mais il ne fonctionne pas sur un seul appareil. Au lieu de cela, il fonctionne simultanément sur des milliers de machines à travers le monde, ce qui signifie qu'il n'a pas de propriétaire.

L'Ethereum, comme le Bitcoin et les autres crypto-monnaies, vous permet de transférer de l'argent numérique. Cependant, il est capable de bien plus : vous pouvez déployer votre propre code et interagir avec des applications créées par d'autres utilisateurs. Grâce à sa grande souplesse, toutes sortes de programmes sophistiqués peuvent être lancés sur Ethereum.

En termes simples, l'idée principale derrière Ethereum est que les développeurs peuvent créer et lancer du code qui s'exécute sur un réseau distribué au lieu d'exister sur un serveur centralisé. Cela signifie que, en théorie, ces applications ne peuvent pas être fermées ou censurées.

### Quelle est la différence entre l'Ethereum et l'ether (ETH) ?

Cela peut sembler peu intuitif, mais les unités utilisées dans Ethereum ne sont pas appelées Ethereum ou Ethereums. Ethereum est le protocole lui-même, mais la monnaie qui l'alimente est simplement connue sous le nom d'éther (ou ETH).

### Qu'est-ce qui fait la valeur de l'Ethereum ?

Nous avons abordé l'idée qu'Ethereum peut exécuter du code à travers un système distribué. En tant que tel, les programmes ne peuvent pas être altérés par des parties externes. Ils sont ajoutés à la base de données d'Ethereum (c'est-à-dire la blockchain) et peuvent être programmés de manière à ce que le code ne puisse pas être modifié. En outre, la base de données est visible par tous, de sorte que les utilisateurs peuvent vérifier le code avant d'interagir avec lui.

Cela signifie que n'importe qui, n'importe où, peut lancer des applications qui ne peuvent pas être mises hors ligne. Plus intéressant encore, comme son unité native - l'éther - stocke la valeur, ces applications peuvent fixer des conditions sur la façon dont la valeur est transférée. Nous appelons les programmes qui composent les applications des contrats intelligents. Dans la plupart des cas, ils peuvent être configurés pour fonctionner sans intervention humaine.

Il est compréhensible que l'idée d'une "monnaie programmable" ait captivé les utilisateurs, les développeurs et les entreprises du monde entier.

### Qu'est-ce que la blockchain ?

La blockchain est au cœur d'Ethereum - c'est la base de données qui contient les informations utilisées par le protocole. Si vous avez lu notre article intitulé "Qu'est-ce que le bitcoin ?", vous aurez une idée de base du fonctionnement d'une blockchain. La blockchain d'Ethereum est similaire à celle de Bitcoin, bien que les données qu'elle stocke - et la façon dont elle les stocke - soient différentes.

Il est utile d'imaginer la blockchain d'Ethereum comme un livre auquel vous ajoutez sans cesse des pages. Chaque page est appelée un bloc, et elle est remplie d'informations sur les transactions. Lorsque nous voulons ajouter une nouvelle page, nous devons inclure une valeur spéciale en haut de la page. Cette valeur doit permettre à quiconque de voir que la nouvelle page a été ajoutée après la page précédente, et non pas insérée dans le livre au hasard.

En fait, c'est un peu comme un numéro de page qui fait référence à la page précédente. En regardant la nouvelle page, nous pouvons dire avec certitude qu'elle suit la précédente. Pour ce faire, nous utilisons un processus appelé hachage. 

Le hachage prend un élément de données - dans ce cas, tout ce qui se trouve sur notre page - et renvoie un identifiant unique (notre hachage). Les chances que deux éléments de données nous donnent le même hachage sont astronomiquement faibles. Il s'agit également d'un processus à sens unique : vous pouvez facilement calculer un hachage, mais il vous est pratiquement impossible d'inverser le hachage pour obtenir les informations utilisées pour le créer. Nous verrons pourquoi cela est important pour l'exploitation minière dans un chapitre ultérieur.

Nous disposons maintenant d'un mécanisme permettant de relier nos pages dans l'ordre correct. Toute tentative de modifier l'ordre ou de supprimer des pages montrera que notre livre a été altéré. 

### Ethereum vs. Bitcoin - quelle est la différence ?

Le bitcoin s'appuie sur la technologie blockchain et sur des incitations financières pour créer un système mondial de monnaie numérique. Il a introduit quelques innovations clés qui permettent de coordonner les utilisateurs du monde entier sans avoir recours à une partie centrale. En demandant à chaque participant d'exécuter un programme sur son ordinateur, Bitcoin a permis aux utilisateurs de se mettre d'accord sur l'état d'une base de données financières dans un environnement décentralisé et sans confiance.

Le bitcoin est souvent considéré comme une blockchain de première génération. Il n'a pas été créé en tant que système excessivement complexe, et c'est un atout en matière de sécurité. Elle est restée intentionnellement inflexible pour donner la priorité à la sécurité dans sa couche de base. En effet, le langage des contrats intelligents du bitcoin est extrêmement limité et ne s'adapte pas très bien aux applications autres que les transactions.

La deuxième génération de blockchains, en revanche, est capable de plus. En plus des transactions financières, ces plateformes permettent un plus grand degré de programmabilité. Ethereum offre aux développeurs beaucoup plus de liberté pour expérimenter avec leur propre code et créer ce que nous appelons des applications décentralisées (DApps).

Ethereum a été la première de la vague de blockchains de deuxième génération et reste la plus importante à ce jour. Elle présente des similitudes avec le bitcoin et peut remplir bon nombre des mêmes fonctions. Sous le capot, cependant, les deux sont très différents, et chacun a ses propres avantages sur l'autre.

### Comment fonctionne Ethereum ?

Nous pourrions définir Ethereum comme une machine à état. Cela signifie qu'à tout moment, vous avez un instantané de tous les soldes de comptes et des contrats intelligents tels qu'ils se présentent actuellement. Certaines actions provoquent la mise à jour de l'état, ce qui signifie que tous les nœuds mettent à jour leur propre instantané pour refléter le changement.

Les contrats intelligents qui fonctionnent sur Ethereum sont déclenchés par des transactions (provenant soit d'utilisateurs, soit d'autres contrats). Lorsqu'un utilisateur envoie une transaction à un contrat, chaque nœud du réseau exécute le code du contrat et enregistre le résultat. Pour ce faire, il utilise la machine virtuelle Ethereum (EVM), qui convertit les contrats intelligents en instructions lisibles par l'ordinateur.

Pour mettre à jour l'état, un mécanisme spécial appelé "mining" est utilisé (pour l'instant). Le minage est effectué à l'aide d'un algorithme de preuve de travail, un peu comme celui de Bitcoin. Nous reviendrons plus en détail sur ce sujet dans un instant.

### Qu'est-ce qu'un contrat intelligent ?

Un contrat intelligent est juste un code. Ce code n'est ni intelligent, ni un contrat au sens traditionnel du terme. Mais nous le qualifions d'intelligent parce qu'il s'exécute lui-même dans certaines conditions, et il pourrait être considéré comme un contrat dans la mesure où il fait respecter les accords entre les parties.

C'est à l'informaticien Nick Szabo que l'on doit cette idée, qu'il a proposée à la fin des années 1990. Il a utilisé l'exemple d'un distributeur automatique pour expliquer le concept, déclarant qu'il pouvait être considéré comme un précurseur du contrat intelligent moderne. Dans le cas d'un distributeur automatique, un contrat simple est exécuté. Les utilisateurs insèrent des pièces de monnaie et, en retour, la machine distribue un produit de leur choix.

Un contrat intelligent applique ce type de logique dans un cadre numérique. Vous pourriez spécifier quelque chose de simple dans le code, comme retourner "Hello, World !" lorsque deux éthers sont envoyés à ce contrat.

Dans Ethereum, le développeur coderait ce contrat de manière à ce qu'il puisse être lu ultérieurement par l'EVM. Il le publie ensuite en l'envoyant à une adresse spéciale qui enregistre le contrat. À ce stade, tout le monde peut l'utiliser. Et le contrat ne peut pas être supprimé, sauf si une condition est spécifiée par le développeur lors de sa rédaction.

Maintenant, le contrat a une adresse. Pour interagir avec lui, il suffit aux utilisateurs d'envoyer 2 ETH à cette adresse. Cela déclenchera le code du contrat - tous les ordinateurs du réseau l'exécuteront, verront que le paiement a été effectué au contrat, et enregistreront sa sortie ("Hello, World !").

Ce qui précède est peut-être l'un des exemples les plus basiques de ce qui peut être fait avec Ethereum. Des applications plus sophistiquées qui connectent de nombreux contrats peuvent - et ont - été construites.

### Qui a créé Ethereum ?

En 2008, un développeur (ou groupe de développeurs) inconnu a publié le livre blanc du bitcoin sous le pseudonyme de Satoshi Nakamoto. Cette publication a définitivement changé le paysage de la monnaie numérique. Quelques années plus tard, un jeune programmeur du nom de Vitalik Buterin a imaginé un moyen d'approfondir cette idée et de l'appliquer à tout type d'application. Le concept a finalement été concrétisé dans Ethereum.

Ethereum a été proposé par Buterin dans un article de blog de 2013 intitulé Ethereum : The Ultimate Smart Contract and Decentralized Application Platform. Dans ce billet, il décrivait l'idée d'une blockchain Turing-complète, c'est-à-dire un ordinateur décentralisé qui, avec suffisamment de temps et de ressources, pourrait exécuter n'importe quelle application. 

À terme, les types d'applications qui pourraient être déployées sur une blockchain ne seraient limitées que par l'imagination des développeurs. Ethereum vise à découvrir si la technologie blockchain a des utilisations valables en dehors des limites de conception intentionnelles de Bitcoin.

### Comment l'éther a-t-il été distribué ?

Ethereum a été lancé en 2015 avec une offre initiale de 72 millions d'éther. Plus de 50 millions de ces jetons ont été distribués lors d'une vente publique de jetons appelée Initial Coin Offering (ICO), où les personnes souhaitant participer pouvaient acheter des jetons d'éther en échange de bitcoins ou de monnaie fiduciaire.

### Qu'était la DAO et qu'est-ce qu'Ethereum Classic ?

Avec Ethereum, de toutes nouvelles méthodes de collaboration ouverte sur Internet sont devenues possibles. Prenons, par exemple, les DAO (organisations autonomes décentralisées), qui sont des entités régies par un code informatique, à l'instar d'un programme informatique.

L'une des premières et des plus ambitieuses tentatives d'une telle organisation était "The DAO". Elle aurait été constituée de contrats intelligents complexes fonctionnant au-dessus d'Ethereum, et fonctionnant comme un fonds de capital-risque autonome. Les jetons DAO ont été distribués dans le cadre d'une ICO et ont permis aux détenteurs de jetons d'acquérir une participation, ainsi que des droits de vote.

Peu de temps après son lancement, cependant, des acteurs malveillants ont exploité une vulnérabilité et drainé près d'un tiers des fonds de la DAO. Il faut savoir qu'à l'époque, 14 % de l'offre totale d'éther était bloquée dans la DAO. Inutile de dire que cet événement a été dévastateur pour le réseau Ethereum, encore jeune.

Après délibération, la chaîne a été scindée en deux chaînes. Dans l'une, les transactions malveillantes ont été effectivement "inversées" pour restaurer les fonds - cette chaîne est maintenant connue sous le nom de blockchain Ethereum. La chaîne originale, où ces transactions n'ont pas été annulées et où l'immuabilité a été maintenue, est maintenant connue sous le nom d'Ethereum Classic.

Cet événement a été un rappel brutal des risques de cette technologie et de la façon dont le fait de confier à un code autonome de grandes quantités de richesses peut se retourner contre nous. C'est aussi un exemple intéressant de la façon dont la prise de décisions collectives dans un environnement ouvert peut poser des défis importants. Mais si l'on fait abstraction de ses faiblesses en matière de sécurité, The DAO a parfaitement illustré le potentiel des contrats intelligents pour permettre une collaboration sans confiance à grande échelle sur Internet.

## D'où vient l'éther ?

### Comment le nouvel éther est-il créé ?

Nous avons brièvement évoqué le minage plus tôt. Si vous connaissez le bitcoin, vous savez que le processus de minage fait partie intégrante de la sécurisation et de la mise à jour de la blockchain. Le même principe s'applique à Ethereum : pour récompenser les utilisateurs qui exploitent les mines (ce qui est coûteux), le protocole les récompense avec de l'éther.

### Combien y a-t-il d'éther ?

En février 2020, l'offre totale d'éther est d'environ 110 millions. Contrairement à celui du bitcoin, le calendrier d'émission des jetons d'Ethereum n'a volontairement pas été décidé au lancement. Le bitcoin a cherché à préserver sa valeur en limitant son offre et en diminuant lentement la quantité de nouvelles pièces qui voient le jour. Ethereum, quant à lui, vise à fournir une base pour les applications décentralisées (DApps). Comme on ne sait pas exactement quel type de calendrier d'émission de jetons correspond le mieux à cet objectif, la question reste ouverte.

### Comment fonctionne le minage d'Ethereum ?

L'exploitation minière est essentielle à la sécurité du réseau. Il garantit que la blockchain peut être mise à jour de manière équitable et permet au réseau de fonctionner sans décideur unique. Dans le cadre du minage, un sous-ensemble de nœuds (appelés à juste titre mineurs) consacre sa puissance de calcul à la résolution d'une énigme cryptographique.

Ce qu'ils font en fait, c'est hacher un ensemble de transactions en attente, ainsi que d'autres données. Pour que le bloc soit considéré comme valide, le hachage doit être inférieur à une valeur fixée par le protocole. S'ils n'y parviennent pas, ils peuvent modifier certaines des données et réessayer.

Pour rivaliser avec les autres, les mineurs doivent donc être capables de hacher le plus rapidement possible - nous mesurons leur puissance en taux de hachage. Plus le taux de hachage est élevé sur le réseau, plus l'énigme devient difficile à résoudre. Seuls les mineurs doivent trouver la solution réelle - une fois qu'elle est connue, il est facile pour tous les autres participants de vérifier qu'elle est valide.

Comme vous pouvez l'imaginer, le hachage continu à grande vitesse est coûteux. Pour inciter les mineurs à sécuriser le réseau, ils reçoivent une récompense. Elle est composée de tous les frais liés aux transactions du bloc. Ils reçoivent également de l'éther fraîchement généré - 2 ETH au moment de la rédaction de cet article.

### Qu'est-ce que le gaz Ethereum ?

Vous vous souvenez de notre contrat Hello, World ! de tout à l'heure ? C'était un programme facile à exécuter. Il n'est pas du tout très coûteux en termes de calcul. Mais vous ne l'exécutez pas seulement sur votre propre PC - vous demandez à tous les membres de l'écosystème Ethereum de l'exécuter également.

Cela nous amène à la question suivante : que se passe-t-il lorsque des dizaines de milliers de personnes exécutent des contrats sophistiqués ? Si quelqu'un configure son contrat pour qu'il tourne en boucle avec le même code, chaque nœud devra l'exécuter indéfiniment. Cela mettrait trop de pression sur les ressources et le système s'effondrerait probablement en conséquence.

Heureusement, Ethereum introduit le concept de gaz (gas) pour atténuer ce risque. Tout comme votre voiture ne peut pas fonctionner sans carburant, les contrats ne peuvent pas être exécutés sans gaz. Les contrats fixent une quantité de gaz que les utilisateurs doivent payer pour qu'ils puissent être exécutés avec succès. S'il n'y a pas assez de carburant, le contrat s'arrête. 

Il s'agit essentiellement d'un mécanisme de rémunération. Le même concept s'applique aux transactions : les mineurs sont principalement motivés par le profit, ils peuvent donc ignorer les transactions dont les frais sont moins élevés.

**Notez que l'éther et le gaz ne sont pas identiques**. Le prix moyen du gaz fluctue et est largement décidé par les mineurs. Lorsque vous effectuez une transaction, vous payez le gaz en ETH. C'est comme les frais de Bitcoin à cet égard - si le réseau est encombré et que de nombreux utilisateurs tentent d'effectuer des transactions, le prix moyen du gaz augmentera probablement. À l'inverse, s'il n'y a pas beaucoup d'activité, il diminuera.

Si le prix du gaz varie, chaque opération nécessite une quantité fixe de gaz. Cela signifie que les contrats complexes consommeront beaucoup plus qu'une simple transaction. En tant que tel, le gaz est une mesure de la puissance de calcul. Il garantit que le système peut fournir une rémunération appropriée aux utilisateurs en fonction de leur utilisation des ressources d'Ethereum.

Le gaz coûte généralement une fraction de l'éther. C'est pourquoi nous utilisons une unité plus petite (gwei) pour le désigner. Un gwei correspond à un milliardième d'éther.

Pour faire court, vous pourriez exécuter un programme qui tourne en boucle pendant une longue période. Mais cela devient rapidement très coûteux pour vous de le faire. Pour cette raison, les nœuds du réseau Ethereum peuvent atténuer le spam.

### Gaz et limites de gaz

Supposons qu'Alice effectue une transaction dans le cadre d'un contrat. Elle calcule le montant qu'elle veut dépenser pour l'essence (par exemple, en utilisant ETH Gas Station). Elle pourrait fixer un prix plus élevé pour inciter les mineurs à inclure sa transaction le plus rapidement possible. 

Mais elle fixera également une limite d'essence, qui sert à la protéger. Un problème peut survenir dans le contrat et entraîner une consommation de gaz supérieure à ce qu'elle avait prévu. La limite de gaz est mise en place pour garantir qu'une fois la quantité x de gaz consommée, l'opération s'arrêtera. Le contrat échouera, mais Alice ne paiera pas plus que ce qu'elle avait initialement convenu de payer.

Au départ, ce concept peut sembler difficile à appréhender. Ne vous inquiétez pas : vous pouvez définir manuellement le prix que vous êtes prêt à payer pour l'essence (et la limite d'essence), mais la plupart des portefeuilles s'en chargent pour vous. En bref, le prix du gaz définit la vitesse à laquelle les mineurs prendront votre transaction, et la limite du gaz définit le montant maximum que vous paierez pour celle-ci. 

### Combien de temps faut-il pour extraire un bloc d'Ethereum ?

Le temps moyen nécessaire à l'ajout d'un nouveau bloc à la chaîne se situe entre 12 et 19 secondes. Cela changera très probablement une fois que le réseau aura fait la transition vers la Proof of Stake, qui vise, entre autres, à permettre des temps de bloc plus rapides. Si vous souhaitez en savoir plus à ce sujet, consultez le document Ethereum Casper Explained.

### Que sont les jetons Ethereum ?

Une grande partie de l'attrait d'Ethereum réside dans la possibilité pour les utilisateurs de créer leurs propres actifs sur la chaîne, qui peuvent être stockés et transférés comme de l'éther. Les règles qui les régissent sont définies dans des contrats intelligents, permettant aux développeurs de définir des paramètres spécifiques concernant leurs jetons. Il peut s'agir du nombre de jetons à émettre, de la manière de les émettre, de leur divisibilité, de leur fongibilité, etc. La plus importante des normes techniques qui permettent la création de jetons sur Ethereum est appelée ERC-20 - et c'est pourquoi les jetons sont communément appelés jetons ERC-20.

La fonctionnalité des jetons offre aux innovateurs un vaste terrain de jeu pour expérimenter des applications à la pointe de la finance et de la technologie. Qu'il s'agisse d'émettre des jetons uniformes servant de monnaie dans l'application ou de produire des jetons uniques garantis par des actifs physiques, il existe une grande souplesse de conception. Il est tout à fait possible que certains des meilleurs cas d'utilisation pour la création facile et rationalisée de jetons ne soient pas encore connus. 

## Démarrer avec Ethereum

### Que puis-je acheter avec l'ether (ETH) ?

Contrairement au bitcoin, Ethereum n'est pas destiné à être utilisé uniquement comme un réseau de crypto-monnaies. Il s'agit d'une plateforme permettant de créer des applications décentralisées et, en tant que jeton négociable, l'éther est le carburant de cet écosystème. Ainsi, le principal cas d'utilisation de l'éther est sans doute l'utilité qu'il procure au sein du réseau Ethereum.

Cela dit, l'éther peut également être utilisé comme une monnaie traditionnelle, ce qui signifie que vous pouvez acheter des biens et des services avec l'ETH comme avec toute autre monnaie.

### A quoi sert l'Ethereum ?

Les gens peuvent utiliser la monnaie native d'Ethereum, ETH, comme monnaie numérique ou comme garantie. Beaucoup la considèrent également comme une réserve de valeur, similaire au Bitcoin. Cependant, contrairement au bitcoin, la blockchain d'Ethereum est plus programmable, de sorte que vous pouvez faire beaucoup plus avec l'ETH. Il peut être utilisé comme source de vie pour des applications financières décentralisées, des marchés décentralisés, des échanges, des jeux et bien d'autres choses encore. 

### Que faire si je perds mes ETH ?

Puisqu'il n'y a pas de banques impliquées, vous êtes responsable de vos propres fonds. Vous pouvez stocker vos pièces sur un échange, ou dans votre propre portefeuille. Il est important de noter que si vous utilisez votre propre portefeuille, vous devez absolument prendre soin de votre phrase de démarrage. Gardez-la en sécurité car vous en aurez besoin pour restaurer vos fonds au cas où vous perdriez l'accès à votre portefeuille.

### Puis-je inverser les transactions Ethereum ?

Une fois que les données sont ajoutées à la blockchain Ethereum, il est presque impossible de les modifier ou de les supprimer. Cela signifie que lorsque vous effectuez une transaction, vous pouvez considérer qu'elle est gravée dans la pierre. Vous devez donc toujours vérifier que vous envoyez des fonds à la bonne adresse. Si vous envoyez un montant important, il peut être utile d'envoyer d'abord un petit montant pour être sûr que vous envoyez à la bonne adresse.

Cela dit, en raison d'un piratage d'un contrat intelligent, Ethereum a fait l'objet d'une bifurcation en 2016, les transactions malveillantes ayant été effectivement "annulées". Il s'agissait toutefois d'une mesure extrême pour un événement exceptionnel, et non de la norme.

### Les transactions Ethereum sont-elles privées ?

Non. Toutes les transactions qui sont ajoutées à la blockchain Ethereum sont publiquement visibles. Même si votre vrai nom ne figure pas sur votre adresse Ethereum, un observateur pourrait être en mesure de le relier à votre identité par d'autres méthodes.

### Puis-je gagner de l'argent avec Ethereum ?

Comme il s'agit d'un actif volatil, vous pouvez gagner de l'argent avec l'ETH tout comme vous pouvez en perdre. Certaines personnes peuvent détenir l'ETH à long terme, en pariant sur le fait que le réseau deviendra une couche de règlement mondiale et programmable. D'autres choisissent de le négocier contre d'autres altcoins. Pourtant, ces deux stratégies comportent leurs propres risques financiers.

En tant que principal pilier du mouvement de la finance décentralisée (DeFi), l'ETH peut également être utilisé pour prêter, servir de garantie pour contracter des prêts, frapper des actifs synthétiques et - à un moment donné dans le futur - jalonner.

Certains investisseurs peuvent ne détenir qu'une position à long terme sur le bitcoin et ne pas inclure d'autres actifs numériques dans leur portefeuille. En revanche, d'autres peuvent choisir de détenir des ETH et d'autres altcoins dans leur portefeuille, ou d'en allouer un certain pourcentage à des transactions à plus court terme (par exemple, le day trading ou le swing trading). Il n'existe pas d'approche unique pour gagner de l'argent sur les marchés, et chaque investisseur doit décider par lui-même quelle est la stratégie la plus adaptée à son profil et à sa situation.

### Comment puis-je stocker mes ETH ?

Il existe de nombreuses options pour stocker les tokens, chacune ayant ses propres avantages et inconvénients. Comme pour tout ce qui comporte des risques, il est préférable de diversifier les options disponibles.

En général, les solutions de stockage peuvent être avec ou sans garde. Une solution de garde signifie que vous confiez vos pièces à un tiers (comme une bourse). Dans ce cas, vous devez vous connecter à la plateforme du dépositaire pour effectuer des transactions avec vos cryptoactifs.

Une solution sans dépositaire est l'inverse : vous gardez le contrôle de vos propres fonds, tout en utilisant un portefeuille de crypto-monnaies. Un portefeuille ne contient pas vos pièces comme un portefeuille physique - il contient plutôt des clés cryptographiques qui vous permettent d'accéder à vos actifs sur la blockchain. Il convient de le souligner à nouveau : il est impératif que vous sauvegardiez votre phrase de départ lorsque vous utilisez un portefeuille sans garde !

### Comment stocker votre ETH dans un portefeuille Ethereum ?

Si vous souhaitez stocker votre ETH dans votre propre portefeuille, deux options principales s'offrent à vous : les portefeuilles chauds et les portefeuilles froids.

#### Hot wallets

Un portefeuille de crypto-monnaies qui est connecté à Internet d'une manière ou d'une autre est appelé "hot wallet". En général, il s'agit d'une application mobile ou de bureau qui vous permet de vérifier vos soldes et d'envoyer ou de recevoir des jetons. Les porte-monnaie électroniques étant en ligne, ils sont généralement plus vulnérables aux attaques, mais aussi plus pratiques pour les paiements quotidiens. Trust Wallet est un exemple de porte-monnaie mobile facile à utiliser, qui prend en charge un grand nombre de pièces.

#### Cold wallets

Un cold wallet est un portefeuille de crypto-monnaies qui n'est pas exposé à l'Internet. Comme il n'y a pas de vecteur d'attaque en ligne, les risques d'attaque sont globalement plus faibles. En même temps, les cold wallets sont généralement moins intuitifs à utiliser que les hot wallets. Parmi les exemples de cold wallets, on peut citer les hardware wallets ou les paper wallets, mais l'utilisation des paper wallets est souvent déconseillée car beaucoup les considèrent comme obsolètes et risqués à utiliser.

### Quel est le logo et le symbole d'Ethereum ?

Vitalik Buterin a conçu le tout premier emblème d'Ethereum. Il était composé de deux symboles de sommation tournés Σ (Sigma de l'alphabet grec). Le design final du logo (basé sur cet emblème) est composé d'une forme rhomboïde appelée octaèdre entourée de quatre triangles. Comme pour les autres monnaies, il pourrait être utile que l'éther ait un symbole Unicode standard afin que les applications et les sites web puissent facilement afficher les valeurs de l'éther. Bien qu'il ne soit pas aussi largement utilisé que, par exemple, le $ pour le dollar américain, le symbole le plus couramment utilisé pour l'éther est Ξ.

## Scalabilité, ETH 2.0 et l'avenir d'Ethereum

### Qu'est-ce que l'évolutivité ?

Dans les termes les plus simples, l'évolutivité est une mesure de la capacité d'un système à se développer. En informatique, par exemple, un réseau ou un serveur peut être mis à l'échelle pour gérer une plus grande demande par le biais de différentes méthodes.

Dans le domaine des crypto-monnaies, l'évolutivité désigne la capacité d'une blockchain à se développer pour accueillir davantage d'utilisateurs. Plus d'utilisateurs signifie plus d'opérations et de transactions "en concurrence" pour être incluses dans la blockchain.

### Pourquoi Ethereum doit-il évoluer ?

Les partisans d'Ethereum pensent que la prochaine itération de l'Internet sera construite sur la plateforme. Ce que l'on appelle le Web 3.0 donnera naissance à une topologie décentralisée caractérisée par l'absence d'intermédiaires, l'accent mis sur la vie privée et l'évolution vers une véritable propriété de ses propres données. Cette base serait construite en utilisant l'informatique distribuée sous la forme de contrats intelligents et de protocoles de stockage/communication distribués.

Pour y parvenir, cependant, Ethereum doit augmenter massivement le nombre de transactions qu'il peut traiter sans nuire à la décentralisation du réseau. Actuellement, Ethereum ne limite pas le volume des transactions en restreignant la taille des blocs comme le fait Bitcoin. Au lieu de cela, il existe une limite de gaz de bloc - seule une certaine quantité de gaz peut tenir dans un bloc.

Par exemple, si vous avez une limite de gaz en bloc de 100 000 gwei et que vous voulez inclure dix transactions avec une limite de gaz de 10 000 gwei chacune, cela fonctionnera. Il en va de même pour deux transactions de 50 000 gwei. Toute autre transaction soumise en parallèle devra attendre le bloc suivant. 

Ce n'est pas idéal pour un système que tout le monde utilise. S'il y a plus de transactions en attente que d'espace disponible dans un bloc, on se retrouve rapidement avec un arriéré. Le prix de l'essence augmentera, et les utilisateurs devront surenchérir pour que leurs transactions soient incluses en premier. En fonction de l'activité du réseau, les opérations pourraient devenir trop coûteuses pour certains cas d'utilisation.

La montée en puissance de CryptoKitties a été un excellent exemple des limites d'Ethereum sur ce plan. En 2017, le jeu basé sur Ethereum a incité de nombreux utilisateurs à effectuer des transactions pour participer à l'élevage de leurs propres chats numériques (représentés sous forme de jetons non fongibles). Il est devenu si populaire que les transactions en attente sont montées en flèche, entraînant une congestion extrême du réseau pendant un certain temps.

### Le trilemme de l'évolutivité de la blockchain

Il semble que le simple fait d'augmenter la limite de gaz des blocs résoudrait tous les problèmes d'évolutivité. Plus le plafond est élevé, plus le nombre de transactions pouvant être traitées dans un laps de temps donné est important, non ?

Malheureusement, cela n'est pas possible sans sacrifier les propriétés clés d'Ethereum. Vitalik Buterin a proposé le trilemme de la blockchain (visualisé ci-dessous) pour expliquer l'équilibre délicat que les blockchains doivent atteindre.

En choisissant d'optimiser deux des trois caractéristiques ci-dessus, la troisième fera défaut. Les blockchains comme Ethereum et Bitcoin privilégient la sécurité et la décentralisation. Leurs algorithmes de consensus assurent la sécurité de leurs réseaux, qui sont constitués de milliers de nœuds, mais cela entraîne une faible évolutivité. Avec autant de nœuds recevant et validant les transactions, le système est beaucoup plus lent que les alternatives centralisées.

Dans un autre scénario, la limite de gaz de bloc pourrait être levée afin que le réseau atteigne la sécurité et l'évolutivité, mais il ne sera pas aussi décentralisé. 

Cela s'explique par le fait qu'un plus grand nombre de transactions dans un bloc entraîne des blocs plus gros. Pourtant, les nœuds du réseau doivent les télécharger et les propager périodiquement. Et ce processus est intensif sur le matériel. Lorsque la limite de gaz des blocs est augmentée, il devient plus difficile pour les nœuds de valider, stocker et diffuser les blocs.

Par conséquent, on peut s'attendre à ce que les nœuds qui ne peuvent pas suivre se retirent du réseau. En continuant de cette manière, seule une fraction de nœuds puissants serait en mesure de participer, ce qui entraînerait une plus grande centralisation. Vous pourriez vous retrouver avec une blockchain sécurisée et évolutive, mais elle ne serait pas décentralisée.

Enfin, nous pouvons imaginer une blockchain qui se concentre sur la décentralisation et l'évolutivité. Pour être à la fois rapide et décentralisée, des sacrifices doivent être faits en ce qui concerne l'algorithme de consensus utilisé, ce qui conduit à une sécurité plus faible.

### Combien de transactions Ethereum peut-il traiter ?

Ces dernières années, Ethereum a rarement dépassé les dix transactions par seconde (TPS). Pour une plateforme visant à devenir un "ordinateur mondial", ce chiffre est étonnamment bas.

Cependant, les solutions de mise à l'échelle font depuis longtemps partie de la feuille de route d'Ethereum. Plasma est un exemple de solution de mise à l'échelle. Il vise à accroître l'efficacité d'Ethereum, mais la technique peut également être appliquée à d'autres réseaux blockchain.

### Qu'est-ce qu'Ethereum 2.0 ?

Malgré tout son potentiel, Ethereum présente actuellement des limites considérables. Nous avons déjà abordé la question de l'évolutivité. En bref, si Ethereum veut être l'épine dorsale du nouveau système financier, il doit être capable de traiter beaucoup plus de transactions par seconde. Étant donné la nature distribuée du réseau, il s'agit d'un problème extrêmement difficile à résoudre, et les développeurs d'Ethereum y réfléchissent depuis des années.

D'une part, pour que le réseau reste suffisamment décentralisé, des limites doivent être imposées. Plus les exigences pour faire fonctionner un nœud sont élevées, moins il y aura de participants, et plus le réseau sera centralisé. Ainsi, augmenter le nombre de transactions qu'Ethereum peut traiter pourrait menacer l'intégrité du système, car cela augmenterait également la charge sur les nœuds.

Une autre critique à l'égard d'Ethereum (et d'autres crypto-monnaies à preuve de travail) est qu'il est incroyablement gourmand en ressources. Pour réussir à ajouter un bloc à la blockchain, ils doivent exploiter une mine. Or, pour créer un bloc de cette manière, ils doivent effectuer rapidement des calculs qui consomment d'énormes quantités d'électricité.

Pour remédier aux limitations susmentionnées, un ensemble important de mises à niveau a été proposé, connu collectivement sous le nom d'Ethereum 2.0 (ou ETH 2.0). Une fois entièrement déployé, ETH 2.0 devrait améliorer considérablement les performances du réseau.

### Qu'est-ce que le sharding Ethereum ?

Comme mentionné ci-dessus, chaque nœud stocke une copie de la blockchain entière. Chaque fois qu'elle est étendue, chacun des nœuds doit la mettre à jour, ce qui consomme sa bande passante et sa mémoire disponible.

Grâce à une méthode appelée sharding, cela ne sera peut-être plus nécessaire. Ce nom fait référence au processus de division du réseau en sous-ensembles de nœuds - ce sont nos shards. Chacun de ces shards traite ses propres transactions et contrats, mais peut néanmoins communiquer avec le réseau plus large des shards si nécessaire. Comme chaque shard valide indépendamment, il n'est plus nécessaire pour eux de stocker les données des autres shards.

Le sharding est l'une des approches les plus complexes de la mise à l'échelle, dont la conception et la mise en œuvre exigent beaucoup de travail. Cependant, si elle est mise en œuvre avec succès, elle sera également l'une des plus efficaces, augmentant la capacité de débit du réseau de plusieurs ordres de grandeur.

### Qu'est-ce que l'Ethereum Plasma ?

Ethereum Plasma est ce que nous appelons une solution de scalabilité hors chaîne, c'est-à-dire qu'elle vise à augmenter le débit des transactions en les poussant hors de la blockchain. À cet égard, elle présente certaines similitudes avec les chaînes secondaires et les canaux de paiement.

Avec Plasma, les chaînes secondaires sont ancrées dans la blockchain principale d'Ethereum, mais elles limitent la communication au minimum. Elles fonctionnent plus ou moins indépendamment, bien que les utilisateurs s'appuient toujours sur la chaîne principale pour régler les différends ou "terminer" leurs activités sur les chaînes secondaires.

La réduction de la quantité de données que les nœuds doivent stocker est essentielle à la réussite de la mise à l'échelle d'Ethereum. L'approche Plasma permet aux développeurs de décrire le fonctionnement de leurs chaînes "enfants" dans un contrat intelligent sur la chaîne principale. Ils sont ensuite libres de créer des applications contenant des informations ou des processus qui seraient trop coûteux à stocker ou à exécuter sur la chaîne principale.

### Que sont les rollups d'Ethereum ?

Les rollups sont similaires à Plasma dans le sens où ils visent à faire évoluer Ethereum en déplaçant les transactions hors de la blockchain principale. Alors, comment fonctionnent-ils ? 

Un contrat unique sur la chaîne principale détient tous les fonds sur la chaîne secondaire et conserve une preuve cryptographique de l'état actuel de cette chaîne. Les opérateurs de cette chaîne secondaire, qui ont déposé une caution dans le contrat du réseau principal, s'assurent que seules les transitions d'état valides sont engagées dans le contrat du réseau principal. L'idée est que, comme cet état est maintenu hors chaîne, il n'est pas nécessaire de stocker les données sur la blockchain. La principale différence entre les rollups et Plasma réside toutefois dans la manière dont les transactions sont soumises à la chaîne principale. En utilisant un type de transaction spécial, un grand nombre de transactions peuvent être "enroulées" (regroupées) ensemble dans un bloc spécial appelé bloc Rollup.   

Il existe deux types de rollup : Optimiste et ZK Rollup. Les deux garantissent l'exactitude des transitions d'état de différentes manières. 

Les rollups ZK soumettent les transactions en utilisant une méthode de vérification cryptographique appelée preuve à connaissance zéro. Plus précisément, une approche de celle-ci appelée zk-SNARK. Nous n'allons pas entrer dans les détails de son fonctionnement ici, mais voici comment elle peut être utilisée pour les rollups. Il s'agit d'un moyen pour différentes parties de se prouver mutuellement qu'elles disposent d'un élément d'information particulier sans révéler cette information. 

Dans le cas des ZK Rollups, ces informations sont des transitions d'état qui sont soumises à la chaîne principale. Un grand avantage de cette méthode est que ce processus peut se produire presque instantanément et qu'il n'y a pratiquement aucune chance que les états soumis soient corrompus. 

Les Rollups optimistes sacrifient un peu d'extensibilité pour plus de flexibilité. En utilisant une machine virtuelle appelée Optimistic Virtual Machine (OVM), ils permettent aux contrats intelligents de fonctionner sur ces chaînes secondaires. En revanche, il n'y a pas de preuve cryptographique que la transition d'état soumise à la chaîne principale est correcte. Pour atténuer ce problème, un léger délai est prévu pour permettre aux utilisateurs de contester et de rejeter les blocs invalides soumis à la chaîne principale. 

### Qu'est-ce que l'Ethereum Proof of Stake (PoS) ?

Proof of Stake (PoS) est une méthode alternative à Proof of Work pour valider les blocs. Dans un système Proof of Stake, les blocs ne sont pas minés en tant que tels, mais frappés (parfois appelés "forgés"). Au lieu que les mineurs soient en compétition avec la puissance de hachage, un nœud (ou validateur) est périodiquement choisi au hasard pour valider un bloc candidat. S'il le fait correctement, il recevra tous les frais de transaction de ce bloc et, selon le protocole, éventuellement une récompense de bloc.

Puisqu'il n'y a pas d'extraction minière, le système Proof of Stake est considéré comme moins nuisible à l'environnement. Les validateurs ne consomment pas autant d'énergie que les mineurs et peuvent frapper les blocs sur du matériel de qualité grand public.

Il est prévu qu'Ethereum passe de PoW à PoS dans le cadre d'Ethereum 2.0, avec une mise à niveau connue sous le nom de Casper. Bien qu'une date exacte n'ait pas encore été officialisée, la première itération sera probablement lancée en 2020.

### Qu'est-ce que le staking Ethereum ?

Dans les protocoles Proof of Work, la sécurité du réseau est assurée par les mineurs. Les mineurs ne tricheront pas, car cela gaspillerait de l'électricité et leur ferait perdre des récompenses potentielles. Dans le protocole Proof of Stake, cette théorie des jeux n'existe pas, et différentes mesures cryptoéconomiques sont mises en place pour assurer la sécurité du réseau.

Au lieu du risque de gaspillage, ce qui empêche les comportements malhonnêtes est le risque de perdre des fonds. Les validateurs doivent avancer un enjeu (c'est-à-dire une détention de jetons) pour être éligibles à la validation. Il s'agit d'une quantité déterminée d'éther qui est perdue si le nœud tente de tricher, ou qui s'épuise lentement si le nœud ne répond pas ou est hors ligne. Toutefois, si le validateur gère des nœuds supplémentaires, il peut obtenir davantage de récompenses.

## Ethereum et la finance décentralisée (DeFi)

### Qu'est-ce que la finance décentralisée (DeFi) ?

La finance décentralisée (ou simplement, DeFi) est un mouvement qui vise à décentraliser les applications financières. DeFi s'appuie sur des blockchains publiques et open-source auxquelles toute personne disposant d'une connexion Internet peut accéder librement (permissionless). Il s'agit d'un élément crucial pour embarquer des milliards de personnes potentielles dans ce nouveau système financier mondial. 

Dans l'écosystème DeFi en pleine expansion, les utilisateurs interagissent avec les contrats intelligents et entre eux par le biais de réseaux peer-to-peer (P2P) et d'applications décentralisées (DApps). Le grand avantage de DeFi est que, même s'il rend tout cela possible, les utilisateurs restent propriétaires de leurs fonds à tout moment. 

En d'autres termes, le mouvement de la finance décentralisée (DeFi) vise à créer un nouveau système financier libéré des limites du système actuel. Il se trouve qu'en raison de son degré relativement élevé de décentralisation et de sa grande base de développeurs, la majeure partie de DeFi est actuellement construite sur Ethereum.  

### À quoi peut servir la finance décentralisée (DeFi) ?

Vous le savez probablement déjà, mais l'un des grands avantages du bitcoin est qu'aucune partie centrale n'est nécessaire pour coordonner le fonctionnement du réseau. Mais que se passerait-il si nous utilisions cela comme idée de base et que nous créions des applications programmables par-dessus ? C'est le potentiel des applications DeFi. Pas de coordinateurs centraux ou d'intermédiaires, et pas de points de défaillance uniques. 

Comme mentionné ci-dessus, l'un des grands avantages de DeFi est le libre accès. Il y a des milliards de personnes dans le monde qui n'ont pas un bon accès à tout type de services financiers. Pouvez-vous imaginer comment vous géreriez votre quotidien sans aucune certitude quant à vos finances ? Il y a des milliards de personnes qui vivent comme ça, et en fin de compte, c'est le groupe démographique que DeFi essaie de servir.

### La finance décentralisée (DeFi) atteindra-t-elle un jour le grand public ?

Tout cela semble génial, alors pourquoi DeFi n'a-t-il pas encore envahi le monde ? Eh bien, actuellement, la plupart des applications DeFi sont difficiles à utiliser, maladroites, cassent fréquemment et sont très expérimentales. Il s'avère que la conception même des cadres de cet écosystème est extrêmement difficile, surtout dans un environnement de développement distribué.

Résoudre tous les défis de la construction de l'écosystème DeFi est un long chemin à parcourir pour les ingénieurs logiciels, les théoriciens des jeux, les concepteurs de mécanismes, et bien d'autres. En tant que tel, il reste à voir si les applications DeFi parviendront un jour à être adoptées par le grand public.

### Quelles sont les applications de la finance décentralisée (DeFi) ?

L'un des cas d'utilisation les plus populaires de la finance décentralisée (DeFi) est celui des monnaies stables. Il s'agit essentiellement de jetons sur une blockchain dont la valeur est liée à un actif du monde réel, comme une monnaie fiduciaire. Par exemple, BUSD est lié à la valeur de l'USD. Ce qui rend ces jetons pratiques à utiliser, c'est que, comme ils existent sur une blockchain, ils sont très faciles à stocker et à transférer.

Un autre type d'application populaire est le prêt. Il existe de nombreux services peer-to-peer (P2P) qui vous permettent de prêter vos fonds à d'autres personnes et de percevoir des intérêts en retour. En fait, l'une des façons les plus simples de le faire est de recourir à Binance Lending. Tout ce que vous avez à faire est de transférer vos fonds vers votre portefeuille de prêt, et vous pouvez commencer à gagner des intérêts dès le lendemain !

Cependant, la partie la plus excitante de DeFi est sans doute les applications qui sont difficiles à catégoriser. Il peut s'agir de toutes sortes de marchés décentralisés de pair à pair, où les utilisateurs peuvent échanger des crypto-objets de collection uniques et d'autres articles numériques. Elles peuvent également permettre la création d'actifs synthétiques, où chacun peut créer un marché pour à peu près tout ce qui a de la valeur. Parmi les autres utilisations possibles, citons les marchés prédictifs, les produits dérivés et bien d'autres encore.

### Bourses décentralisées (DEX) sur Ethereum

Un échange décentralisé (DEX) est un lieu qui permet aux transactions de s'effectuer directement entre les portefeuilles des utilisateurs. Lorsque vous négociez sur Binance, une bourse centralisée, vous envoyez vos fonds à Binance et vous négociez via ses systèmes internes.

Les bourses décentralisées sont différentes. Grâce à la magie des contrats intelligents, elles vous permettent de négocier directement à partir de votre portefeuille de crypto-monnaies, éliminant ainsi la possibilité de piratage de la bourse et d'autres risques.

Binance DEX est un excellent exemple de bourse décentralisée. D'autres exemples notables construits sur Ethereum sont Uniswap, Kyber Network et IDEX. Beaucoup d'entre eux vous permettront même de négocier à partir d'un portefeuille matériel pour une sécurité maximale.

Ci-dessus, nous avons illustré les différences entre les échanges centralisés et décentralisés. À gauche, nous pouvons voir que Binance se situe au milieu des transactions entre les utilisateurs. Ainsi, si Alice souhaite échanger le Token A contre le Token B de Bob, elle doit d'abord déposer ses actifs sur la bourse. Après l'échange, Binance réaffectera leurs soldes en conséquence.

À droite, cependant, se trouve un échange décentralisé. Vous remarquerez qu'il n'y a pas de tierce partie impliquée dans la transaction. Au lieu de cela, le jeton d'Alice est directement échangé contre celui de Bob en utilisant un contrat intelligent. De cette façon, aucune des parties n'a besoin de faire confiance à un intermédiaire, car les termes de leur contrat sont automatiquement exécutoires.

En février 2020, les DEX sont généralement les applications les plus utilisées sur la blockchain Ethereum. Toutefois, le volume d'échanges par rapport aux bourses centralisées est encore faible. Néanmoins, si les développeurs et les concepteurs de DEX étoffent l'expérience utilisateur pour la rendre plus accueillante, les DEX pourraient rivaliser avec les bourses centralisées à l'avenir.

## Participer au réseau Ethereum

### Qu'est-ce qu'un nœud Ethereum ?

"Ethereum node" est un terme qui peut être utilisé pour décrire un programme qui interagit avec le réseau Ethereum d'une certaine manière. Un nœud Ethereum peut être n'importe quoi, d'une simple application de portefeuille de téléphone mobile à un ordinateur qui stocke une copie entière de la blockchain. 

Tous les nœuds fonctionnent comme un point de communication d'une manière ou d'une autre, mais il existe différents types de nœuds sur le réseau Ethereum.

### Comment fonctionne un nœud Ethereum ?

Ethereum, contrairement à Bitcoin, n'a pas un seul programme comme implémentation de référence. Alors que l'écosystème Bitcoin a Bitcoin Core comme principal logiciel de nœud, Ethereum a une gamme de programmes individuels (mais compatibles) basés sur son Livre Jaune. Les options populaires comprennent Geth et Parity.

### Nœuds complets Ethereum

Pour vous interfacer avec le réseau Ethereum d'une manière qui vous permette de valider les données de la blockchain de façon indépendante, vous devez exécuter un nœud complet à l'aide d'un logiciel comme ceux mentionnés ci-dessus. 

Le logiciel téléchargera des blocs à partir d'autres nœuds et vérifiera si les transactions incluses sont correctes. Il exécutera également tous les contrats intelligents qui ont été appelés pour s'assurer que vous recevez les mêmes informations que les autres pairs. Si tout fonctionne comme prévu, on peut s'attendre à ce que chaque nœud ait une copie identique de la blockchain sur son ordinateur.

Les nœuds complets sont essentiels au fonctionnement d'Ethereum. Sans de multiples nœuds répartis dans le monde entier, le réseau perdrait ses propriétés de résistance à la censure et de décentralisation.

### Nœuds légers Ethereum

L'exploitation d'un nœud complet vous permet de contribuer directement à la santé et à la sécurité du réseau. Mais un nœud complet nécessite souvent une machine séparée pour fonctionner ainsi qu'une maintenance occasionnelle. Les nœuds légers pourraient être une meilleure option pour les utilisateurs qui ne sont pas en mesure de faire fonctionner un nœud complet (ou qui préfèrent simplement ne pas le faire).

Comme leur nom l'indique, les nœuds légers sont légers : ils utilisent moins de ressources et occupent un espace minimal. En tant que tels, ils peuvent fonctionner sur des appareils de moindre qualité, comme les téléphones ou les ordinateurs portables. Mais ces faibles frais généraux ont un coût : les nœuds légers ne sont pas entièrement autonomes. Ils ne synchronisent pas la blockchain dans son intégralité et ont donc besoin que les nœuds complets leur fournissent des informations pertinentes.

Les nœuds légers sont populaires parmi les marchands, les services et les utilisateurs. Ils sont largement utilisés pour effectuer et recevoir des paiements dans des scénarios où les nœuds complets sont jugés inutiles et trop coûteux à gérer.

### Nœuds miniers Ethereum

Un nœud minier peut être soit un client complet, soit un client léger. Le terme "nœud minier" n'est pas vraiment utilisé comme il l'est dans l'écosystème Bitcoin, mais il est néanmoins utile d'identifier ces participants.

Pour miner de l'Ethereum, les utilisateurs ont besoin de matériel supplémentaire. Une pratique courante consiste à construire une plateforme de minage. Avec ce matériel, les utilisateurs connectent plusieurs GPU (processeurs graphiques) pour hacher des données à grande vitesse.

Les mineurs ont deux options : le minage en solo ou dans un pool de minage. Le minage en solo signifie que le mineur travaille seul pour créer des blocs. S'il réussit, il ne partage pas ses récompenses avec qui que ce soit. En revanche, s'il rejoint un pool minier, il combine sa puissance de hachage avec celle d'autres utilisateurs. Il aura ainsi plus de chances de trouver un bloc, mais il devra également partager ses récompenses avec les membres du pool.

### Comment faire fonctionner un nœud Ethereum

L'un des grands aspects des blockchains est l'accès ouvert. Cela signifie que tout le monde peut faire fonctionner un nœud Ethereum et renforcer le réseau en validant les transactions et les blocs. 

Comme pour le Bitcoin, il existe un certain nombre d'entreprises qui proposent des nœuds Ethereum prêts à l'emploi. C'est peut-être la meilleure option si vous souhaitez simplement mettre en place un nœud et le faire fonctionner - cependant, soyez prêt à payer un supplément pour cette commodité.

Comme nous l'avons mentionné, Ethereum dispose d'un certain nombre d'implémentations logicielles de nœuds différentes, telles que Geth ou Parity. Si vous souhaitez exécuter votre propre nœud, vous devrez vous familiariser avec le processus de configuration de l'implémentation que vous choisissez d'exécuter.

À moins que vous ne souhaitiez exécuter un nœud spécial appelé nœud d'archivage, un ordinateur portable de qualité grand public devrait suffire pour exécuter un nœud complet Ethereum. En même temps, il est préférable de ne pas utiliser votre machine de tous les jours, car cela pourrait la ralentir considérablement. 

L'exécution de votre propre nœud fonctionne mieux sur les appareils qui peuvent toujours être en ligne. Si votre nœud est déconnecté, il peut prendre un temps considérable pour se synchroniser avec le réseau une fois qu'il est de nouveau en ligne. Ainsi, les meilleures solutions sont des dispositifs peu coûteux à construire et faciles à entretenir. Par exemple, vous pouvez faire fonctionner un nœud léger même sur un Raspberry Pi.

### Comment miner sur Ethereum

Comme le réseau va bientôt passer à la méthode Proof of Stake, le minage sur Ethereum n'est pas le pari le plus sûr à long terme. Une fois la transition effectuée, les mineurs d'Ethereum orienteront probablement leur équipement minier vers un autre réseau ou le vendront entièrement.

Malgré tout, si vous souhaitez participer au minage d'Ethereum, vous aurez besoin de matériel spécialisé, comme des GPU ou des ASIC. Si vous recherchez des rendements raisonnables, vous aurez très probablement besoin d'une installation de minage personnalisée et d'un accès à de l'électricité bon marché. En outre, vous devrez mettre en place un portefeuille Ethereum et configurer le logiciel de minage pour l'utiliser. Tout cela exige un investissement important en temps et en argent, alors demandez-vous bien si vous êtes prêt à relever le défi. 

### Qu'est-ce que l'Ethereum ProgPoW ?

ProgPoW est l'acronyme de Programmatic Proof of Work (preuve de travail programmée). Il s'agit d'une proposition d'extension de l'algorithme de minage Ethereum, Ethash, qui vise à rendre les GPU plus compétitifs par rapport aux ASIC. 

La résistance aux ASIC est un sujet très débattu depuis des années dans les communautés Bitcoin et Ethereum. Dans le cas de Bitcoin, les ASIC sont devenus la force minière dominante sur le réseau. 

Sur Ethereum, cependant, les ASIC sont présents mais beaucoup moins importants - une partie considérable des mineurs utilisent toujours des GPU. Cette situation pourrait toutefois changer bientôt, car de plus en plus de sociétés mettent sur le marché des mineurs ASIC pour Ethereum. Mais pourquoi les ASIC pourraient-ils poser un problème ? 

Tout d'abord, les ASIC pourraient réduire considérablement la décentralisation du réseau. Si les mineurs GPU ne sont pas rentables et doivent fermer leurs opérations minières, le taux de hachage pourrait se concentrer entre les mains d'une poignée de mineurs seulement. De plus, le développement de puces ASIC est coûteux, et seules quelques entreprises ont les capacités et les ressources pour le faire. Cela crée une menace de monopolisation du côté de la fabrication en centralisant potentiellement l'industrie minière d'Ethereum entre les mains de quelques sociétés.

L'intégration de ProgPow est un sujet de controverse depuis 2018. Alors que certains pensent qu'elle pourrait être saine pour l'écosystème Ethereum, d'autres s'y opposent en raison de la possibilité qu'elle provoque un hard fork. Avec la transition à venir vers le Proof of Stake, il reste à voir si ProgPow sera un jour implémenté sur le réseau.

### Qui développe le logiciel Ethereum ?

Comme le bitcoin, Ethereum est un logiciel libre. Chacun est libre de participer au développement du protocole lui-même ou de créer des applications à partir de celui-ci. En fait, Ethereum possède actuellement la plus grande communauté de développeurs dans l'espace blockchain.

### Qu'est-ce que Solidity ?

Les contrats intelligents ont été décrits pour la première fois dans les années 1990, mais leur mise en œuvre sur des blockchains a posé une toute nouvelle série de défis. Solidity a été proposé en 2014 par Gavin Wood, et est devenu depuis le principal langage de programmation pour le développement de contrats intelligents sur Ethereum. D'un point de vue syntaxique, il ressemble à Java, JavaScript et C++.

Essentiellement, Solidity permet aux développeurs d'écrire du code qui peut être décomposé en instructions que la machine virtuelle Ethereum (EVM) peut comprendre. Si vous souhaitez mieux comprendre son fonctionnement, le GitHub de Solidity est un bon point de départ.

Il convient de noter que Solidity n'est pas le seul langage disponible pour les développeurs Ethereum. Une autre option populaire est Vyper, qui ressemble davantage à Python dans sa syntaxe.