Anciennement connue sous le nom d'OpenCoin, Ripple est une société privée qui construit un réseau de paiement et d'échange (RippleNet) sur une base de données à grand livre distribué (XRP Ledger). L'objectif principal de Ripple est de connecter les banques, les fournisseurs de paiement et les bourses d'actifs numériques, afin de permettre des paiements mondiaux plus rapides et plus économiques. 

## Histoire

Le Ripple a été idéalisé en 2004 par Ryan Fugger, qui a développé le premier prototype du Ripple en tant que système monétaire numérique décentralisé (RipplePay). Le système a été mis en service en 2005 et était destiné à fournir des solutions de paiement sécurisées au sein d'un réseau mondial.

En 2012, Fugger a transmis le projet à Jed McCaleb et Chris Larsen, qui ont fondé ensemble la société technologique américaine OpenCoin. À partir de ce moment-là, Ripple a commencé à être construit comme un protocole axé sur les solutions de paiement pour les banques et autres institutions financières. En 2013, OpenCoin a été rebaptisé Ripple Labs, qui a ensuite été rebaptisé Ripple, en 2015.

## Le registre XRP (XRPL)

S'appuyant sur les travaux de Fugger et s'inspirant de la création de Bitcoin, Ripple a déployé le Ripple Consensus Ledger (RCL) en 2012 - ainsi que sa crypto-monnaie native XRP. Le RCL a ensuite été renommé XRP Ledger (XRPL).

Le XRPL fonctionne comme un système économique distribué qui non seulement stocke toutes les informations comptables des participants au réseau, mais fournit également des services d'échange sur plusieurs paires de devises. Ripple présente le XRPL comme un grand livre distribué open-source qui permet des transactions financières en temps réel. Ces transactions sont sécurisées et vérifiées par les participants du réseau grâce à un mécanisme de consensus. 

Contrairement au bitcoin, cependant, le grand livre XRP n'est pas basé sur un algorithme de consensus Proof of Work et, par conséquent, ne repose pas sur un processus de minage pour vérifier les transactions. Au lieu de cela, le réseau atteint un consensus en utilisant son propre algorithme de consensus personnalisé, anciennement connu sous le nom d'algorithme de consensus du protocole Ripple (RPCA).

Le XRPL est géré par un réseau de nœuds de validation indépendants qui comparent en permanence leurs enregistrements de transactions. N'importe qui est en mesure non seulement de mettre en place et de faire fonctionner un nœud de validation Ripple, mais aussi de choisir les nœuds auxquels faire confiance en tant que validateurs. Cependant, Ripple recommande à ses clients d'utiliser une liste de participants identifiés et de confiance pour valider leurs transactions. Cette liste est connue sous le nom de Unique Node List (UNL).

Les nœuds UNL échangent des données de transaction entre eux jusqu'à ce qu'ils soient tous d'accord sur l'état actuel du grand livre. En d'autres termes, les transactions qui sont approuvées par une supermajorité de nœuds UNL sont considérées comme valides et le consensus est atteint lorsque tous ces nœuds appliquent le même ensemble de transactions au grand livre.

Selon le site officiel de Ripple, Ripple est une société privée qui a fondé le développement du XRPL en tant que grand livre distribué open-source. Cela signifie que tout le monde peut contribuer au code et que le XRPL est capable de continuer même si la société cesse d'exister.

## RippleNet

Contrairement au XRPL, le RippleNet est exclusif à la société Ripple et a été construit sur le XRPL en tant que réseau de paiement et d'échange.

Le RippleNet offre actuellement une suite de trois produits conçue comme un système de solutions de paiement pour les banques et autres institutions financières. Actuellement, RippleNet compte trois produits majeurs : xRapid, xCurrent, et xVia.

## xRapid

En bref, xRapid est une solution de liquidité à la demande qui utilise le XRP comme monnaie-pont mondiale entre plusieurs monnaies fiduciaires. XRP et xRapid s'appuient tous deux sur le grand livre XRP, qui permet des temps de confirmation plus rapides et des frais beaucoup plus bas par rapport aux méthodes conventionnelles.

Prenons un exemple simple. Bob, qui vit en Australie, souhaite envoyer 100 dollars à Alice, qui vit en Inde. Bob transfère l'argent via une institution financière appelée FIN. Afin d'effectuer la transaction, FIN utilise la solution xRapid pour créer une connexion avec les bourses d'actifs dans le pays d'origine et de destination. Ainsi, l'entreprise est en mesure de convertir les 100 dollars de Bob en XRP, ce qui fournit les liquidités nécessaires au paiement final. En quelques secondes, le XRP est converti en roupies indiennes et Alice peut retirer l'argent auprès de la bourse d'actifs située en Inde.

## xCurrent

xCurrent est une solution conçue pour fournir un règlement et un suivi instantanés des paiements transfrontaliers entre les membres de RippleNet. Contrairement à xRapid, la solution xCurrent n'est pas basée sur le XRP Ledger et n'utilise pas la crypto-monnaie XRP par défaut. Le xCurrent est construit autour du protocole Interledger Protocol (ILP), qui a été conçu par Ripple comme un protocole permettant de connecter différents grands livres ou réseaux de paiement. 

Les quatre composants de base du xCurrent sont :

- **Messenger** - Le messager xCurrent permet une communication de pair à pair entre les institutions financières RippleNet connectées. Il est utilisé pour échanger des informations concernant les risques et la conformité, les frais, les taux de change, les détails des paiements et le délai prévu pour la livraison des fonds.
- **Validateur** - Le validateur est utilisé pour confirmer de manière cryptographique le succès ou l'échec d'une transaction et également pour coordonner le mouvement des fonds à travers l'Interledger. Les institutions financières peuvent utiliser leur propre validateur ou faire appel à un validateur tiers.
- **Grand livre ILP** - Le protocole Interledger est mis en œuvre dans les grands livres bancaires existants, ce qui crée le grand livre ILP. Le grand livre ILP fonctionne comme un grand livre auxiliaire et est utilisé pour suivre les crédits, les débits et les liquidités entre les parties à la transaction. Les fonds sont réglés de manière atomique, ce qui signifie qu'ils sont réglés instantanément ou pas du tout.
- **FX Ticker** - Le FX Ticker est utilisé pour définir les taux de change entre les parties contractantes. Il suit l'état actuel de chaque grand livre ILP configuré.

Bien que xCurrent soit principalement conçu pour les monnaies fiduciaires, il prend également en charge les transactions en crypto-monnaies.

## xVia

xVia est une interface standardisée basée sur une API qui permet aux banques et aux autres prestataires de services financiers d'interagir dans un cadre unique - sans avoir à dépendre de multiples intégrations de réseaux de paiement. xVia permet aux banques de créer des paiements par l'intermédiaire d'autres partenaires bancaires connectés à RippleNet et leur permet également de joindre des factures ou d'autres informations à leurs transactions.

## Conclusion

Alors que Bitcoin est connu comme la première crypto-monnaie et qu'Ethereum est reconnu pour la création d'une plateforme pour les contrats intelligents, nous pouvons considérer le réseau Ripple comme un système d'échange de devises qui se concentre sur les solutions de paiement global pour les banques et autres institutions financières.

RippleNet peut être mis en œuvre au-dessus de l'infrastructure bancaire existante afin de compléter et d'améliorer le système de paiement traditionnel. xCurrent permet d'effectuer des paiements en temps réel rentables entre les institutions financières, xRapid utilise XRP comme une monnaie sans frontière pour fournir des pools de liquidité à la demande, et xVia facilite l'intégration et la communication de tous les participants à RippleNet.