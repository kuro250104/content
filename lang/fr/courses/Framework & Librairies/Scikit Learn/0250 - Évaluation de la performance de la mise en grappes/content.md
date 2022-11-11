## Introduction

Il existe plusieurs fonctions à l'aide desquelles nous pouvons évaluer la performance des algorithmes de clustering.

Voici quelques-unes des fonctions les plus importantes et les plus utilisées fournies par Scikit-learn pour évaluer la performance du clustering.

## Indice Rand ajusté

Rand Index est une fonction qui calcule une mesure de similarité entre deux clusters. Pour ce calcul, l'indice de Rand considère toutes les paires d'échantillons et compte les paires qui sont assignées dans les clusters similaires ou différents dans le clustering prédit et le clustering réel. Ensuite, le score brut de l'indice Rand est "ajusté pour le hasard" dans le score de l'indice Rand ajusté en utilisant la formule suivante -

![Formule de calcul de score de l'indice Rand ajusté](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0250%20-%20%C3%89valuation%20de%20la%20performance%20de%20la%20mise%20en%20grappes/images/image1.png)

Il a deux paramètres : labels_true, qui sont les étiquettes de classe de la vérité du sol, et labels_pred, qui sont les étiquettes des clusters à évaluer.

### Exemple

```python
from sklearn.metrics.cluster import adjusted_rand_score

    labels_true = [0, 0, 1, 1, 1, 1]
    labels_pred = [0, 0, 2, 2, 3, 3]

adjusted_rand_score(labels_true, labels_pred)
```

### Sortie

```python
0.4444444444444445
```

Un étiquetage parfait est noté 1 et un mauvais étiquetage ou un étiquetage indépendant est noté 0 ou négatif.

## Mutual Information Based Score

L'information mutuelle est une fonction qui calcule la concordance des deux affectations. Elle ignore les permutations. Les versions suivantes sont disponibles -

### Information mutuelle normalisée (NMI)

Scikit learn dispose du module sklearn.metrics.normalized_mutual_info_score.

#### Exemple

```python
from sklearn.metrics.cluster import normalized_mutual_info_score

    labels_true = [0, 0, 1, 1, 1, 1]
    labels_pred = [0, 0, 2, 2, 3, 3]

normalized_mutual_info_score (labels_true, labels_pred)
```

#### Sortie

```python
0.7611702597222881
```

## Adjusted Mutual Information (AMI)

Scikit learn dispose du module sklearn.metrics.adjusted_mutual_info_score.

### Exemple

```python
from sklearn.metrics.cluster import adjusted_mutual_info_score

   labels_true = [0, 0, 1, 1, 1, 1]
   labels_pred = [0, 0, 2, 2, 3, 3]

adjusted_mutual_info_score (labels_true, labels_pred)
```

### Sortie

```python
0.4444444444444448
```

## Score de Fowlkes-Mallows

La fonction de Fowlkes-Mallows mesure la similarité de deux regroupements d'un ensemble de points. Elle peut être définie comme la moyenne géométrique de la précision et du rappel par paire.D

Mathématiquement :

![Formule de calcul de score de Fowlkes-Mallows](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0250%20-%20%C3%89valuation%20de%20la%20performance%20de%20la%20mise%20en%20grappes/images/image2.png)

Ici, TP = True Positive − nombre de paires de points appartenant aux mêmes clusters dans les étiquettes vraies et prédites.

FP = False Positive − nombre de paires de points appartenant aux mêmes clusters dans les étiquettes vraies mais pas dans les étiquettes prédites.

FN = False Negative − nombre de paires de points appartenant aux mêmes clusters dans les étiquettes prédites mais pas dans les vraies étiquettes.

Scikit learn dispose du module sklearn.metrics.fowlkes_mallows_score -.

### Exemple

```python
from sklearn.metrics.cluster import fowlkes_mallows_score

    labels_true = [0, 0, 1, 1, 1, 1]
    labels_pred = [0, 0, 2, 2, 3, 3]

fowlkes_mallows__score (labels_true, labels_pred)
```

### Sortie

```python
0.6546536707079771
```

## Silhouette Coefficient

La fonction Silhouette calculera le coefficient de Silhouette moyen de tous les échantillons en utilisant la distance intra-groupe moyenne et la distance la plus proche pour chaque échantillon.

Mathématiquement : S=(b−a)/max(a,b)

Ici, a est la distance intra-groupe.

et, b est la distance moyenne entre les clusters les plus proches.

Le module sklearn.metrics.silhouette_score de Scikit learn a -

### Exemple

```python
from sklearn import metrics.silhouette_score
from sklearn.metrics import pairwise_distances
from sklearn import datasets
import numpy as np
from sklearn.cluster import KMeans
dataset = datasets.load_iris()
X = dataset.data
y = dataset.target

kmeans_model = KMeans(n_clusters = 3, random_state = 1).fit(X)
labels = kmeans_model.labels_
silhouette_score(X, labels, metric = 'euclidean')
```

### Sortie

```python
0.5528190123564091
```

## Matrice de contingence

Cette matrice indique la cardinalité de l'intersection pour chaque paire de confiance (vrai, prédit). La matrice de confusion pour les problèmes de classification est une matrice de contingence carrée.

Le module sklearn.metrics.contingency_matrix de Scikit learn.

### Exemple

```python
from sklearn.metrics.cluster import contingency_matrix
x = ["a", "a", "a", "b", "b", "b"]
y = [1, 1, 2, 0, 1, 2]
contingency_matrix(x, y)
```

### Sortie

```python
array([
    [0, 2, 1],
    [1, 1, 1]
])
```

La première ligne de la sortie ci-dessus montre que parmi les trois échantillons dont le vrai cluster est "a", aucun d'entre eux n'est dans 0, deux sont dans 1 et 1 est dans 2. D'autre part, la deuxième ligne montre que parmi les trois échantillons dont le vrai cluster est "b", 1 est dans 0, 1 est dans 1 et 1 est dans 2.