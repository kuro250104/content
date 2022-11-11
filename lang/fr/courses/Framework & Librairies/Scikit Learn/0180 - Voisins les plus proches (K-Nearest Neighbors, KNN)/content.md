## Introduction

Les méthodes d'apprentissage basées sur les voisins sont de deux types : supervisées et non supervisées. L'apprentissage supervisé basé sur les voisins peut être utilisé pour les problèmes prédictifs de classification et de régression, mais il est principalement utilisé pour les problèmes prédictifs de classification dans l'industrie.

Les méthodes d'apprentissage basées sur les voisins n'ont pas de phase de formation spécialisée et utilisent toutes les données pour la formation pendant la classification. Elles ne supposent rien non plus sur les données sous-jacentes. C'est la raison pour laquelle elles sont paresseuses et non paramétriques par nature.

Le principe de base des méthodes du plus proche voisin est -

- Trouver un nombre prédéfini d'échantillons d'entraînement proches en distance du nouveau point de données.
- Prédire l'étiquette à partir de ce nombre d'échantillons d'entraînement.

Ici, le nombre d'échantillons peut être une constante définie par l'utilisateur comme dans l'apprentissage du K-plus proche voisin ou varier en fonction de la densité locale du point comme dans l'apprentissage du voisin basé sur le rayon.

## sklearn.neighbors Module

Scikit-learn dispose du module sklearn.neighbors qui fournit des fonctionnalités pour les méthodes d'apprentissage non supervisées et supervisées basées sur les voisins. En entrée, les classes de ce module peuvent gérer soit des tableaux NumPy, soit des matrices scipy.sparse.

## Types d'algorithmes

Les différents types d'algorithmes qui peuvent être utilisés dans la mise en œuvre des méthodes basées sur les voisins sont les suivants

## Brute Force

Le calcul par force brute des distances entre toutes les paires de points dans l'ensemble de données fournit l'implémentation la plus naïve de la recherche de voisinage. Mathématiquement, pour N échantillons dans D dimensions, l'approche par force brute s'échelonne comme suit : 0[DN2]

Pour de petits échantillons de données, cet algorithme peut être très utile, mais il devient infaisable lorsque le nombre d'échantillons augmente. La recherche de voisins par force brute peut être activée en écrivant le mot clé algorithm='brute'.

## K-D Tree

L'une des structures de données arborescentes qui ont été inventées pour remédier à l'inefficacité de l'approche par la force brute est la structure de données arborescente KD. Fondamentalement, l'arbre KD est une structure arborescente binaire appelée arbre à K dimensions. Il partitionne récursivement l'espace des paramètres le long des axes de données en le divisant en régions orthographiques imbriquées dans lesquelles les points de données sont remplis.

### Avantages

Voici quelques avantages de l'algorithme de l'arbre K-D. -

- **Construction is fast** − Comme le partitionnement est effectué uniquement le long des axes de données, la construction de l'arbre K-D est très rapide.
- **Less distance computations** − Cet algorithme prend très peu de calculs de distance pour déterminer le plus proche voisin d'un point de requête. Il ne nécessite que 𝑶[𝐥𝐨𝐠 (𝑵)] calculs de distance.

### Inconvénients

- **Fast for only low-dimensional neighbor searches** − Elle est très rapide pour les recherches de voisinage à faible dimension (D < 20), mais lorsque D augmente, elle devient inefficace. En effet, le partitionnement n'est effectué que le long des axes de données,

Les recherches de voisins par arbre K-D peuvent être activées en écrivant le mot clé algorithm='kd_tree'.

## Arbre à boule

Comme nous savons que l'arbre KD est inefficace dans les dimensions supérieures, c'est pour remédier à cette inefficacité de l'arbre KD que la structure de données de l'arbre Ball a été développée. Mathématiquement, elle divise récursivement les données en nœuds définis par un centroïde C et un rayon r, de telle sorte que chaque point du nœud se trouve dans l'hyper-sphère définie par le centroïde C et le rayon r. Elle utilise l'inégalité triangulaire, donnée ci-dessous, qui réduit le nombre de points candidats pour une recherche de voisins.

```
⏐X+Y⏐≤⏐X⏐+⏐Y⏐
```

### Avantages

Voici quelques-uns des avantages de l'algorithme de l'arbre à billes.

- **Efficient on highly structured data** − Comme l'arbre à boules partitionne les données en une série d'hyper-sphères imbriquées, il est efficace sur les données hautement structurées.
- **Out-performs KD-tree** − L'arbre à boule est plus performant que l'arbre KD dans les hautes dimensions, car il présente une géométrie sphérique des nœuds de l'arbre à boule.

### Inconvénients

- **Costly** - La partition des données en une série d'hyper-sphères imbriquées rend sa construction très coûteuse.

La recherche de voisins par arbre à billes peut être activée en écrivant le mot clé algorithm='ball_tree'.

## Choisir l'algorithme du plus proche voisi

Le choix d'un algorithme optimal pour un ensemble de données donné dépend des facteurs suivants : - le choix de l'algorithme.

## Nombre d'échantillons (N) et Dimensionnalité (D)

Ce sont les facteurs les plus importants à prendre en compte lors du choix de l'algorithme du plus proche voisin. C'est pour les raisons indiquées ci-dessous -

- Le temps d'interrogation de l'algorithme de la force brute croît comme O[DN].
- Le temps d'interrogation de l'algorithme de l'arbre de Boule croît comme O[D log(N)].
- Le temps d'interrogation de l'algorithme de l'arbre KD change avec D d'une manière étrange qui est très difficile à caractériser. Lorsque D < 20, le coût est O[D log(N)] et cet algorithme est très efficace. Par contre, il est inefficace dans le cas où D > 20 car le coût augmente à presque O[DN].

## Structure des données

Un autre facteur qui affecte les performances de ces algorithmes est la dimensionnalité intrinsèque des données ou la rareté des données. En effet, les temps d'interrogation des algorithmes Ball tree et KD tree peuvent être fortement influencés par ce facteur. En revanche, le temps d'interrogation de l'algorithme Brute Force est inchangé par la structure des données. En général, les algorithmes Ball tree et KD tree produisent des temps d'interrogation plus rapides lorsqu'ils sont implantés sur des données plus éparses avec une dimensionnalité intrinsèque plus petite.

## Nombre de voisins (k)

Le nombre de voisins (k) demandés pour un point d'interrogation affecte le temps d'interrogation des algorithmes de l'arbre de Ball et de l'arbre KD. Leur temps d'interrogation devient plus lent lorsque le nombre de voisins (k) augmente. Alors que le temps de requête de Brute Force ne sera pas affecté par la valeur de k.

## Nombre de points d'interrogation

Parce qu'ils nécessitent une phase de construction, les algorithmes de l'arbre de KD et de l'arbre de boule seront efficaces s'il y a un grand nombre de points d'interrogation. En revanche, si le nombre de points d'interrogation est moindre, l'algorithme de la force brute est plus performant que les algorithmes de l'arbre de KD et de l'arbre de boule.