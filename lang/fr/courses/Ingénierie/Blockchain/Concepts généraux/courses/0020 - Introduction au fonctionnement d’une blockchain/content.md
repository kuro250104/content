## Qu'est-ce qu'une blockchain ?

Une blockchain est un type particulier de base de données dans laquelle les données peuvent uniquement être ajoutées (et non supprimées ou modifiées). Les transactions sont périodiquement ajoutées à une blockchain à l'intérieur de ce que nous appelons des blocs (composés d'informations sur les transactions et d'autres métadonnées importantes).

Nous appelons cette structure une chaîne car les métadonnées de chaque bloc comprennent un élément d'information qui le relie au bloc précédent. Plus précisément, elles comprennent un hachage du bloc précédent, que vous pouvez considérer comme une empreinte numérique unique. 

La probabilité que deux éléments de données donnent le même résultat d'une fonction de hachage est infiniment faible. C'est pourquoi, si quelqu'un tente de modifier un ancien bloc, son hachage sera différent, ce qui signifie que le hachage du bloc suivant sera également différent, et ainsi de suite. Il est donc évident qu'un bloc a été modifié, car tous les blocs qui le suivent devraient également être modifiés.

La blockchain est téléchargée dans son intégralité par les participants au réseau. Vous vous souvenez que nous avons dit que n'importe qui peut valider des transactions et des signatures avec la cryptographie à clé publique ? Lorsqu'un nœud reçoit un bloc, il effectue un certain nombre de vérifications. Si un élément n'est pas valide, le bloc est rejeté.

Lorsqu'un nœud reçoit un bloc valide, il en fait sa propre copie et propage ensuite ce bloc aux autres nœuds. Ceux-ci font alors de même jusqu'à ce que le bloc se soit propagé dans tout le réseau. Ce processus est également exécuté pour les transactions non confirmées, c'est-à-dire les transactions qui ont été diffusées, mais qui ne sont pas encore incluses dans la blockchain.

## Comment les blocs sont-ils ajoutés à une blockchain ?

L'intégrité d'une blockchain est compromise si de fausses informations financières peuvent être enregistrées. En même temps, il n'y a pas d'administrateur ou de leader dans le système distribué qui maintient le grand livre - alors comment s'assurer que les participants agissent honnêtement ?

Satoshi a proposé un système de preuve de travail, qui permet à quiconque de suggérer un bloc à ajouter à la blockchain. Pour proposer un bloc, les utilisateurs doivent sacrifier leur puissance de calcul pour deviner un défi défini par le protocole.

La preuve de travail est le système le plus éprouvé pour obtenir un consensus entre les utilisateurs, mais ce n'est pas le seul. Des alternatives telles que Proof of Stake sont de plus en plus explorées, bien qu'elles n'aient pas encore été mises en œuvre dans leur forme réelle (bien que des mécanismes de consensus hybrides existent depuis un certain temps).

## Comment fonctionne le crypto mining ?

Le processus mentionné ci-dessus est connu sous le nom de minage. Si le mineur trouve une solution, le bloc qu'il a construit prolongera la chaîne. En conséquence, il recevra une récompense libellée dans la devise native de la blockchain.

L'énigme cryptographique que les mineurs doivent résoudre consiste à hacher des données de manière répétée afin de produire un nombre inférieur à une valeur donnée. Le hachage avec une fonction à sens unique signifie que, compte tenu de la sortie, il est pratiquement impossible de deviner l'entrée. Mais étant donné l'entrée, il est trivial de vérifier la sortie. De cette façon, tout participant peut vérifier que le mineur a produit un bloc "correct" et rejette ceux qui ne sont pas valides. Dans ce cas, le mineur ne reçoit aucune récompense et a gaspillé des ressources en essayant de forger un bloc invalide.

Il en résulte une théorie des jeux intéressante qui fait qu'il est coûteux pour un acteur de tenter de tricher, mais rentable pour lui d'agir honnêtement. Aucune entité malveillante ne dispose des ressources nécessaires pour attaquer indéfiniment un réseau solide. Par conséquent, nous attendons de ceux qui disposent de ressources qu'ils rentabilisent leur investissement en participant correctement.

## Les crypto-monnaies peuvent-elles évoluer ?

Comme vous pouvez probablement le constater, les réseaux distribués ne sont pas très efficaces. Malheureusement, les crypto-monnaies ne peuvent être sécurisées et résister à la censure que si tous les nœuds peuvent synchroniser une copie de la blockchain. Plus les exigences pour suivre le rythme sont faibles, plus il sera facile pour les gens d'adhérer. 

Vous pouvez comprendre pourquoi une blockchain qui n'ajoute qu'un petit bloc toutes les dix minutes est préférable, à cet égard, à une blockchain qui ajoute un énorme bloc toutes les cinq minutes. Cette dernière nécessiterait que les nœuds fassent tourner des ordinateurs très puissants pour rester synchronisés, et pousseraient les moins puissants à se déconnecter. Il en résulterait une plus grande centralisation, car il y aurait moins de pairs sur le réseau.

Mais avec des blocs plus petits, nous ne pouvons pas réaliser beaucoup de transactions par seconde (TPS). Cela signifie également qu'en période d'affluence, les transactions peuvent mettre un certain temps à être ajoutées à la blockchain. C'est un inconvénient si vous voulez effectuer un paiement rapide, mais c'est le prix à payer pour la décentralisation.

Nous appelons ce problème le dilemme de l'évolutivité. Un système qui évolue bien est un système qui peut facilement s'adapter à une augmentation du débit avec un minimum d'inconvénients. Les blockchains ne sont pas évolutives - comme nous l'avons expliqué, le simple fait d'augmenter le débit avec des blocs plus gros compromet l'objectif même du réseau distribué.

Pour augmenter le TPS sans nuire à la décentralisation du réseau, la mise à l'échelle hors chaîne semble être une approche viable. Celle-ci englobe un large éventail de solutions - centralisées et décentralisées - qui permettent d'effectuer des transactions sans les enregistrer sur la blockchain.

## Qui prend les décisions concernant les logiciels de crypto-monnaie ?

Les réseaux de crypto-monnaies sont opt-in. Personne ne vous oblige à utiliser un logiciel que vous ne voulez pas. Dans un bon protocole, le code sera entièrement en open-source afin que les utilisateurs puissent être sûrs de l'équité et de la sécurité du système.

En général, les crypto-monnaies permettent à quiconque de participer à leur développement. Les nouvelles fonctionnalités ou les modifications apportées au code sont examinées par une communauté de développeurs avant d'être approuvées et publiées. À partir de là, les utilisateurs peuvent examiner le code eux-mêmes et choisir de l'exécuter ou non. 

Certaines mises à jour seront rétrocompatibles, ce qui signifie que les nœuds mis à jour pourront toujours communiquer avec les anciens. D'autres ne seront pas rétrocompatibles : les anciens nœuds seront "éjectés" du réseau s'ils ne sont pas mis à jour. Consultez la rubrique Hard Forks et Soft Forks pour obtenir une explication à ce sujet.