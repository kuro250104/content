Le bitcoin est parfois qualifié de monnaie programmable. En raison de sa nature numérique, il offre aux utilisateurs un grand degré de flexibilité lorsqu'il s'agit de définir les conditions dans lesquelles les fonds peuvent être dépensés. 

Lorsque nous parlons de Bitcoin, nous parlons de portefeuilles et de pièces. Mais nous pourrions également considérer les portefeuilles comme des clés, les pièces comme des chèques et la blockchain comme une succession de rangées de coffres-forts verrouillés. Chaque coffre est doté d'une mince fente, de sorte que n'importe qui peut déposer des chèques ou regarder à l'intérieur pour connaître la valeur du coffre. Cependant, seul le détenteur de la clé pourra accéder à l'intérieur.

Lorsqu'un détenteur de clé veut donner de l'argent à quelqu'un d'autre, il déverrouille son coffre. Il établit un nouveau chèque qui fait référence à l'ancien (qui est ensuite détruit) et l'enferme dans une boîte que le destinataire peut ouvrir. Pour le dépenser, le nouveau bénéficiaire répète le processus.

Dans cet article, nous allons examiner de plus près le script, le langage de programmation interprété par les nœuds du réseau Bitcoin. Le script est ce qui régit le mécanisme de verrouillage/déverrouillage mentionné pour les coffres-forts.

## Comment fonctionne Bitcoin ?

En reprenant l'analogie ci-dessus, on pourrait dire que chaque transaction comporte deux parties : une clé (pour déverrouiller votre boîte) et une serrure. Vous utilisez votre clé pour ouvrir la boîte qui contient le chèque que vous voulez envoyer, puis vous en ajoutez une nouvelle dans une nouvelle boîte avec une serrure différente. Pour dépenser à partir de la nouvelle boîte, vous avez besoin d'une autre clé.

C'est assez simple. Vous pouvez également varier un peu les types de serrures du système. Certains coffres exigent peut-être que vous fournissiez plusieurs clés, et d'autres que vous prouviez que vous connaissez un secret. Il y a un tas de conditions que les gens peuvent définir. 

Notre clé est ce que nous appelons un scriptSig. Le verrou est notre scriptPubKey. Si nous examinons ces composants plus en détail, nous verrons qu'ils sont en fait constitués de bits de données et de blocs de code. Une fois combinés, ils créent un petit programme.

Lorsque vous effectuez une transaction, vous diffusez cette combinaison sur le réseau. Chaque nœud qui la reçoit vérifie le programme, qui lui indique si la transaction est valide. Si ce n'est pas le cas, elle sera simplement rejetée, et vous ne pourrez pas dépenser les fonds bloqués.

Les chèques (pièces) que vous détenez sont appelés sorties de transaction non dépensées (UTXO). Les fonds peuvent être utilisés par quiconque peut fournir la clé qui correspond à la serrure. Plus précisément, la clé est le scriptSig et la serrure est le scriptPubKey.

Si les UTXO se trouvent dans votre portefeuille, ils seront probablement assortis d'une condition stipulant que seule la personne pouvant prouver la propriété de cette clé publique peut débloquer ces fonds. Pour les débloquer, vous fournissez un scriptSig qui inclut une signature numérique, en utilisant la clé privée qui correspond à la clé publique spécifiée dans le scriptPubKey. Tout ceci deviendra plus clair dans un instant.

## Comprendre la pile Bitcoin

Le script est ce que l'on appelle un langage basé sur la pile. Cela signifie que, lorsque nous lisons un ensemble d'instructions, nous les plaçons dans ce qui peut être considéré comme une colonne verticale. La liste A, B, C, par exemple, donne une pile avec A en bas et C en haut. Lorsque les instructions nous demandent de faire quelque chose, nous agissons sur un ou plusieurs éléments en commençant par le sommet de la pile.

Nous pouvons faire la distinction entre les données (des choses comme les signatures, les hachages et les clés publiques) et les instructions (ou opcodes). Les instructions suppriment les données et font quelque chose avec. Voici un exemple très simple de ce à quoi pourrait ressembler un script :

```xml
<xyz> <md5 hasher> <d16fb36f0911f878998c136191af705e> <check if equal>
```

```<xyz>``` et ```<d16fb36f0911f878998c136191af705e>``` sont les données, et le reste sont les opcodes. Nous lisons de gauche à droite, donc nous mettons d'abord la chaîne ```<xyz>``` sur la pile. Le suivant est l'opcode ```<md5 hasher>```. Celui-ci n'existe pas dans Bitcoin, mais disons qu'il retire l'élément supérieur de la pile (```<xyz>```) et le hachages en utilisant l'algorithme MD5. Ensuite, le résultat est ajouté à la pile. Le résultat est ici ```d16fb36f0911f878998c136191af705e```.

Quelle coïncidence ! Notre prochain élément à ajouter est ```<d16fb36f0911f878998c136191af705e>```, donc maintenant notre pile a deux éléments identiques. Enfin, ```<check if equal>``` fait sauter deux éléments du sommet et vérifie s'ils sont égaux. S'ils le sont, elle ajoute ```<1>``` à la pile. Sinon, elle ajoute ```<0>```.

Nous sommes arrivés à la fin de notre liste d'instructions. Notre script aurait pu échouer de deux façons - si l'élément restant était un zéro, ou si l'un des opérateurs le faisait échouer lorsque certaines conditions n'étaient pas remplies. Dans cet exemple, nous n'avions aucun opérateur de ce type et nous avons obtenu un élément non nul (<1>), notre script était donc valide. Ces règles sont également valables pour les transactions Bitcoin réelles.

C'était juste un programme inventé. Regardons maintenant les vrais programmes.

## Pay-to-Pubkey (P2PK)

Le système Pay-to-Pubkey (P2PK) est incroyablement simple. Il s'agit de verrouiller des fonds à une clé publique particulière. Si vous souhaitez recevoir des fonds de cette manière, vous devez fournir à l'expéditeur votre clé publique, plutôt qu'une adresse Bitcoin. 

La toute première transaction entre Satoshi Nakamoto et Hal Finney en 2009 était une transaction P2PK. Cette structure a été fortement utilisée dans les premiers jours du bitcoin, mais de nos jours, la structure P2PKH (Pay-to-Pubkey-Hash) l'a largement remplacée. 

Le script de verrouillage d'une transaction P2PK suit le format suivant : ```<public key>``` OP_CHECKSIG. C'est assez simple. Vous avez peut-être deviné que OP_CHECKSIG vérifie la présence d'une signature par rapport à la clé publique fournie. En tant que tel, notre scriptSig va être une simple ```<signature>```. Rappelez-vous, le scriptSig est la clé de la serrure.

Il n'y a pas plus simple que ça. Une signature est ajoutée à la pile, suivie d'une clé publique. OP_CHECKSIG les ouvre toutes les deux et vérifie la signature par rapport à la clé publique. Si elles correspondent, il ajoute un <1> à la pile. Sinon, il ajoute un <0>.

Pour des raisons que nous développerons dans la section suivante, P2PK n'est plus vraiment utilisé.

## Pay-to-Pubkey-Hash (P2PKH)

Les transactions de type "Pay-to-Pubkey-Hash" (P2PKH) sont désormais les plus courantes. À moins que vous ne fassiez des efforts pour télécharger un logiciel archaïque, votre porte-monnaie effectue probablement ces transactions par défaut.

La scriptPubKey dans P2PKH est la suivante :

```
OP_DUP OP_HASH160 <public key hash> OP_EQUALVERIFY OP_CHECKSIG
```

Avant de présenter le scriptSig, décomposons ce que les nouveaux opcodes vont faire :

### OP_DUP

OP_DUP extrait le premier élément et le duplique. Ensuite, il ajoute les deux éléments à la pile. Typiquement, ceci est fait pour que nous puissions effectuer une opération sur le duplicata sans affecter l'original.

### OP_HASH160

Cette commande extrait le premier élément et le hache deux fois. Le premier tour est haché avec l'algorithme SHA-256. La sortie SHA-256 est ensuite hachée avec l'algorithme RIPEMD-160. La sortie résultante est ajoutée à la pile.

### OP_EQUALVERIFY

OP_EQUALVERIFY combine deux autres opérateurs - OP_EQUAL et OP_VERIFY. OP_EQUAL éjecte deux éléments et vérifie s'ils sont identiques. S'ils le sont, il ajoute un 1 à la pile. Sinon, il ajoute un 0. OP_VERIFY extrait l'élément supérieur et vérifie s'il est vrai (c'est-à-dire non nul). S'il ne l'est pas, la transaction échoue. Combiné, OP_EQUALVERIFY fait échouer la transaction si les deux premiers éléments ne correspondent pas.

Cette fois, le scriptSig ressemble à ceci :

```
<signature> <public key>
```

Vous devez fournir une signature et la clé publique correspondante pour débloquer les sorties P2PKH.

Ce n'est pas très différent d'un script P2PK. Nous ajoutons simplement une étape supplémentaire pour vérifier que la clé publique correspond au hachage du script.

Il y a cependant quelque chose à noter. Dans un script de verrouillage P2PKH, la clé publique n'est pas visible - nous pouvons seulement voir son hachage. Si nous allons dans un explorateur de blockchain et regardons une sortie P2PKH qui n'a pas été dépensée, nous ne pouvons pas déterminer la clé publique. Elle n'est révélée que lorsque le destinataire décide de transférer les fonds.

Cela présente quelques avantages. Le premier est que le hachage de la clé publique est simplement plus facile à faire circuler qu'une clé publique complète. Satoshi l'a lancé en 2009 pour cette raison précise. Le hachage de la clé publique est ce que nous appelons aujourd'hui une adresse Bitcoin.

Le deuxième avantage est que les hachages de clés publiques pourraient fournir une couche supplémentaire de sécurité contre l'informatique quantique. Comme notre clé publique n'est pas connue avant que nous ayons dépensé les fonds, il est encore plus difficile pour les autres de calculer la clé privée. Ils devront inverser les deux tours de hachage (RIPEMD-160 et SHA-256) pour l'obtenir.

## Pay-to-Script-Hash (P2SH)

Le Pay-to-Script-Hash (P2SH) a été un développement très intéressant pour Bitcoin. Il permet à l'expéditeur de verrouiller des fonds sur le hachage d'un script - il n'a pas besoin de savoir ce que fait réellement le script. Prenez le hachage SHA-256 suivant :

```e145fe9ed5c23aa71fdb443de00c7d9b4a69f8a27a2e4fbb1fe1d0dbfb6583f1```

Il n'est pas nécessaire de connaître l'entrée du hachage pour y verrouiller des fonds. Le dépensier, en revanche, doit fournir le script utilisé pour le hachage et doit satisfaire aux conditions de ce script.

Le hachage ci-dessus a été créé à partir du script suivant :

```<multiplier par 2> <4> <vérifier si égal>```

Si vous voulez dépenser les pièces liées à cette scriptPubKey, vous ne devez pas seulement fournir ces commandes. Vous avez également besoin d'un scriptSig qui fait que le script terminé est évalué à True. Dans cet exemple, c'est un élément que vous ```<multipliez par 2>``` pour obtenir un résultat de ```<4>```. Bien sûr, cela signifie que notre scriptSig est juste ```<2>```.

Dans la vie réelle, la scriptPubKey pour une sortie P2SH est :

```OP_HASH160 <redeemScript hash> OP_EQUAL```

Pas de nouveaux opérateurs ici. Mais, nous avons ```<redeemScript hash>``` comme nouvel élément. Comme son nom l'indique, c'est un hash du script que nous devons fournir pour racheter les fonds (appelé ```redeemScript```). Le scriptSig changera en fonction du contenu du ```redeemScript```. En général, cependant, vous trouverez qu'il s'agit d'une combinaison de signatures et des clés publiques jointes, suivie par le ```redeemScript``` (obligatoire) :

```<signature> <public key> <redeemScript>```

Notre évaluation diffère un peu de l'exécution de la pile que nous avons vue jusqu'à présent. Elle se déroule en deux parties. La première vérifie simplement que vous avez fourni le bon hachage. 

Vous remarquerez que nous ne faisons rien avec les éléments qui précèdent le redemScript. Ils ne sont pas utilisés à ce stade. Nous avons atteint la fin de ce mini-programme, et l'élément supérieur n'est pas nul. Cela signifie qu'il est valide.

Mais nous n'avons pas encore terminé. Les noeuds du réseau reconnaissent cette structure comme P2SH, donc ils ont en fait les éléments du scriptSig qui attendent dans une autre pile. C'est là que la signature et la clé publique seront utilisées.

Jusqu'à présent, nous avons traité le redeemScript comme un élément. Mais maintenant, il va être interprété comme des instructions, qui peuvent être n'importe quoi. Prenons l'exemple d'un script de verrouillage P2PKH, auquel nous devons fournir la ```<signature>``` et la ```<clé publique>``` qui correspond à un ```<hachage de clé publique>``` à l'intérieur du ```<redeemScript>```.

Une fois que votre redeemScript a été étendu, nous avons une situation qui ressemble exactement à une transaction P2PKH régulière. A partir de là, il suffit de l'exécuter comme vous le feriez pour une transaction normale.

Nous avons démontré ce qu'on appelle un script P2SH(P2PKH) ici, mais il est peu probable que vous en trouviez un dans la nature. Rien ne vous empêche d'en fabriquer un, mais il ne vous apporte aucun avantage supplémentaire et finit par prendre plus de place dans un bloc (et, par conséquent, coûte plus cher).

Le P2SH est généralement utile pour des choses comme les transactions à signature multiple ou compatibles avec SegWit. Les transactions multi-signatures peuvent être très volumineuses car elles peuvent nécessiter plusieurs clés. Avant la mise en œuvre de Pay-to-Script-Hash, un expéditeur devait énumérer toutes les clés publiques possibles dans son script de verrouillage. 

Mais avec P2SH, la complexité des conditions de dépense n'a pas d'importance. Le hachage de la redémarrage est toujours d'une taille fixe. Les coûts sont donc répercutés sur le ou les utilisateurs qui veulent débloquer le script de verrouillage.

La compatibilité SegWit est un autre cas où les P2SH sont utiles (nous entrerons dans les détails de la différence de structure des transactions dans la section suivante). SegWit est un soft fork qui a entraîné une modification des formats de bloc/transaction. Comme il s'agit d'une mise à niveau facultative, tous les logiciels de portefeuille ne reconnaissent pas les changements.

Cela n'a pas d'importance si les clients enveloppent le hash du script SegWit dans P2SH. Comme pour toutes les transactions de ce type, ils n'ont pas besoin de savoir ce que sera le redemptage de déblocage. 

## Transactions SegWit (P2WPKH et P2WSH)

Pour comprendre le format de transaction dans SegWit, il suffit de savoir que nous n'avons plus seulement un scriptSig et un scriptPubKey. Maintenant, nous avons également un nouveau champ appelé le témoin. Les données que nous avions l'habitude de conserver dans le scriptSig sont déplacées vers le témoin, de sorte que le scriptSig est vide.

Si vous avez rencontré des adresses commençant par 'bc1', elles sont ce que nous appelons SegWit-natives (par opposition à SegWit-compatibles, qui commencent par un '3' puisqu'il s'agit d'adresses P2SH).

## Pay-to-Witness-Pubkey-Hash (P2WPKH)

Pay-to-Witness-Pubkey-Hash (P2WPKH) est la version SegWit de P2PKH. Notre témoin ressemble à ceci :

```<signature> <public key>```

Vous remarquerez que c'est la même chose que le scriptSig de P2PKH. Ici, le scriptSig est vide. Pendant ce temps, le scriptPubKey ressemble à ce qui suit :

```<OP_0> <public key hash>```

Cela semble un peu étrange, n'est-ce pas ? Où sont les opcodes qui nous permettent de comparer la signature, la clé publique et son hachage ?

Nous ne montrons pas d'opérateurs supplémentaires ici, parce que les nœuds qui reçoivent la transaction savent ce qu'il faut en faire en fonction de la longueur de <hachage de clé publique>. Ils calculeront la longueur et comprendront qu'elle doit être exécutée dans le même style qu'une bonne vieille transaction P2PKH.

Les nœuds non mis à jour ne savent pas comment interpréter la transaction de cette manière, mais cela n'a pas d'importance. Selon les anciennes règles, il n'y a pas de témoin, donc ils lisent un scriptSig vide et quelques données. Ils évaluent cela et le marquent comme valide - en ce qui les concerne, n'importe qui pourrait dépenser le résultat. C'est pourquoi SegWit est considéré comme un soft fork rétrocompatible.

## Pay-to-Witness-Script-Hash (P2WSH)

Pay-to-Witness-Script Hash (P2WSH) est le nouveau P2SH. Si vous êtes arrivés jusqu'ici, vous pouvez probablement comprendre à quoi cela ressemblera, mais nous allons quand même l'expliquer. Notre témoin est ce que nous mettrions normalement dans le scriptSig. Dans un P2WSH qui englobe une transaction P2PKH, par exemple, cela pourrait ressembler à quelque chose comme ceci :

```<signature 1> <public key>```

Voici notre scriptPubKey :

```<OP_0> <script hash>```

Les mêmes règles s'appliquent. Les nœuds SegWit lisent la longueur du hachage du script et déterminent qu'il s'agit d'une sortie P2WSH, qui est évaluée de la même manière que P2SH. Pendant ce temps, les anciens nœuds le voient simplement comme une sortie de n'importe qui peut dépenser.

## Résumé

| **Type de script** | **Description** |
| --- | --- |
| Pay-to-Pubkey (P2PK) | Verrouille les fonds à une clé publique particulière |
| Pay-to-Pubkey-Hash (P2PKH) | Verrouille les fonds à une clé publique particulière (c'est-à-dire une adresse). |
| Pay-to-Script-Hash (P2SH) | Verrouille les fonds sur le hachage d'un script que le destinataire peut fournir. |
| Pay-to-Witness-Pubkey-Hash (P2WPKH) | La version SegWit de P2PK |
| Pay-to-Witness-Script-Hash (P2WSH) | La version SegWit de P2SH |

Lorsque l'on s'intéresse de plus près au bitcoin, on commence à comprendre pourquoi il a tant de potentiel. Les transactions peuvent être constituées de nombreux éléments différents. En manipulant ces éléments constitutifs, les utilisateurs disposent d'une grande flexibilité lorsqu'il s'agit de définir les conditions dans lesquelles les fonds peuvent être dépensés.