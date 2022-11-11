## Introduction

k-NN (k-Nearest Neighbor), l'un des algorithmes d'apprentissage automatique les plus simples, est non paramétrique et paresseux par nature. Non paramétrique signifie qu'il n'y a aucune hypothèse sur la distribution sous-jacente des données, c'est-à-dire que la structure du modèle est déterminée à partir de l'ensemble des données. L'apprentissage paresseux ou basé sur les instances signifie qu'aux fins de la génération du modèle, il ne nécessite aucun point de données d'apprentissage et que l'ensemble des données d'apprentissage est utilisé dans la phase de test.

L'algorithme k-NN se compose des deux étapes suivantes :

1. Étape 1 - Dans cette étape, il calcule et stocke les k voisins les plus proches pour chaque échantillon de l'ensemble d'apprentissage.
2. Étape 2 - Dans cette étape, pour un échantillon non étiqueté, il récupère les k plus proches voisins de l'ensemble de données. Ensuite, parmi ces k plus proches voisins, il prédit la classe par vote (la classe avec la majorité des votes gagne).

Le module sklearn.neighbors, qui met en œuvre l'algorithme des k-plus proches voisins, fournit la fonctionnalité pour les méthodes d'apprentissage non supervisées et supervisées basées sur les voisins.

Les plus proches voisins non supervisés mettent en œuvre différents algorithmes (BallTree, KDTree ou Brute Force) pour trouver le ou les plus proches voisins pour chaque échantillon. Cette version non supervisée n'est en fait que l'étape 1, qui est discutée ci-dessus, et la base de nombreux algorithmes (KNN et K-means étant les plus connus) qui nécessitent la recherche de voisins. En d'autres termes, il s'agit d'un apprenant non supervisé qui met en œuvre la recherche de voisins.

D'autre part, l'apprentissage supervisé basé sur les voisins est utilisé pour la classification et la régression.

## Unsupervised KNN Learning

Comme nous l'avons vu, il existe de nombreux algorithmes, tels que KNN et K-Means, qui nécessitent des recherches sur les voisins les plus proches. C'est pourquoi Scikit-learn a décidé d'implémenter la partie recherche de voisins comme son propre "apprenant". La raison pour laquelle la recherche de voisins fait l'objet d'un apprentissage distinct est que le calcul de toutes les distances par paire pour trouver un voisin le plus proche n'est évidemment pas très efficace. Voyons le module utilisé par Sklearn pour implémenter l'apprentissage non supervisé du plus proche voisin avec un exemple.

## Scikit-learn module

sklearn.neighbors.NearestNeighbors est le module utilisé pour implémenter l'apprentissage non supervisé du plus proche voisin. Il utilise des algorithmes spécifiques de plus proche voisin nommés BallTree, KDTree ou Brute Force. En d'autres termes, il agit comme une interface uniforme pour ces trois algorithmes.

## Paramètres

Le tableau suivant présente les paramètres utilisés par le module NearestNeighbors.

**Paramètre et description**

- **n_neighbors** − int, optional - Le nombre de voisins à obtenir. La valeur par défaut est 5.
- **radius** − float, optional - Elle limite la distance des voisins aux retours. La valeur par défaut est de 1,0.
- **algorithm** − {‘auto’, ‘ball_tree’, ‘kd_tree’, ‘brute’}, optional - Ce paramètre prend l'algorithme (BallTree, KDTree ou Brute-force) que vous souhaitez utiliser pour calculer les plus proches voisins. Si vous fournissez 'auto', l'algorithme le plus approprié sera choisi en fonction des valeurs transmises à la méthode fit.
- **leaf_size** − int, optional - Il peut affecter la vitesse de construction et d'interrogation ainsi que la mémoire nécessaire pour stocker l'arbre. Elle est passée à BallTree ou KDTree. Bien que la valeur optimale dépende de la nature du problème, sa valeur par défaut est 30.
- **metric** − string or callable - C'est la métrique à utiliser pour le calcul de la distance entre les points. Nous pouvons la transmettre sous forme de chaîne ou de fonction appelable. Dans le cas d'une fonction appelable, la métrique est appelée sur chaque paire de lignes et la valeur résultante est enregistrée. C'est moins efficace que de passer le nom de la métrique sous forme de chaîne. Nous pouvons choisir une métrique issue de scikit-learn ou de scipy.spatial.distance. les valeurs valides sont les suivantes : -
- **Scikit-learn** − [‘cosine’,’manhattan’,‘Euclidean’, ‘l1’,’l2’, ‘cityblock’]
Scipy.spatial.distance −['braycurtis', 'canberra', 'chebyshev', 'dice', 'hamming', 'jaccard', 'correlation', 'kulsinski', 'mahalanobis', 'minkowski', 'rogerstanimoto', 'russellrao', 'sokalmicheme', 'sokalsneath', 'seuclidean', 'sqeuclidean', 'yule'].
La métrique par défaut est "Minkowski".
- **P** − integer, optional - C'est le paramètre de la métrique de Minkowski. La valeur par défaut est 2, ce qui équivaut à utiliser la distance euclidienne(l2).
- **metric_params** − dict, optional - Il s'agit des arguments supplémentaires du mot-clé pour la fonction métrique. La valeur par défaut est None.
- **N_jobs** − int or None, optional - Il représente le nombre de tâches parallèles à exécuter pour la recherche de voisins. La valeur par défaut est Aucun.

### Exemple de mise en œuvre

L'exemple ci-dessous trouvera les plus proches voisins entre deux ensembles de données en utilisant le module sklearn.neighbors.NearestNeighbors.

Tout d'abord, nous devons importer le module et les paquets nécessaires.

```python
from sklearn.neighbors import NearestNeighbors
import numpy as np
```

Maintenant, après avoir importé les paquets, définissez les ensembles de données entre lesquels nous voulons trouver les plus proches voisins -.

```python
Input_data = np.array([[-1, 1], [-2, 2], [-3, 3], [1, 2], [2, 3], [3, 4],[4, 5]])
```

Ensuite, appliquer l'algorithme d'apprentissage non supervisé, comme suit -

```python
nrst_neigh = NearestNeighbors(n_neighbors = 3, algorithm = 'ball_tree')
```

Ensuite, ajustez le modèle avec l'ensemble des données d'entrée.

```python
nrst_neigh.fit(Input_data)
```

Maintenant, trouvez les K-voisins de l'ensemble des données. Il retournera les indices et les distances des voisins de chaque point.

```python
distances, indices = nbrs.kneighbors(Input_data)
indices
```

### Sortie

```python
array(
    [
        [0, 1, 3],
        [1, 2, 0],
        [2, 1, 0],
        [3, 4, 0],
        [4, 5, 3],
        [5, 6, 4],
        [6, 5, 4]
    ], dtype = int64
)
```

```python
distances

array(
    [
        [0. , 1.41421356, 2.23606798],
        [0. , 1.41421356, 1.41421356],
        [0. , 1.41421356, 2.82842712],
        [0. , 1.41421356, 2.23606798],
        [0. , 1.41421356, 1.41421356],
        [0. , 1.41421356, 1.41421356],
        [0. , 1.41421356, 2.82842712]
    ]
)
```

La sortie ci-dessus montre que le plus proche voisin de chaque point est le point lui-même, c'est-à-dire à zéro. C'est parce que l'ensemble de requêtes correspond à l'ensemble de formation.

### Exemple

Nous pouvons également montrer une connexion entre des points voisins en produisant un graphe clairsemé comme suit : -.

```python
nrst_neigh.kneighbors_graph(Input_data).toarray()
```

### Sortie

```python
array(
    [
        [1., 1., 0., 1., 0., 0., 0.],
        [1., 1., 1., 0., 0., 0., 0.],
        [1., 1., 1., 0., 0., 0., 0.],
        [1., 0., 0., 1., 1., 0., 0.],
        [0., 0., 0., 1., 1., 1., 0.],
        [0., 0., 0., 0., 1., 1., 1.],
        [0., 0., 0., 0., 1., 1., 1.]
    ]
)
```

Une fois que nous avons ajusté le modèle de plus proches voisins non supervisé, les données seront stockées dans une structure de données basée sur la valeur définie pour l'argument 'algorithme'. Ensuite, nous pouvons utiliser les genoux de cet apprenant non supervisé dans un modèle qui nécessite des recherches de voisins.

## Programme complet fonctionnel/exécutable

```python
from sklearn.neighbors import NearestNeighbors
import numpy as np
Input_data = np.array([[-1, 1], [-2, 2], [-3, 3], [1, 2], [2, 3], [3, 4],[4, 5]])
nrst_neigh = NearestNeighbors(n_neighbors = 3, algorithm='ball_tree')
nrst_neigh.fit(Input_data)
distances, indices = nbrs.kneighbors(Input_data)
indices
distances
nrst_neigh.kneighbors_graph(Input_data).toarray()
```

## Apprentissage supervisé de KNN

L'apprentissage supervisé basé sur les voisins est utilisé pour les raisons suivantes -.

- Classification, pour les données avec des étiquettes discrètes
- Régression, pour les données avec des étiquettes continues.

## Classificateur du plus proche voisin

Nous pouvons comprendre la classification basée sur les voisins à l'aide des deux caractéristiques suivantes : - l'utilisation d'une méthode de classification basée sur les voisins

- Il est calculé à partir d'un vote majoritaire simple des plus proches voisins de chaque point.
- Il stocke simplement les instances des données de formation, c'est pourquoi il s'agit d'un type d'apprentissage non généralisé.

## Modules Scikit-learn

Voici les deux différents types de classificateurs de voisins les plus proches utilisés par scikit-learn.

**Classificateurs et description**

- **KNeighborsClassifier** - Le K dans le nom de ce classificateur représente les k plus proches voisins, où k est une valeur entière spécifiée par l'utilisateur. Ainsi, comme son nom l'indique, ce classificateur met en œuvre un apprentissage basé sur les k plus proches voisins. Le choix de la valeur de k dépend des données.
- **RadiusNeighborsClassifier** - Le Radius dans le nom de ce classificateur représente les plus proches voisins dans un rayon r spécifié, où r est une valeur flottante spécifiée par l'utilisateur. Ainsi, comme son nom l'indique, ce classificateur met en œuvre un apprentissage basé sur le nombre de voisins dans un rayon fixe r de chaque point d'apprentissage.

## Régresseur du plus proche voisin

Elle est utilisée dans les cas où les étiquettes de données sont continues par nature. Les étiquettes de données attribuées sont calculées sur la base de la moyenne des étiquettes de ses voisins les plus proches.

Voici les deux différents types de régresseurs du plus proche voisin utilisés par scikit-learn.

### KNeighborsRegressor

Le K du nom de ce régresseur représente les k plus proches voisins, où k est une valeur entière spécifiée par l'utilisateur. Ainsi, comme son nom l'indique, ce régresseur met en œuvre un apprentissage basé sur les k plus proches voisins. Le choix de la valeur de k dépend des données. Comprenons-le mieux à l'aide d'un exemple de mise en œuvre.

#### Exemple de mise en œuvre

Dans cet exemple, nous allons mettre en œuvre KNN sur l'ensemble de données appelé ensemble de données Iris Flower en utilisant scikit-learn KNeighborsRegressor.

Tout d'abord, importez l'ensemble de données de l'iris comme suit -

```python
from sklearn.datasets import load_iris
iris = load_iris()
```

Maintenant, nous devons diviser les données en données de formation et de test. Nous allons utiliser la fonction train_test_split de Sklearn pour diviser les données en un rapport de 70 (données d'entraînement) et 20 (données de test).

```python
X = iris.data[:, :4]
y = iris.target
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.20)
```

Ensuite, nous allons faire une mise à l'échelle des données avec l'aide du module de prétraitement de Sklearn comme suit -.

```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
scaler.fit(X_train)
X_train = scaler.transform(X_train)
X_test = scaler.transform(X_test)
```

Ensuite, importez la classe KNeighborsRegressor de Sklearn et fournissez la valeur des voisins comme suit.

#### Exemple

```python
import numpy as np
from sklearn.neighbors import KNeighborsRegressor
knnr = KNeighborsRegressor(n_neighbors = 8)
knnr.fit(X_train, y_train)
```

#### Sortie

```python
KNeighborsRegressor(
    algorithm = 'auto', leaf_size = 30, metric = 'minkowski',
    metric_params = None, n_jobs = None, n_neighbors = 8, p = 2,
    weights = 'uniform'
)
```

#### Exemple

Maintenant, nous pouvons trouver le MSE (Mean Squared Error) comme suit -

```python
print ("The MSE is:",format(np.power(y-knnr.predict(X),4).mean()))
```

#### Sortie

```python
The MSE is: 4.4333349609375
```

#### Exemple

Maintenant, utilisez-le pour prédire la valeur comme suit -

```python
X = [[0], [1], [2], [3]]
y = [0, 0, 1, 1]
from sklearn.neighbors import KNeighborsRegressor
knnr = KNeighborsRegressor(n_neighbors = 3)
knnr.fit(X, y)
print(knnr.predict([[2.5]]))
```

#### Sortie

```python
[0.66666667]
```

#### Programme complet fonctionnel/exécutable

```python
from sklearn.datasets import load_iris
iris = load_iris()
X = iris.data[:, :4]
y = iris.target
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.20)
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()

scaler.fit(X_train)
X_train = scaler.transform(X_train)
X_test = scaler.transform(X_test)

import numpy as np
from sklearn.neighbors import KNeighborsRegressor
knnr = KNeighborsRegressor(n_neighbors=8)
knnr.fit(X_train, y_train)

print ("The MSE is:",format(np.power(y-knnr.predict(X),4).mean()))

X = [[0], [1], [2], [3]]
y = [0, 0, 1, 1]
from sklearn.neighbors import KNeighborsRegressor
knnr = KNeighborsRegressor(n_neighbors=3)
knnr.fit(X, y)
print(knnr.predict([[2.5]]))
```

## RadiusNeighborsRegressor

Le Radius dans le nom de ce régresseur représente les plus proches voisins dans un rayon r spécifié, où r est une valeur à virgule flottante spécifiée par l'utilisateur. Ainsi, comme son nom l'indique, ce régresseur met en œuvre un apprentissage basé sur le nombre de voisins dans un rayon r fixé de chaque point de formation. Comprenons-le mieux à l'aide d'un exemple d'implémentation.

### Exemple de mise en œuvre

Dans cet exemple, nous allons mettre en œuvre KNN sur l'ensemble de données nommé Iris Flower data set en utilisant scikit-learn RadiusNeighborsRegressor -.

Tout d'abord, importez l'ensemble de données de l'iris comme suit -

```python
from sklearn.datasets import load_iris
iris = load_iris()
```

Maintenant, nous devons diviser les données en données de formation et de test. Nous allons utiliser la fonction train_test_split de Sklearn pour diviser les données en un rapport de 70 (données d'entraînement) et 20 (données de test).

```python
X = iris.data[:, :4]
y = iris.target
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.20)
```

Ensuite, nous allons faire une mise à l'échelle des données avec l'aide du module de prétraitement de Sklearn comme suit -.

```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
scaler.fit(X_train)
X_train = scaler.transform(X_train)
X_test = scaler.transform(X_test)
```

Ensuite, importez la classe RadiusneighborsRegressor de Sklearn et fournissez la valeur de radius comme suit : -.

```python
import numpy as np
from sklearn.neighbors import RadiusNeighborsRegressor
knnr_r = RadiusNeighborsRegressor(radius=1)
knnr_r.fit(X_train, y_train)
```

### Exemple

Maintenant, nous pouvons trouver le MSE (Mean Squared Error) comme suit -

```python
print ("The MSE is:",format(np.power(y-knnr_r.predict(X),4).mean()))
```

#### Sortie

```python
The MSE is: The MSE is: 5.666666666666667
```

#### Exemple

Maintenant, utilisez-le pour prédire la valeur comme suit -

```python
X = [[0], [1], [2], [3]]
y = [0, 0, 1, 1]
from sklearn.neighbors import RadiusNeighborsRegressor
knnr_r = RadiusNeighborsRegressor(radius=1)
knnr_r.fit(X, y)
print(knnr_r.predict([[2.5]]))
```

#### Sortie

```python
[1.]
```

### Programme complet fonctionnel/exécutable

```python
from sklearn.datasets import load_iris

iris = load_iris()

X = iris.data[:, :4]
y = iris.target
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.20)
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
scaler.fit(X_train)
X_train = scaler.transform(X_train)
X_test = scaler.transform(X_test)
import numpy as np
from sklearn.neighbors import RadiusNeighborsRegressor
knnr_r = RadiusNeighborsRegressor(radius = 1)
knnr_r.fit(X_train, y_train)
print ("The MSE is:",format(np.power(y-knnr_r.predict(X),4).mean()))
X = [[0], [1], [2], [3]]
y = [0, 0, 1, 1]
from sklearn.neighbors import RadiusNeighborsRegressor
knnr_r = RadiusNeighborsRegressor(radius = 1)
knnr_r.fit(X, y)
print(knnr_r.predict([[2.5]]))
```