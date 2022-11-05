Un audit de sécurité des contrats intelligents fournit une analyse détaillée des contrats intelligents d'un projet. Ils sont importants pour sauvegarder les fonds investis par leur intermédiaire. Comme toutes les transactions sur la blockchain sont définitives, les fonds ne peuvent être récupérés en cas de vol. En général, les auditeurs examinent le code des contrats intelligents, produisent un rapport et le remettent au projet pour qu'il puisse travailler. Un rapport final est ensuite publié, détaillant les erreurs en suspens et le travail déjà effectué pour résoudre les problèmes de performance ou de sécurité.

## Introduction

Les audits de sécurité des contrats intelligents sont très courants dans l'écosystème de la finance décentralisée (DeFi). Si vous avez investi dans un projet blockchain, votre décision a peut-être été en partie basée sur les résultats d'un examen du code d'un contrat intelligent.

Si la plupart des gens comprennent l'importance des audits pour la cybersécurité, peu se plongent dans les lignes de code. Jetons un coup d'œil aux méthodes, outils et résultats généralement observés dans les audits de sécurité des contrats intelligents, afin que vous puissiez prendre des décisions plus éclairées.

## Qu'est-ce qu'un audit de contrat intelligent ?

Un audit de sécurité des contrats intelligents examine et commente le code des contrats intelligents d'un projet. Généralement, ces contrats sont écrits en langage de programmation Solidity et fournis via GitHub. Les audits de sécurité sont particulièrement précieux pour les projets DeFi qui s'attendent à traiter des transactions blockchain valant des millions de dollars ou une énorme quantité d'acteurs. Les audits suivent généralement un processus en quatre étapes :

1. Les contrats intelligents sont fournis à l'équipe d'audit pour une analyse initiale.
2. L'équipe d'audit présente ses conclusions aux responsables du projet afin qu'ils puissent agir en conséquence.
3. L'équipe de projet apporte des modifications en fonction des problèmes constatés.
4. L'équipe d'audit publie son rapport final, en tenant compte des nouveaux changements ou des erreurs en suspens.

Pour de nombreux utilisateurs de crypto-monnaies, les audits de contrats intelligents sont essentiels lorsqu'on investit dans de nouveaux projets deFi. C'est devenu une norme pour les projets qui veulent être pris au sérieux. Certains fournisseurs d'audits sont également considérés comme des leaders du secteur, ce qui rend leurs audits plus précieux aux yeux des investisseurs.

## Pourquoi avons-nous besoin d'audits de contrats intelligents ?

Comme de grandes quantités de valeur sont transigées ou verrouillées dans des contrats intelligents, ceux-ci deviennent des cibles attrayantes pour les attaques malveillantes des pirates informatiques. Des erreurs de codage mineures peuvent entraîner le vol d'énormes sommes d'argent. Par exemple, le piratage de DAO sur la blockchain Ethereum a fait perdre environ 60 millions de dollars en ETH et a même conduit à un hard fork du réseau Ethereum.

Les transactions par blockchain étant irréversibles, il est essentiel de s'assurer que le code d'un projet est sécurisé. La nature hautement sécurisée de la technologie blockchain rend difficile la récupération des fonds et la résolution des problèmes après coup, il est donc préférable de prévenir les vulnérabilités à tout prix.

## Comment fonctionnent les audits de contrats intelligents ?

Le processus d'un audit de contrat intelligent est assez standard parmi les fournisseurs d'audit. Bien que l'approche de chaque auditeur puisse différer légèrement, le processus typique est le suivant :

1. Déterminer la portée de l'audit. Le contrat intelligent et les spécifications du projet sont définis par le projet (leur objectif) et l'architecture globale. Une spécification aide l'équipe d'audit à comprendre les objectifs du projet lorsqu'elle écrit et utilise le code.
2. Fournir un devis initial en fonction de la quantité de travail nécessaire.
3. Effectuer des tests. Leur nature exacte changera en fonction de l'équipe d'audit, de ses outils d'analyse et de ses méthodes. En général, des tests manuels et automatisés sont effectués.
4. Créez une première version du rapport avec les erreurs trouvées et fournissez-la à l'équipe de projet pour qu'elle donne son avis et apporte les corrections nécessaires.
5. Publier le rapport final, en tenant compte de toute action entreprise par l'équipe pour répondre aux problèmes soulevés.

## Méthodes d'audit des contrats intelligents

### Gas efficiency

Les audits de contrats intelligents ne se concentrent pas uniquement sur la sécurité de la blockchain. Ils s'intéressent également à l'efficacité et à l'optimisation. Certains contrats effectuent une série compliquée de transactions pour remplir leur fonction prévue. Les frais de gaz sur des réseaux comme Ethereum étant relativement coûteux, des contrats efficaces peuvent permettre d'économiser beaucoup sur les coûts de transaction.

L'optimisation de leurs performances est également un indicateur de la compétence du développeur. Les étapes inefficaces offrent davantage de points d'échec et doivent être évitées. Lorsque les coûts du gaz sont élevés, les contrats intelligents peuvent ne pas s'exécuter, d'autant plus lorsqu'une faible limite de gaz est utilisée.

### Vulnérabilité des contrats

La plupart des travaux d'audit consistent à vérifier les contrats à la recherche de failles de sécurité. Si certains problèmes sont faciles à déceler, de nombreux exploits impliquent des techniques et des stratégies avancées pour drainer des fonds. Par exemple, la manipulation du marché peut être utilisée avec des contrats intelligents faibles pour mener des attaques de type "flash loan". Pour trouver ces problèmes, les auditeurs commencent le processus de test de rupture et simulent des attaques malveillantes sur le contrat intelligent. Les vulnérabilités courantes comprennent :

1. **Problèmes de réentraînement**: Lorsqu'un contrat intelligent fait un appel externe à un autre contrat externe avant que tous les effets ne soient résolus. Le contrat externe peut alors appeler récursivement le contrat intelligent d'origine et interagir avec lui d'une manière qu'il ne devrait pas pouvoir, puisque le solde du contrat d'origine n'a pas encore été mis à jour.
2. **Débordements et sous-exécutions de nombres entiers**: Lorsqu'un contrat intelligent effectue une opération arithmétique, mais que le résultat dépasse la capacité de stockage (généralement 18 décimales). Cela peut entraîner le calcul de montants incorrects.
3. **Opportunités de premier plan**: Un code mal structuré peut permettre d'anticiper les achats ou les ventes sur le marché. Ce qui, à son tour, peut permettre à d'autres d'utiliser ces informations et d'en tirer profit.

### Défauts de sécurité de la plate-forme

La plupart des audits comprennent l'examen du réseau hébergeant les contrats et même l'API utilisée pour interagir avec la DApp. Un projet peut être vulnérable à une attaque DDoS ou voir l'interface utilisateur de son site Web compromise, ce qui signifie que les utilisateurs connecteront effectivement leurs portefeuilles à des applications blockchain malveillantes.

## Qu'est-ce qu'un rapport d'audit ?

Le rapport d'audit est fourni à la fin du processus d'audit. Par souci de transparence, les projets sont censés partager leurs conclusions avec la communauté. La plupart des rapports classent les problèmes en fonction de leur gravité (critique, majeure, mineure, etc.). Le rapport indique également le statut du problème, car les projets ont le temps de le résoudre avant la publication du rapport final.

Outre un résumé, un rapport standard contient des recommandations, des exemples de code redondant et une analyse complète des erreurs de codage. Un délai est accordé au projet pour agir sur les conclusions du rapport avant la publication de la version finale.

## Où puis-je obtenir un audit des contrats intelligents ?

Un certain nombre de services d'audit de contrats intelligents sont devenus célèbres pour leurs services. Deux d'entre eux sont particulièrement populaires, et pour obtenir un audit de leur part, il faudra établir un devis initial et transmettre des informations.

### CertiK

CertiK est un leader de l'industrie en matière d'audits de contrats intelligents. Des centaines de projets ont audité leurs contrats intelligents avec eux. PancakeSwap, le plus grand Automated Market Maker (AMM) de la BSC, en est un exemple.

En outre, la grande majorité des projets soutenus par Binance Labs ont audité leurs contrats avec CertiK. CertiK publie un classement des projets audités qui vous permet de comparer chacun d'entre eux, ainsi qu'un score de sécurité. Notez que, outre Ethereum, CertiK couvre également les projets BSC et Polygon.

### Diligence de ConsenSys

Dirigée par Joseph Lubin, cofondateur d'Ethereum, ConsenSys est l'un des plus grands noms du secteur des crypto-monnaies en matière de développement de blockchain. Sous le nom de ConsenSys Diligence, l'entreprise propose des audits de contrats intelligents Ethereum. Elle propose également un service automatisé qui vérifie les contrats Ethereum Virtual Machine (EVM) pour détecter les erreurs les plus courantes.

## Combien coûte un audit de contrat intelligent ?

Le coût exact d'un audit dépend du nombre de contrats intelligents à vérifier. Généralement, un audit se chiffre en milliers de dollars. Un projet particulièrement important peut facilement coûter plus de 10 000 dollars. La société d'audit qui effectue l'audit et sa réputation auront également une incidence sur le montant de votre paiement.

## Conclusion

Heureusement pour les investisseurs et les utilisateurs, les audits de contrats intelligents sont devenus une norme en or. Cependant, lorsque chaque projet en possède un, ce n'est plus un indicateur facile de la valeur. C'est pourquoi il est incroyablement important de lire l'audit vous-même. Même si vous n'avez pas de connaissances techniques, il est utile de jeter un coup d'œil aux commentaires et à la gravité des problèmes potentiels.

Lorsque vous rencontrez un audit, vous devriez au moins avoir plus de facilité à comprendre son contenu. Comme toujours, veillez à ce que toute décision d'investissement tienne compte de l'ensemble du tableau et de toutes les informations.