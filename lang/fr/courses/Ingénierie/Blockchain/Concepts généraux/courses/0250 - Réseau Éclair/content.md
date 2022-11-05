## Introduction

Les crypto-monnaies ont des propriétés assez uniques. Elles ne peuvent pas être piratées ou fermées facilement, et tout le monde peut les utiliser pour transmettre de la valeur dans le monde entier sans l'intervention d'un tiers.

Pour garantir le maintien de ces caractéristiques, des compromis importants doivent être faits. Étant donné que de nombreux nœuds sont chargés de faire fonctionner un réseau de crypto-monnaies, le débit est limité. Par conséquent, le nombre de transactions par seconde (TPS) qu'un réseau blockchain peut traiter est relativement faible pour une technologie qui vise à être adoptée par les masses.

Pour surmonter les limites inhérentes à la technologie blockchain, un certain nombre de solutions d'évolutivité ont été proposées pour augmenter le nombre de transactions qu'un réseau peut traiter. Dans cet article, nous allons nous plonger dans le Lightning Network, une de ces extensions du protocole Bitcoin.

## Qu'est-ce que le réseau Éclair ?

Le réseau éclair (*Lightning Network*) est un réseau qui se trouve au-dessus d'une blockchain pour faciliter les transactions rapides entre pairs. Il n'est pas exclusif au bitcoin - d'autres crypto-monnaies comme le Litecoin l'ont intégré.

Vous vous demandez peut-être ce que nous entendons par "se trouve au-dessus d'une blockchain". Le Lightning Network est ce que l'on appelle une solution hors chaîne ou de niveau 2. Il permet aux individus d'effectuer des transactions sans avoir à enregistrer chaque transaction sur la blockchain.

Le Lightning Network est distinct du réseau Bitcoin - il possède ses propres nœuds et logiciels, mais il communique néanmoins avec la chaîne principale. Pour entrer ou sortir du Lightning Network, vous devez créer des transactions spéciales sur la blockchain.

Ce que vous faites en fait avec votre première transaction est de construire une sorte de contrat intelligent avec un autre utilisateur. Nous entrerons bientôt dans les détails - pour l'instant, imaginez que le contrat intelligent détient un grand livre privé avec l'autre utilisateur. Vous pouvez écrire de nombreuses transactions dans ce registre. Elles ne sont visibles que pour vous et votre contrepartie, mais aucun de vous ne peut tricher en raison de certaines caractéristiques particulières de la configuration.

Ce mini-registre est appelé un canal. Disons que Jane et Tarzan ont mis 5 BTC chacun dans le contrat intelligent. Dans leur canal, ils ont maintenant tous les deux un solde de 5 BTC. Jane pourrait alors écrire dans le grand livre pour payer 1 BTC à Tarzan. Tarzan a maintenant 6 BTC de son côté, et Jane en a 4. Ensuite, Tarzan pourrait renvoyer 2 BTC à Jane à une date ultérieure, mettant à jour les soldes à 6 BTC du côté d'Jane et 4 BTC du côté de Tarzan. Ils peuvent continuer à faire cela pendant un certain temps.

À tout moment, l'un ou l'autre peut publier l'état actuel du canal sur la blockchain. À ce moment-là, les soldes de chaque côté du canal sont alloués à leurs parties respectives sur la chaîne.

Comme son nom l'indique, les transactions Lightning sont rapides comme l'éclair. Il n'y a pas de confirmation de bloc à attendre - les paiements peuvent être effectués aussi vite que le permet votre connexion Internet.

## Pourquoi le Lightning Network est-il nécessaire ?

Jusqu'à présent, le Lightning Network (ou plus simplement LN) semble être l'approche la plus raisonnable pour mettre à l'échelle la blockchain Bitcoin. La coordination des changements dans un écosystème aussi vaste est délicate - il y a un risque de hard forks et de bugs potentiellement catastrophiques. Avec autant de valeur en jeu, l'expérimentation est incroyablement dangereuse.

Lorsque vous déplacez cette expérimentation hors de la blockchain, vous disposez de beaucoup plus de flexibilité. Si quelque chose ne va pas, cela n'aura aucun impact sur le réseau Bitcoin actuel. Les solutions de niveau 2 ne remettent pas en cause les hypothèses de sécurité qui ont permis au protocole de fonctionner pendant plus de 10 ans.

Il n'y a pas non plus d'obligation de changer l'ancienne façon de faire les choses. Les transactions sur la chaîne continuent de fonctionner normalement pour l'utilisateur final, mais il a désormais la possibilité d'effectuer des transactions hors chaîne également.

L'utilisation du Lightning Network présente plusieurs avantages. Nous allons en examiner les principaux ci-dessous. 

### Évolutivité

Les blocs de bitcoins sont créés toutes les dix minutes environ et ne peuvent contenir qu'un nombre limité de transactions. L'espace dans les blocs est une ressource rare. Vous devez donc faire une offre aux autres utilisateurs pour que la vôtre soit incluse en temps voulu. Les mineurs se soucient avant tout d'être payés, c'est pourquoi ils incluent d'abord les transactions dont les frais sont les plus élevés.

Lorsque peu d'utilisateurs essaient d'envoyer des fonds en même temps, ce n'est pas vraiment un problème. Vous pouvez fixer des frais peu élevés et vous avez de bonnes chances que la transaction soit incluse dans le bloc suivant. Mais lorsque tout le monde diffuse des transactions en même temps, les frais moyens peuvent augmenter considérablement. À quelques occasions, ils ont dépassé les 5 $, et au plus fort du marché haussier de 2017, ils ont dépassé les 50 $.

### Frais moyens de transaction en bitcoins (en USD)

Ces frais peuvent sembler insignifiants pour des transactions portant sur des milliers de dollars en bitcoins, mais pour les petits paiements, ils ne sont pas viables. Qui veut payer un café à 3 dollars avec des frais de 5 dollars ?

Avec le réseau Lightning, vous payez toujours deux frais - un pour ouvrir votre canal, et un autre pour le fermer. Mais vous et votre contrepartie pouvez effectuer des milliers de transactions gratuitement une fois le canal ouvert. Une fois que vous avez terminé, il vous suffit de publier l'état final sur la blockchain.

Dans l'ensemble, si davantage d'utilisateurs ont recours à des solutions hors chaîne comme le Lightning Network, l'espace de blocs sera utilisé plus efficacement. Les transferts de faible valeur et à haute fréquence pourraient être effectués dans les canaux de paiement, tandis que l'espace de bloc est utilisé pour les transactions plus importantes et l'ouverture/la fermeture des canaux. Le système serait ainsi accessible à une base d'utilisateurs beaucoup plus large, ce qui lui permettrait d'évoluer à long terme.

### Micropaiements

Il y a un montant minimum de bitcoins que vous pouvez envoyer dans une transaction - environ 0,00000546 BTC. Au moment de la rédaction de cet article, cela équivaut à environ quatre cents. C'est un petit montant, mais le réseau Lightning vous permet de repousser les limites pour effectuer une transaction dans la plus petite unité actuellement disponible, à savoir 0,00000001 BTC, ou un satoshi.

Lightning est beaucoup plus attrayant pour les micropaiements. Les frais sur les transactions régulières rendent peu pratique l'envoi de petits montants sur la chaîne principale. En revanche, au sein d'un canal, vous êtes libre d'envoyer gratuitement une fraction de fraction de bitcoin.

Les micropaiements sont adaptés à de nombreux cas d'utilisation. Certains pensent qu'ils pourraient remplacer avantageusement les modèles d'abonnement, dans lesquels les utilisateurs paient de petites sommes chaque fois qu'ils utilisent un service.

### Confidentialité

Un avantage secondaire du réseau Lightning est qu'il peut offrir aux utilisateurs un haut degré de confidentialité. Les parties n'ont pas besoin de faire connaître leurs canaux à l'ensemble du réseau. Si vous pouvez regarder la blockchain et dire que cette transaction a ouvert un canal, vous ne pourrez pas nécessairement savoir ce qui s'y passe. Si les participants choisissent de rendre leur canal privé, ils seront les seuls à savoir quelles transactions ont lieu.

Si Jane a un canal avec Tarzan et que Tarzan a un canal avec Adeline, Jane et Adeline peuvent s'envoyer des paiements via Tarzan. Si Dan est connecté à Adeline, Jane peut lui envoyer des paiements. Vous pouvez imaginer que cela se développe en un réseau tentaculaire de canaux de paiement interconnectés. Dans une telle configuration, vous ne pourriez pas être sûr de savoir à qui Jane a envoyé des fonds une fois que le canal est fermé.

## Comment fonctionne le Lightning Network ?

Nous avons expliqué comment le Lightning Network s'appuie sur les canaux entre les nœuds à un niveau élevé. Jetons maintenant un coup d'œil sous le capot.

### Adresses multisignatures

Une adresse multisignature (ou multisig) est une adresse à partir de laquelle plusieurs clés privées peuvent dépenser. Lorsque vous en créez une, vous spécifiez combien de clés privées peuvent dépenser les fonds, et combien de ces clés sont nécessaires pour signer une transaction. Par exemple, un schéma 1 sur 5 signifie que cinq clés peuvent produire une signature valide et qu'une seule est nécessaire. Un schéma 2-of-3 indique que, sur les trois clés possibles, deux sont nécessaires pour dépenser les fonds.

Pour initialiser un canal Lightning, les participants bloquent les fonds selon un schéma 2 de 2. Il n'y a que deux clés privées capables de signer, et les deux sont nécessaires pour déplacer les pièces. Revenons à nos amis Jane et Tarzan à ce stade. Ils vont devoir effectuer de nombreux paiements l'un envers l'autre dans les mois à venir, et ils décident donc d'ouvrir un canal Lightning Network.

Pour commencer, ils déposent tous les deux, disons, 3 BTC chacun sur l'adresse multisig détenue conjointement. Il est utile de rappeler que Tarzan ne peut pas sortir des fonds de l'adresse sans l'accord d'Jane, et vice versa. 

Maintenant, ils pourraient simplement garder une feuille de papier qui ajuste les soldes de chaque côté. Tous deux ont un solde de départ de 3 BTC. Si Jane veut faire un paiement de 1 BTC à Tarzan, pourquoi ne pas simplement noter qu'Jane possède maintenant 2 BTC et Tarzan 4 BTC ? Les soldes pourraient être suivis de cette manière jusqu'à ce qu'ils décident de sortir les fonds.

C'est possible, mais où est le plaisir ? Plus important encore, cela ne rend-il pas incroyablement facile pour quelqu'un de ne pas coopérer ? Si Jane se retrouve avec 6 BTC et Tarzan sans, ce dernier ne perd rien en refusant de débloquer les fonds (sauf, peut-être, son amitié avec Jane).

### Contrats HTLC (Hash Timelock Contracts)

Le système ci-dessus est ennuyeux et n'offre pas beaucoup plus que les configurations de confiance actuelles. Il devient beaucoup plus intéressant lorsque nous introduisons un mécanisme qui fait respecter le "contrat" entre Jane et Tarzan. Si l'une des parties décide de ne pas respecter les règles du jeu, l'autre a toujours un recours pour sortir ses fonds du canal.

Ce mécanisme est un contrat de hachage temporel (ou HTLC). Ce terme peut sembler intimidant, mais il s'agit en fait d'un concept assez simple à comprendre. Il marie deux autres technologies (hashlocks et timelocks) pour remédier à tout comportement non coopératif dans les canaux de paiement.

Un hashlock est une condition placée sur une transaction dictant que vous ne pouvez dépenser des fonds qu'en prouvant que vous connaissez un secret. L'expéditeur hachète un élément de données et inclut le hachage dans la transaction vers le récepteur. Le destinataire ne peut dépenser l'argent que s'il fournit les données originales (le secret) qui correspondent au hachage. Et la seule façon pour lui de fournir ces données est que l'expéditeur les lui donne.

Un timelock est une condition qui vous empêche de dépenser des fonds avant un certain temps. Elle est spécifiée soit sous la forme d'une heure réelle, soit sous la forme d'une hauteur de bloc spécifiée.

Les HTLC sont créées en combinant des hashlocks et des timelocks. En pratique, les HTLC peuvent être utilisées pour créer des paiements conditionnels - le destinataire doit fournir un secret avant une certaine heure, ou l'expéditeur peut récupérer les fonds. La partie suivante est probablement mieux expliquée avec un exemple, alors revenons à Jane et Tarzan.

### Ouverture et fermeture des canaux

Nous avons donné l'exemple d'Jane et Tarzan qui viennent de créer des transactions qui financent l'adresse multisignature qu'ils vont partager. Mais ces transactions ne sont pas encore publiées sur la blockchain ! Nous devons d'abord faire une dernière chose.

#### Trois pièces de Tarzan et trois pièces d'Jane.

N'oubliez pas que ces pièces ne peuvent sortir du multisig que si Jane et Tarzan signent conjointement une transaction. Si Jane voulait envoyer les six pièces à une adresse externe, elle aurait besoin de l'accord de Tarzan. Elle doit d'abord créer une transaction (six bitcoins à cette adresse) et ajouter sa propre signature. 

Elle pourrait essayer de diffuser la transaction immédiatement, mais elle ne serait pas valide car Tarzan n'a pas inclus sa signature. Jane doit d'abord lui remettre la transaction incomplète. Une fois qu'il a ajouté sa signature, elle devient valide.

Nous n'avons toujours pas mis en place un mécanisme permettant à chacun de jouer honnêtement. Comme nous l'avons dit précédemment, si votre contrepartie refuse de coopérer, vos fonds sont effectivement piégés. Entrons dans le mécanisme qui empêche cela. Il y a plusieurs pièces mobiles, alors soyez indulgents avec nous.

Chaque partie doit trouver un secret - appelons-les A et B. Ces secrets seraient terribles si Jane et Tarzan les révélaient, ils les garderont donc cachés pour l'instant. La paire va générer les hachages des secrets respectifs - h(As) et h(Bs). Ainsi, au lieu de partager leurs secrets, ils partagent ces hachages entre eux.

#### Jane et Tarzan partagent les hachages de leurs secrets entre eux.

Jane et Tarzan doivent également créer un ensemble de transactions d'engagement avant de publier leurs premières transactions à l'adresse multisignature. Cela leur donnera un recours au cas où l'autre déciderait de garder les fonds en otage.

Si vous considérez un canal comme le mini-ledger dont nous avons parlé précédemment, les transactions d'engagement sont les mises à jour que vous effectuez sur le ledger. Chaque fois que vous créez une nouvelle paire de transactions d'engagement, vous rééquilibrez les fonds entre les deux participants.

Celle d'Jane aura deux sorties - une qui paie une adresse qu'elle possède, et une autre qui est verrouillée dans une nouvelle adresse multisig. Elle le signe et le donne à Tarzan.

La transaction d'Jane avec deux sorties - une vers sa propre adresse, et une vers un nouveau multisig. Elle a encore besoin de la signature de Tarzan pour la rendre valide. Tarzan fait de même - une sortie le paie lui-même, l'autre paie une autre adresse multisig. Il le signe et le donne à Jane.

#### Nous avons deux transactions incomplètes qui sont très similaires.

Normalement, Jane pourrait ajouter une signature à la transaction de Tarzan pour la rendre valide. Mais vous remarquerez que ces fonds sont dépensés à partir du multisig 2 sur 2 que nous n'avons pas encore financé. C'est un peu comme essayer de dépenser un chèque d'un compte dont le solde est nul pour le moment. Par conséquent, ces transactions partiellement signées ne seront utilisables que lorsque le multisig sera opérationnel. 

Les nouvelles adresses multisignature (auxquelles sont destinées les sorties de 3 BTC) ont des propriétés particulières. Examinons la transaction incomplète qu'Jane a signée et donnée à Tarzan. La sortie multisig peut être dépensée dans les conditions suivantes :

- Les deux parties peuvent le signer en coopération.
- Tarzan peut le dépenser lui-même après une certaine période de temps (grâce à notre timelock).
- Jane peut le dépenser si elle connaît les B secrets de Tarzan.

Pour la transaction que Tarzan a donnée à Jane :

- Les deux parties peuvent coopérer pour le signer.
- Jane peut le dépenser seule après un certain temps.
- Tarzan peut le dépenser s'il connaît l'As secret d'Jane.

Gardez à l'esprit qu'aucune des parties ne connaît le secret de l'autre, donc 3) n'est pas encore une possibilité. Une autre chose à noter est que, si vous signez une transaction, votre contrepartie peut dépenser immédiatement car il n'y a pas de conditions spéciales sur leur sortie. Vous pouvez soit attendre que le timelock expire pour dépenser les fonds par vous-même, soit coopérer avec l'autre partie pour les dépenser immédiatement.

Bien ! Vous pouvez maintenant publier les transactions dans l'adresse multisignature originale à deux signatures. Vous pouvez enfin le faire en toute sécurité, car vous pouvez récupérer vos fonds si votre contrepartie abandonne le canal.

Une fois les transactions confirmées, le canal est opérationnel. Cette première paire de transactions nous montre l'état actuel du mini-ledger. Actuellement, il paiera 3 BTC à Tarzan, et 3 BTC à Jane. 

Lorsque Jane veut effectuer un nouveau paiement à Tarzan, la paire crée deux nouvelles transactions pour remplacer la première série. L'exercice est le même - elles ne sont que demi-signées. Cependant, Jane et Tarzan abandonnent d'abord leurs anciens secrets et échangent de nouveaux hachages pour la prochaine série de transactions.

**Si Jane voulait payer 1 BTC à Tarzan, par exemple, les deux nouvelles transactions créditeraient 2 BTC à Jane et 4 BTC à Tarzan. De cette façon, le solde est mis à jour.**

Chaque partie peut signer et diffuser l'une des transactions les plus récentes à tout moment pour la "régler" sur la blockchain. Mais la partie qui le fait devra attendre que le timelock ait expiré, tandis que l'autre peut dépenser immédiatement. Rappelez-vous, si Tarzan signe et diffuse la transaction d'Jane, elle dispose maintenant d'une sortie sans conditions.

Les deux parties peuvent convenir de fermer le canal ensemble (une fermeture coopérative). C'est probablement le moyen le plus simple et le plus rapide de remettre vos fonds sur la chaîne. Cependant, même si une partie ne répond plus ou refuse de coopérer, l'autre partie peut toujours récupérer ses fonds en attendant la fin du timelock.

### Comment le réseau Lightning empêche-t-il la tricherie ?

Vous avez peut-être identifié un vecteur d'attaque ici. Si Tarzan a actuellement un solde de 1 BTC, qu'est-ce qui l'empêche de diffuser une transaction plus ancienne où il avait plus ? Il a déjà la transaction semi-signée d'Jane, il lui suffit d'ajouter sa signature et de la diffuser, non ?

Rien ne l'empêche de le faire - sauf le fait qu'il pourrait perdre tout son solde. Supposons qu'il aille jusqu'au bout et diffuse une ancienne transaction qui paie une pièce à Jane et cinq à l'adresse multisig que nous avons mentionnée plus tôt.

Jane reçoit sa pièce immédiatement. Tarzan, quant à lui, doit attendre l'expiration du timelock pour dépenser à partir de l'adresse multisig. Vous vous souvenez de l'autre condition que nous avons mentionnée et qui permettrait à Jane de dépenser ces mêmes fonds immédiatement ? Elle a besoin d'un secret qu'elle n'avait pas à l'époque. Elle l'a maintenant - dès que la deuxième série de transactions a été créée, Tarzan a donné ce secret.

Pendant que Tarzan reste assis, incapable de faire quoi que ce soit en attendant que le timelock expire, Jane peut déplacer ces fonds. Ce mécanisme basé sur la punition signifie que les participants sont peu susceptibles de tenter de tricher, car le pair aura accès à leurs pièces.

### Acheminement des paiements

Nous avons abordé ce sujet plus tôt - les canaux peuvent être connectés. Sinon, le réseau Lightning ne serait pas aussi utile pour les paiements. Allez-vous vraiment bloquer 500 dollars dans un canal avec un café juste pour avoir votre dose quotidienne pendant les prochains mois ?

Vous n'êtes pas obligé de le faire. Si Jane ouvre un canal avec Tarzan et que Tarzan en a déjà un avec Adeline, Tarzan peut acheminer les paiements entre les deux. Cela peut fonctionner sur plusieurs "sauts", ce qui signifie qu'Jane peut effectivement payer toute personne vers laquelle un chemin existe.

**Dans ce scénario, Jane peut emprunter plusieurs chemins pour se rendre chez François. En pratique, elle prendra toujours le chemin le plus facile.**

Pour leur rôle dans l'acheminement, les intermédiaires peuvent percevoir une petite commission (bien qu'ils n'y soient pas obligés). Le Lightning Network étant encore très récent, un marché de frais n'a pas encore été mis en place. Ce que beaucoup attendent, ce sont des frais basés sur la liquidité fournie. 

Sur la chaîne de base, vos frais sont uniquement basés sur l'espace que votre transaction occupe dans un bloc - la valeur transmise n'a pas d'importance - les paiements de 1 $ et de 10 000 000 $ coûtent la même chose. En revanche, il n'y a pas d'espace de bloc dans le réseau Lightning. 

Au lieu de cela, il y a l'idée de soldes locaux et distants. Le solde local est le montant que vous pouvez "pousser" vers l'autre extrémité du canal, tandis que le solde distant est celui que votre contrepartie peut pousser vers vous.

Prenons un autre exemple. Examinons de plus près l'un des chemins ci-dessus : ```Jane <> Adeline <> François```.

Les comptes ```Jane <> Adeline``` et ```Adeline <> François``` ont chacun une capacité totale de 1 BTC. Le solde local d'Jane est de 0,7 BTC. S'ils effectuaient un règlement sur la blockchain maintenant, elle recevrait 0,7 BTC, et Adeline recevrait le solde distant (c'est-à-dire 0,3 BTC).

Si Jane veut envoyer 0,3 BTC à François, elle pousse 0,3 BTC vers le côté du canal de Adelinee. Ensuite, Adelinee pousse 0,3 BTC de son solde local dans le canal avec François. Par conséquent, le solde de Adelinee reste le même : les +0,3 BTC d'Jane et les -0,3 BTC de François s'annulent.

Adeline ne perd pas de valeur en agissant comme une connexion entre François, mais elle se rend moins flexible. Vous voyez, elle peut maintenant dépenser 0,6 BTC dans son canal avec Jane, mais seulement 0,1 BTC dans le canal avec François.

Vous pouvez imaginer une situation où Jane n'est connectée qu'à Adeline, alors que François est connecté à un réseau beaucoup plus large. Adeline pouvait auparavant envoyer un total de 0,4 BTC à d'autres personnes par l'intermédiaire de François, mais maintenant elle ne peut envoyer que 0,1 BTC parce que c'est tout ce qu'elle a sur son extrémité du canal.

Dans ce scénario, Jane mange effectivement les liquidités de Adelinee. Sans aucune sorte d'incitation, Adelinee ne voudra peut-être pas affaiblir sa propre position. Elle pourrait donc se contenter de dire qu'elle acheminera chaque 0,01 BTC moyennant des frais de dix satoshis. De cette façon, plus Adeline sacrifie ses équilibres locaux dans des chemins plus "forts", plus elle en profite.

Comme mentionné précédemment, il n'y a pas d'obligation de facto de facturer des frais. Certains pourraient ne pas être concernés par la réduction de la liquidité. D'autres pourraient se contenter d'ouvrir des canaux directement vers le récepteur.

## Limites du réseau Lightning

Ce serait fantastique si le réseau Lightning s'avérait être la solution à tous les problèmes de scalabilité du bitcoin. Malheureusement, il a ses propres défauts qui peuvent l'entraver. 

### Facilité d'utilisation

Le bitcoin n'est pas le système le plus intuitif pour les débutants : il peut être difficile de se familiariser avec les adresses, les frais, etc. Mais les portefeuilles peuvent faire abstraction des éléments compliqués pour donner aux utilisateurs quelque chose qui ressemble vaguement aux systèmes de paiement existants. Vous pouvez faire en sorte que quelqu'un télécharge un porte-monnaie pour smartphone, lui envoyer des pièces et le tour est joué.

Pour l'instant, ce n'est pas possible avec le Lightning Network. Les options sont limitées lorsqu'il s'agit d'applications pour smartphone - généralement, les nœuds Lightning nécessitent l'accès à un nœud Bitcoin pour être pleinement utilisables.

Après la configuration d'un client, les utilisateurs doivent également commencer à ouvrir des canaux avant de pouvoir effectuer des paiements. Ce processus peut prendre beaucoup de temps et peut s'avérer accablant lorsqu'un nouvel arrivant est confronté à des concepts tels que la capacité entrante/sortante.

Cela dit, des améliorations sont constamment apportées pour réduire les obstacles à l'entrée et offrir aux utilisateurs une expérience plus rationnelle.

### Liquidité

L'une des plus grandes critiques du Lightning Network est que votre capacité à effectuer des transactions est limitée. Vous ne pouvez pas dépenser plus que ce que vous avez bloqué dans un canal. Si vous dépensez tous vos fonds de sorte que le solde distant dispose de tous les fonds du canal, vous devrez fermer le canal. Vous pouvez aussi attendre que quelqu'un vous paie par son intermédiaire, mais ce n'est pas l'idéal.

Vos chemins peuvent également être limités par la capacité totale du canal. Reprenez l'exemple ```Jane <> Adeline <> François``` de tout à l'heure. Si Jane et Adeline ont une capacité de 5 BTC dans leur canal, mais que Adeline et François n'ont qu'une capacité de 1 BTC, Jane ne peut jamais envoyer plus de 1 BTC. Même dans ce cas, il faudrait que la totalité du solde se trouve du côté de Adeline sur le canal ```Adeline <> François``` pour que cela fonctionne. Cela peut limiter considérablement le montant des fonds qui peuvent être transmis sur les canaux LN, et a donc un effet d'entraînement sur la convivialité.

### Hubs centralisés

En raison du problème mentionné dans la section précédente, certains craignent que le réseau ne facilite la création de "hubs" massifs. C'est-à-dire des entités importantes, fortement connectées et disposant de beaucoup de liquidités. Tout paiement important devrait être acheminé par certaines de ces entités.

Évidemment, ce ne serait pas une bonne situation. Elle affaiblirait le système, car la mise hors ligne de ces entités perturberait considérablement les relations entre pairs. Il y a également un risque accru de censure puisqu'il n'y a que quelques points par lesquels les transactions circulent.

## L'état du réseau Lightning

En avril 2020, le Lightning Network semble en bonne santé. Il compte plus de 12 000 nœuds en ligne, plus de 30 000 canaux actifs et un peu plus de 920 milliards de dollars de capacité.

Il existe une poignée d'implémentations de nœuds différentes - c-lightning de Blockstream, Lightning Labs' Lightning Network Daemon et Eclair de l'ACINQ sont parmi les plus populaires. Pour les utilisateurs moins techniques, de nombreuses entreprises proposent des nœuds prêts à l'emploi. La seule chose que vous ayez à faire est d'allumer le dispositif et vous êtes prêt à utiliser le réseau Lightning.

## Conclusion

Depuis son lancement sur le réseau principal en 2018, le réseau Lightning a connu une croissance impressionnante, malgré le fait que beaucoup le considèrent comme étant encore en phase bêta.

Il reste encore quelques obstacles à surmonter en matière de convivialité, car il faut actuellement un certain degré de compétence technique pour exploiter un nœud Lightning. Mais compte tenu du nombre de développements en cours, les barrières à l'entrée pourraient bien être réduites au fil du temps. 

Si les problèmes peuvent être résolus, le réseau Lightning pourrait devenir une partie intégrante de l'écosystème Bitcoin, améliorant considérablement l'évolutivité et la vitesse des transactions.