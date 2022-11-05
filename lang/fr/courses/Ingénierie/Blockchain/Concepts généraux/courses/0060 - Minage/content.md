Le minage de crypto-monnaies est le processus par lequel les transactions entre utilisateurs sont vérifiées et ajoutées au grand livre public de la blockchain. Le processus de minage est également responsable de l'introduction de nouvelles pièces dans l'offre en circulation existante et constitue l'un des éléments clés qui permettent aux crypto-monnaies de fonctionner comme un réseau décentralisé de pair à pair, sans avoir besoin d'une autorité centrale tierce. 

Le bitcoin est l'exemple le plus populaire et le mieux établi de crypto-monnaie minable, mais il convient de noter que toutes les crypto-monnaies ne sont pas minables. Le minage du bitcoin est basé sur un algorithme de consensus appelé Proof of Work.

## Comment cela fonctionne-t-il ?

Un mineur est un nœud du réseau qui collecte les transactions et les organise en blocs. Chaque fois que des transactions sont effectuées, tous les nœuds du réseau les reçoivent et vérifient leur validité. Ensuite, les nœuds mineurs rassemblent ces transactions dans le pool de mémoire et commencent à les assembler en un bloc (bloc candidat). 

La première étape du minage d'un bloc consiste à hacher individuellement chaque transaction prise dans le pool de mémoire, mais avant de commencer le processus, le nœud mineur ajoute une transaction où il s'envoie la récompense du minage (récompense du bloc). Cette transaction est appelée "transaction coinbase". Il s'agit d'une transaction où des pièces sont créées "à partir de rien" et, dans la plupart des cas, c'est la première transaction à être enregistrée dans un nouveau bloc.

Après le hachage de chaque transaction, les hachages sont organisés en un arbre de Merkle (ou arbre de hachage), qui est formé en organisant les divers hachages de transaction par paires, puis en les hachant. Les sorties sont ensuite organisées en paires et hachées une nouvelle fois, et le processus est répété jusqu'à ce que le "sommet de l'arbre" soit atteint. Le sommet de l'arbre est également appelé racine de hachage (ou racine de Merkle). Il s'agit essentiellement d'un hachage unique qui représente tous les hachages précédents qui ont été utilisés pour le générer.

Le hachage racine - ainsi que le hachage du bloc précédent et un nombre aléatoire appelé nonce - est ensuite placé dans l'en-tête du bloc. L'en-tête du bloc est ensuite haché, produisant une sortie basée sur ces éléments (hachage de la racine, hachage du bloc précédent et nonce) plus quelques autres paramètres. La sortie résultante est le hachage du bloc et servira d'identifiant au bloc nouvellement généré (bloc candidat). 

Pour être considéré comme valide, le résultat (hachage de bloc) doit être inférieur à une certaine valeur cible déterminée par le protocole. En d'autres termes, le hachage de bloc doit commencer par un certain nombre de zéros.

La valeur cible - également connue sous le nom de difficulté de hachage - est régulièrement ajustée par le protocole, ce qui garantit que le taux de création de nouveaux blocs reste constant et proportionnel à la quantité de puissance de hachage consacrée au réseau.

Par conséquent, chaque fois que de nouveaux mineurs rejoignent le réseau et que la concurrence augmente, la difficulté de hachage augmente, ce qui empêche la durée moyenne des blocs de diminuer.  En revanche, si les mineurs décident de quitter le réseau, la difficulté de hachage diminuera, ce qui maintiendra le temps de bloc constant, même si la puissance de calcul consacrée au réseau est moindre.

Le processus de minage exige des mineurs qu'ils hachent l'en-tête du bloc encore et encore, en itérant par le nonce jusqu'à ce qu'un mineur du réseau produise finalement un hachage valide du bloc. Lorsqu'un hachage valide est trouvé, le nœud fondateur diffuse le bloc sur le réseau. Tous les autres nœuds vérifient si le hachage est valide et, si c'est le cas, ajoutent le bloc à leur copie de la blockchain et passent au minage du bloc suivant.

Cependant, il arrive parfois que deux mineurs diffusent un bloc valide en même temps et que le réseau se retrouve avec deux blocs concurrents. Les mineurs commencent à extraire le bloc suivant en se basant sur le bloc qu'ils ont reçu en premier. La compétition entre ces blocs se poursuivra jusqu'à ce que le bloc suivant soit extrait sur la base de l'un ou l'autre des blocs en compétition. Le bloc qui est abandonné est appelé bloc orphelin ou bloc périmé. Les mineurs de ce bloc se remettent à miner la chaîne du bloc gagnant.

## Pools miniers

Si la récompense du bloc est accordée au mineur qui découvre le premier le hachage valide, la probabilité de trouver le hachage est égale à la part de la puissance minière totale du réseau. Les mineurs disposant d'un faible pourcentage de la puissance minière ont très peu de chances de découvrir le prochain bloc par eux-mêmes. Les pools miniers sont créés pour résoudre ce problème. Il s'agit de la mise en commun des ressources par les mineurs, qui partagent leur puissance de traitement sur un réseau, afin de répartir la récompense de manière égale entre tous les membres du pool, en fonction de la quantité de travail qu'ils contribuent à la probabilité de trouver un bloc.