## Introduction

Ici, nous allons étudier les méthodes de clustering dans Sklearn qui aideront à identifier toute similarité dans les échantillons de données.

Les méthodes de regroupement, l'une des méthodes de ML non supervisées les plus utiles, sont utilisées pour trouver des modèles de similarité et de relation entre les échantillons de données. Ensuite, elles regroupent ces échantillons en groupes ayant une similarité basée sur des caractéristiques. Le clustering détermine le regroupement intrinsèque entre les données non étiquetées actuelles, d'où son importance.

La bibliothèque Scikit-learn possède sklearn.cluster pour effectuer le clustering de données non étiquetées. Sous ce module, scikit-leran dispose des méthodes de clustering suivantes -

## KMeans

Cet algorithme calcule les centroïdes et itère jusqu'à ce qu'il trouve le centroïde optimal. Il exige que le nombre de groupes soit spécifié, c'est pourquoi il suppose qu'il est déjà connu. La logique principale de cet algorithme est de regrouper les échantillons de séparation des données dans un nombre n de groupes de variances égales en minimisant le critère connu sous le nom d'inertie. Le nombre de groupes identifiés par l'algorithme est représenté par 'K'.

Scikit-learn dispose du module sklearn.cluster.KMeans pour effectuer le clustering K-Means. Lors du calcul des centres de clusters et de la valeur d'inertie, le paramètre nommé sample_weight permet au module sklearn.cluster.KMeans d'attribuer plus de poids à certains échantillons.

## Affinity Propagation

Cet algorithme est basé sur le concept de "passage de messages" entre différentes paires d'échantillons jusqu'à convergence. Il ne nécessite pas de spécifier le nombre de clusters avant d'exécuter l'algorithme. L'algorithme a une complexité temporelle de l'ordre de 𝑂(𝑁2𝑇), ce qui constitue son plus grand inconvénient.

Scikit-learn dispose du module sklearn.cluster.AffinityPropagation pour effectuer le clustering par propagation d'affinité.

## Mean Shift

Cet algorithme découvre principalement des blobs dans une densité lisse d'échantillons. Il affecte les points de données aux clusters de manière itérative en déplaçant les points vers la densité la plus élevée de points de données. Au lieu de s'appuyer sur un paramètre appelé bande passante qui dicte la taille de la région à parcourir, il définit automatiquement le nombre de clusters.

Scikit-learn dispose du module sklearn.cluster.MeanShift pour réaliser le clustering Mean Shift.

## Spectral Clustering

Avant le clustering, cet algorithme utilise essentiellement les valeurs propres, c'est-à-dire le spectre de la matrice de similarité des données, pour effectuer une réduction de la dimensionnalité en moins de dimensions. L'utilisation de cet algorithme n'est pas conseillée lorsqu'il y a un grand nombre de clusters.

Scikit-learn dispose du module sklearn.cluster.SpectralClustering pour effectuer un clustering spectral.

## Hierarchical Clustering

Cet algorithme construit des clusters imbriqués en fusionnant ou en divisant les clusters successivement. Cette hiérarchie de clusters est représentée sous forme de dendrogramme, c'est-à-dire d'arbre. Elle se divise en deux catégories -

Agglomerative hierarchical algorithms − Dans ce type d'algorithme hiérarchique, chaque point de données est traité comme un seul cluster. Il agglomère ensuite successivement les paires de clusters. Cette méthode utilise l'approche ascendante.

Divisive hierarchical algorithms − Dans cet algorithme hiérarchique, tous les points de données sont traités comme un seul grand cluster. Le processus de mise en grappes consiste à diviser, en utilisant une approche descendante, le grand groupe en plusieurs petits groupes.

Scikit-learn dispose du module sklearn.cluster.AgglomerativeClustering pour effectuer un clustering hiérarchique agglomératif.

## DBSCAN

Il s'agit de l'acronyme "Density-based spatial clustering of applications with noise". Cet algorithme est basé sur la notion intuitive de "clusters" et de "bruit", selon laquelle les clusters sont des régions denses de plus faible densité dans l'espace des données, séparées par des régions de plus faible densité de points de données.

Scikit-learn dispose du module sklearn.cluster.DBSCAN pour effectuer le clustering DBSCAN. Il existe deux paramètres importants, à savoir min_samples et eps, utilisés par cet algorithme pour définir la densité.

Une valeur plus élevée du paramètre min_samples ou une valeur plus faible du paramètre eps donnera une indication sur la densité plus élevée des points de données qui est nécessaire pour former un cluster.

## OPTICS

Il s'agit de l'acronyme anglais "Ordering points to identify the clustering structure". Cet algorithme trouve également des clusters basés sur la densité dans les données spatiales. Sa logique de fonctionnement de base est similaire à celle de DBSCAN.

Il répond à l'une des principales faiblesses de l'algorithme DBSCAN - le problème de la détection de groupes significatifs dans des données de densité variable - en ordonnant les points de la base de données de manière à ce que les points les plus proches dans l'espace deviennent des voisins dans l'ordre.

Scikit-learn dispose du module sklearn.cluster.OPTICS pour effectuer le clustering OPTICS.

## BIRCH

Il s'agit de l'acronyme anglais Balanced iterative reducing and clustering using hierarchies. Il est utilisé pour effectuer un clustering hiérarchique sur de grands ensembles de données. Il construit un arbre nommé CFT (Characteristics Feature Tree) pour les données données.

L'avantage de la CFT est que les nœuds de données appelés nœuds CF (Characteristics Feature) contiennent les informations nécessaires à la mise en grappes, ce qui évite de devoir conserver en mémoire l'ensemble des données d'entrée.

Scikit-learn dispose du module sklearn.cluster.Birch pour effectuer le clustering BIRCH.

## Comparaison des algorithmes de clustering

Le tableau suivant donne une comparaison (basée sur les paramètres, l'évolutivité et la métrique) des algorithmes de clustering dans scikit-learn.

| **Nom de l'algorithme** | **Paramètres** | **Scalabilité** | **Métrique utilisée** |
| --- | --- | --- | --- |
| K-Means | Nombre de clusters | Très grand n_échantillons | La distance entre les points. |
| Affinity Propagation | Amortissement | Ce n'est pas extensible avec n_échantillons. | Distance du graphique |
| Mean-Shift | Bande passante | Ce n'est pas extensible avec n_échantillons. | La distance entre les points. |
| Spectral Clustering | Nombre de clusters | Niveau moyen d'extensibilité avec n_échantillons. Petit niveau d'extensibilité avec n_clusters. | Distance du graphique |
| Hierarchical Clustering | Seuil de distance ou nombre de clusters | Grand n_échantillons Grand n_clusters | La distance entre les points. |
| DBSCAN | Taille du quartier | Très grands n_échantillons et n_clusters moyens. | Distance du point le plus proche |
| OPTICS | Adhésion minimale au cluster | Très grands n_échantillons et grands n_clusters. | La distance entre les points. |
| BIRCH | Seuil, facteur de branchement | Grand n_échantillons Grand n_clusters | La distance euclidienne entre les points. |

## Clustering K-Means sur l'ensemble de données Scikit-learn Digit

Dans cet exemple, nous allons appliquer le clustering K-means au jeu de données des chiffres. Cet algorithme identifiera les chiffres similaires sans utiliser les informations de l'étiquette originale. L'implémentation est faite sur Jupyter notebook.

```python
%matplotlib inline
import matplotlib.pyplot as plt
import seaborn as sns; sns.set()
import numpy as np
from sklearn.cluster import KMeans
from sklearn.datasets import load_digits
digits = load_digits()
digits.data.shape
```

### Sortie

```python
1797, 64)
```

Cette sortie montre que l'ensemble de données numériques a 1797 échantillons avec 64 caractéristiques.

### Exemple

Maintenant, effectuez le clustering K-Means comme suit -

```python
kmeans = KMeans(n_clusters = 10, random_state = 0)
clusters = kmeans.fit_predict(digits.data)
kmeans.cluster_centers_.shape
```

### Sortie

```python
(10, 64)
```

Cette sortie montre que le clustering K-means a créé 10 clusters avec 64 caractéristiques.

### Exemple

```python
fig, ax = plt.subplots(2, 5, figsize = (8, 3))
centers = kmeans.cluster_centers_.reshape(10, 8, 8)
for axi, center in zip(ax.flat, centers):
axi.set(xticks = [], yticks = [])
axi.imshow(center, interpolation = 'nearest', cmap = plt.cm.binary)
```

### Sortie

La sortie ci-dessous contient des images montrant les centres des clusters appris par K-Means Clustering.

![Image montrant les centres des clusters appris par K-Means Clustering](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0240%20-%20M%C3%A9thodes%20de%20regroupement/images/image1.jpg)

Ensuite, le script Python ci-dessous fera correspondre les étiquettes de clusters apprises (par K-Means) avec les véritables étiquettes trouvées dans ces clusters.

```python
from scipy.stats import mode
labels = np.zeros_like(clusters)
for i in range(10):
mask = (clusters == i)
labels[mask] = mode(digits.target[mask])[0]
```

Nous pouvons également vérifier la précision avec l'aide de la commande mentionnée ci-dessous.

```python
from sklearn.metrics import accuracy_score
accuracy_score(digits.target, labels)
```

Sortie

```python
0.7935447968836951
```

## Exemple de mise en œuvre complète

```python
%matplotlib inline
import matplotlib.pyplot as plt
import seaborn as sns; sns.set()
import numpy as np

from sklearn.cluster import KMeans
from sklearn.datasets import load_digits
digits = load_digits()
digits.data.shape
kmeans = KMeans(n_clusters = 10, random_state = 0)
clusters = kmeans.fit_predict(digits.data)
kmeans.cluster_centers_.shape
fig, ax = plt.subplots(2, 5, figsize = (8, 3))
centers = kmeans.cluster_centers_.reshape(10, 8, 8)
for axi, center in zip(ax.flat, centers):
   axi.set(xticks=[], yticks = [])
   axi.imshow(center, interpolation = 'nearest', cmap = plt.cm.binary)
from scipy.stats import mode
labels = np.zeros_like(clusters)
for i in range(10):
   mask = (clusters == i)
   labels[mask] = mode(digits.target[mask])[0]
from sklearn.metrics import accuracy_score
accuracy_score(digits.target, labels)
```