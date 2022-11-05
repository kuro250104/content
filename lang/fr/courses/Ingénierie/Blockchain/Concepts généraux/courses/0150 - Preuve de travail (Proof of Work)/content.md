La preuve de travail (communément abrégée en *PoW - Proof of Work*) est un mécanisme permettant d'éviter les doubles dépenses. La plupart des principales crypto-monnaies l'utilisent comme algorithme de consensus. C'est ce qu'on appelle une méthode pour sécuriser le grand livre de la crypto-monnaie.

L'algorithme Proof of Work a été le premier algorithme de consensus à faire surface et, à ce jour, il reste le principal. Il a été introduit par Satoshi Nakamoto dans le livre blanc du Bitcoin de 2008, mais la technologie elle-même a été conçue bien avant. 

HashCash d'Adam Back est un exemple précoce d'algorithme de preuve de travail à l'époque pré-cryptocurrency. En exigeant des expéditeurs qu'ils effectuent une petite quantité de calcul avant d'envoyer un courriel, les destinataires pouvaient limiter le spam. Ce calcul ne coûterait pratiquement rien à un expéditeur légitime, mais s'accumulerait rapidement pour quelqu'un qui envoie des courriels en masse.

## Qu'est-ce qu'une double dépense ?

On parle de double dépense lorsque les mêmes fonds sont dépensés plus d'une fois. Ce terme est utilisé presque exclusivement dans le contexte de l'argent numérique - après tout, vous auriez du mal à dépenser deux fois le même argent physique. Lorsque vous payez un café aujourd'hui, vous remettez de l'argent liquide à un caissier qui l'enferme probablement dans une caisse. Vous ne pouvez pas aller au café d'en face et payer un autre café avec la même facture.

Dans les systèmes d'argent liquide numérique, il y a une possibilité que vous puissiez le faire. Vous avez sûrement déjà dupliqué un fichier informatique - il suffit de le copier et de le coller. Vous pouvez envoyer le même fichier par e-mail à dix, vingt ou cinquante personnes. 

Puisque la monnaie numérique n'est que des données, vous devez empêcher les gens de copier et de dépenser les mêmes unités à différents endroits. Sinon, votre monnaie s'effondrera en un rien de temps. 

## Pourquoi la preuve du travail est-elle nécessaire ?

Si vous avez lu notre guide de la technologie blockchain, vous savez que les utilisateurs diffusent des transactions sur le réseau. Ces transactions ne sont cependant pas immédiatement considérées comme valides. Cela ne se produit que lorsqu'elles sont ajoutées à la blockchain. 

La blockchain est une grande base de données que chaque utilisateur peut consulter et qui lui permet de vérifier si des fonds ont déjà été dépensés. Imaginez la situation suivante : vous et trois amis avez un bloc-notes. Chaque fois que l'un d'entre vous souhaite effectuer un transfert des unités que vous utilisez, vous l'écrivez : Alice paie cinq unités à Bob, Bob paie deux unités à Carol, etc.

Il y a une autre complexité : chaque fois que vous effectuez une transaction, vous faites référence à la transaction d'où proviennent les fonds. Ainsi, si Bob payait Carol avec deux unités, l'entrée ressemblerait en fait à ce qui suit : Bob paie à Carole deux unités provenant de cette transaction précédente avec Alice.

Maintenant, nous avons un moyen de suivre les unités. Si Bob essaie d'effectuer une autre transaction en utilisant les mêmes unités que celles qu'il vient d'envoyer à Carol, tout le monde le saura immédiatement. Le groupe ne permettra pas que la transaction soit ajoutée au bloc-notes.

Maintenant, cela pourrait bien fonctionner dans un petit groupe. Tout le monde se connaît, et ils se mettront probablement d'accord sur qui, parmi leurs amis, doit ajouter les transactions au bloc-notes. Mais qu'en est-il si nous voulons un groupe de 10 000 participants ? L'idée du bloc-notes n'est pas très évolutive, car personne ne veut faire confiance à un étranger pour le gérer.

C'est là que la preuve de travail entre en jeu. Elle garantit que les utilisateurs ne dépensent pas de l'argent qu'ils n'ont pas le droit de dépenser. En utilisant une combinaison de théorie des jeux et de cryptographie, un algorithme PoW permet à quiconque de mettre à jour la blockchain conformément aux règles du système.

## Comment fonctionne le PoW ?

Notre bloc-notes ci-dessus est la blockchain. Mais nous n'ajoutons pas les transactions une par une - au lieu de cela, nous les regroupons en blocs. Nous annonçons les transactions au réseau, puis les utilisateurs qui créent un bloc les incluent dans un bloc candidat. Les transactions ne seront considérées comme valides que lorsque leur bloc candidat sera devenu un bloc confirmé, c'est-à-dire qu'il aura été ajouté à la blockchain.

L'ajout d'un bloc n'est cependant pas bon marché. La preuve de travail exige qu'un mineur (l'utilisateur qui crée le bloc) utilise certaines de ses propres ressources pour obtenir ce privilège. Cette ressource est la puissance de calcul, qui est utilisée pour hacher les données du bloc jusqu'à ce qu'une solution à un puzzle soit trouvée.

Le hachage des données du bloc signifie que vous les faites passer par une fonction de hachage pour générer un hachage de bloc. Le hachage du bloc fonctionne comme une "empreinte digitale" : il s'agit d'une identité pour vos données d'entrée et elle est unique pour chaque bloc.

Il est pratiquement impossible d'inverser un bloc de hachage pour obtenir les données d'entrée. En revanche, si vous connaissez les données d'entrée, il vous est facile de confirmer que le hachage est correct. Il vous suffit de soumettre l'entrée à la fonction et de vérifier si la sortie est la même.

Dans Proof of Work, vous devez fournir des données dont le hachage correspond à certaines conditions. Mais vous ne savez pas comment y parvenir. Votre seule option est de faire passer vos données par une fonction de hachage et de vérifier si elles correspondent aux conditions. Si ce n'est pas le cas, vous devrez modifier légèrement vos données pour obtenir un hachage différent. Si vous changez ne serait-ce qu'un seul caractère dans vos données, vous obtiendrez un résultat totalement différent, et il n'y a donc aucun moyen de prédire ce que pourrait être le résultat.

Par conséquent, si vous voulez créer un bloc, vous jouez aux devinettes. En général, vous prenez des informations sur toutes les transactions que vous voulez ajouter et d'autres données importantes, puis vous hachurez le tout. Mais comme votre ensemble de données ne changera pas, vous devez ajouter une information qui est variable. Sinon, vous obtiendrez toujours le même hachage en sortie. Ces données variables sont ce que nous appelons un nonce. C'est un nombre que vous changerez à chaque tentative, de sorte que vous obtiendrez un hachage différent à chaque fois. Et c'est ce qu'on appelle le minage.

Pour les principales crypto-monnaies actuelles, les conditions sont incroyablement difficiles à satisfaire. Plus le taux de hachage est élevé sur le réseau, plus il est difficile de trouver un hachage valide. Ceci est fait pour s'assurer que les blocs ne sont pas trouvés trop rapidement.

Comme vous pouvez l'imaginer, essayer de deviner des quantités massives de hachages peut être coûteux pour votre ordinateur. Vous gaspillez des cycles de calcul et de l'électricité. Mais le protocole vous récompensera en crypto-monnaies si vous trouvez un hachage valide.

Récapitulons ce que nous savons jusqu'à présent :

- C'est cher pour vous de miner.
- Vous êtes récompensé si vous produisez un bloc valide.
- En connaissant une entrée, un utilisateur peut facilement vérifier son hachage - les utilisateurs non mineurs peuvent vérifier qu'un bloc est valide sans dépenser beaucoup de puissance de calcul.

Jusqu'ici, tout va bien. Mais que se passe-t-il si vous essayez de tricher ? Qu'est-ce qui vous empêche d'introduire un ensemble de transactions frauduleuses dans le bloc et de produire un hachage valide ?

C'est là que la cryptographie à clé publique entre en jeu. Nous n'entrerons pas dans les détails dans ce cours. En bref, nous utilisons des astuces cryptographiques astucieuses qui permettent à tout utilisateur de vérifier si quelqu'un a le droit de déplacer les fonds qu'il tente de dépenser.

Lorsque vous créez une transaction, vous la signez. N'importe qui sur le réseau peut comparer votre signature avec votre clé publique et vérifier si elles correspondent. Ils vérifieront également si vous pouvez réellement dépenser vos fonds et si la somme de vos entrées est supérieure à la somme de vos sorties (c'est-à-dire que vous ne dépensez pas plus que ce que vous avez).

Tout bloc qui comprend une transaction invalide sera automatiquement rejeté par le réseau. Il est coûteux pour vous de ne serait-ce qu'essayer de tricher. Vous gaspillerez vos propres ressources sans aucune récompense.

C'est là que réside la beauté de la preuve de travail : il est coûteux de tricher, mais rentable d'agir honnêtement. Tout mineur rationnel cherchera à obtenir un retour sur investissement, on peut donc s'attendre à ce qu'il se comporte de manière à garantir des revenus.

## Preuve de travail ou preuve d'enjeu ?

Il existe de nombreux algorithmes de consensus, mais l'un des plus attendus est la Preuve d’Enjeu (*PoS - Proof of Stake*). Le concept remonte à 2011 et a été mis en œuvre dans certains protocoles plus petits. Mais il n'a encore été adopté par aucune des grandes blockchains.

Dans les systèmes Proof of Stake, les mineurs sont remplacés par des validateurs. Il n'y a pas de minage et pas de course pour deviner les hachages. Au lieu de cela, les utilisateurs sont sélectionnés au hasard. S'ils sont choisis, ils doivent proposer (ou "forger") un bloc. Si le bloc est valide, ils recevront une récompense composée des frais des transactions du bloc.

Cependant, n'importe quel utilisateur ne peut pas être sélectionné - le protocole les choisit en fonction d'un certain nombre de facteurs. Pour être éligibles, les participants doivent bloquer un enjeu, qui est un montant prédéterminé de la monnaie native de la blockchain. La mise fonctionne comme une caution : tout comme les accusés versent une grosse somme d'argent pour les dissuader de se soustraire au procès, les validateurs bloquent une mise pour les dissuader de tricher. S'ils agissent de manière malhonnête, leur mise (ou une partie de celle-ci) sera prise.

Le système Proof of Stake présente certains avantages par rapport au système Proof of Work. Le plus notable est la réduction de l'empreinte carbone : comme il n'est pas nécessaire de disposer de fermes d'extraction très puissantes dans le cas du PoS, l'électricité consommée ne représente qu'une fraction de celle consommée dans le cas du PoW. 

Cela dit, le bilan de la PoS est loin d'être aussi bon que celui de la PoW. Bien qu'il puisse être perçu comme un gaspillage, le minage est le seul algorithme de consensus qui a fait ses preuves à l'échelle. En un peu plus d'une décennie, il a permis de sécuriser des transactions d'une valeur de plusieurs milliers de milliards de dollars. Pour dire avec certitude si le PoS peut rivaliser avec sa sécurité, le jalonnement doit être testé correctement dans la nature. 

## Conclusion

La preuve de travail était la solution originale au problème de double dépense et s'est avérée fiable et sûre. Le bitcoin a prouvé que nous n'avions pas besoin d'entités centralisées pour empêcher que les mêmes fonds soient dépensés deux fois. Grâce à une utilisation intelligente de la cryptographie, des fonctions de hachage et de la théorie des jeux, les participants d'un environnement décentralisé peuvent se mettre d'accord sur l'état d'une base de données financières.