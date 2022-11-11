## Introduction

La détection des anomalies est une technique utilisée pour identifier les points de données dans un ensemble de données qui ne correspondent pas au reste des données. Elle a de nombreuses applications dans le monde des affaires, comme la détection des fraudes, la détection des intrusions, le contrôle de la santé des systèmes, la surveillance et la maintenance prédictive. Les anomalies, également appelées valeurs aberrantes, peuvent être divisées en trois catégories, à savoir

- **Point anomalies** − Cela se produit lorsqu'une instance de données individuelle est considérée comme anormale par rapport au reste des données.
- **Contextual anomalies** − Ce type d'anomalie est spécifique au contexte. Elle se produit si une instance de données est anormale dans un contexte spécifique.
- **Collective anomalies** − Cela se produit lorsqu'une collection d'instances de données liées est anormale par rapport à l'ensemble des données plutôt que par rapport aux valeurs individuelles.

## Methods

Deux méthodes, à savoir la détection des valeurs Outlier et la détection des Novelty , peuvent être utilisées pour la détection des anomalies. Il est nécessaire de faire la distinction entre ces deux méthodes.

### Outlier detection

Les données de formation contiennent des valeurs aberrantes qui sont éloignées du reste des données. Ces valeurs aberrantes sont définies comme des observations. C'est la raison pour laquelle les estimateurs de détection des valeurs aberrantes essaient toujours de s'adapter à la région présentant les données d'apprentissage les plus concentrées tout en ignorant les observations déviantes. Cette méthode est également connue sous le nom de détection d'anomalie non supervisée.

### Novelty detection

Il s'agit de détecter un modèle non observé dans les nouvelles observations qui ne sont pas incluses dans les données de formation. Ici, les données de formation ne sont pas polluées par les valeurs aberrantes. Elle est également connue sous le nom de détection d'anomalie semi-supervisée.

Il existe un ensemble d'outils ML, fournis par scikit-learn, qui peuvent être utilisés à la fois pour la détection des aberrations et pour la détection des nouveautés. Ces outils mettent d'abord en œuvre l'apprentissage d'objets à partir des données de manière non supervisée en utilisant la méthode fit (), comme suit .

```python
estimator.fit(X_train)
```

Maintenant, les nouvelles observations seront triées en tant que valeurs inliers (étiquetées 1) ou outliers (étiquetées -1) en utilisant la méthode predict() comme suit -

```python
estimator.fit(X_test)
```

L'estimateur calcule d'abord la fonction de notation brute, puis la méthode de prédiction utilise un seuil sur cette fonction de notation brute. Nous pouvons accéder à cette fonction de notation brute à l'aide de la méthode score_sample et nous pouvons contrôler le seuil par le paramètre de contamination.

Nous pouvons également définir la méthode decision_function qui définit les valeurs aberrantes comme des valeurs négatives et les valeurs aberrantes comme des valeurs non négatives.

```python
estimator.decision_function(X_test)
```

## Algorithmes de Sklearn pour la détection de valeurs aberrantes

Commençons par comprendre ce qu'est une enveloppe elliptique.

### Ajuster une enveloppe elliptique

Cet algorithme suppose que les données régulières proviennent d'une distribution connue, telle que la distribution gaussienne. Pour la détection des valeurs aberrantes, Scikit-learn fournit un objet nommé covariance.EllipticEnvelop.

Cet objet ajuste une estimation robuste de la covariance aux données, et donc, ajuste une ellipse aux points centraux des données. Il ignore les points situés en dehors du mode central.

#### Paramètres

Le tableau suivant présente les paramètres utilisés par sklearn. covariance.méthode EllipticEnvelop -

**Paramètre et description**

- **store_precision** − Boolean, optional, default = True - Nous pouvons le spécifier si la précision estimée est stockée.
- **assume_centered** − Boolean, optional, default = False - Si nous le mettons à Faux, il calculera l'emplacement robuste et la covariance directement avec l'aide de l'algorithme FastMCD. D'autre part, si on le met à True, il calculera le support de l'emplacement robuste et de la covariance.
- **support_fraction** − float in (0., 1.), optional, default = None - Ce paramètre indique à la méthode quelle proportion de points doit être incluse dans le support des estimations MCD brutes.
- **contamination** − float in (0., 1.), optional, default = 0.1 - Il fournit la proportion des valeurs aberrantes dans l'ensemble des données.
- **random_state** − int, RandomState instance or None, optional, default = none - Ce paramètre représente la graine du nombre pseudo-aléatoire généré qui est utilisé lors du brassage des données. Les options suivantes sont disponibles
    - **int** − Dans ce cas, random_state est la graine utilisée par le générateur de nombres aléatoires.
    - **RandomState instance** − Dans ce cas, random_state est le générateur de nombres aléatoires.
    - **None** − Dans ce cas, le générateur de nombres aléatoires est l'instance RandonState utilisée par np.random.

#### Attributes

Le tableau suivant présente les attributs utilisés par sklearn. covariance.méthode EllipticEnvelop -

**Attributs et description**

- **support_** − array-like, shape(n_samples,) - Il représente le masque des observations utilisées pour calculer des estimations robustes de l'emplacement et de la forme.
- **location_** − array-like, shape (n_features) - Il renvoie l'emplacement robuste estimé.
- **covariance_** − array-like, shape (n_features, n_features) - Il renvoie la matrice de covariance robuste estimée.
- **precision_** − array-like, shape (n_features, n_features) - Il renvoie la matrice pseudo-inverse estimée.
- **offset_** − float - Elle est utilisée pour définir la fonction de décision à partir des scores bruts. fonction_de_décision = score_samples -offset_

#### Exemple de mise en œuvre

```python
import numpy as np^M
from sklearn.covariance import EllipticEnvelope^M
true_cov = np.array([[.5, .6],[.6, .4]])
X = np.random.RandomState(0).multivariate_normal(mean = [0, 0], cov=true_cov,size=500)
cov = EllipticEnvelope(random_state = 0).fit(X)^M
# Now we can use predict method. It will return 1 for an inlier and -1 for an outlier.
cov.predict([[0, 0],[2, 2]])
```

#### Sortie

```python
array([ 1, -1])
```

## Isolation Forest

Dans le cas d'un ensemble de données à haute dimension, une façon efficace de détecter les valeurs aberrantes est d'utiliser les forêts aléatoires. Le scikit-learn fournit la méthode ensemble.IsolationForest qui isole les observations en sélectionnant aléatoirement une caractéristique. Ensuite, elle sélectionne de manière aléatoire une valeur entre les valeurs maximale et minimale des caractéristiques sélectionnées.

Ici, le nombre de fractionnements nécessaires pour isoler un échantillon est équivalent à la longueur du chemin entre le nœud racine et le nœud terminateur.

### Paramètres

Le tableau suivant présente les paramètres utilisés par la méthode ensemble.IsolationForest de sklearn.

**Paramètre et description**

- **n_estimators** − int, optional, default = 100 - Il représente le nombre d'estimateurs de base dans l'ensemble.
- **max_samples** − int or float, optional, default = “auto” - Il représente le nombre d'échantillons à tirer de X pour entraîner chaque estimateur de base. Si nous choisissons int comme valeur, il tirera max_samples échantillons. Si nous choisissons float comme valeur, il tirera des échantillons max_samples ∗ 𝑋.shape[0]. Et, si nous choisissons auto comme valeur, il dessinera max_échantillons = min(256,n_échantillons).
- **support_fraction** − float in (0., 1.), optional, default = None - Ce paramètre indique à la méthode quelle proportion de points doit être incluse dans le support des estimations MCD brutes.
- **contamination** − auto or float, optional, default = auto - Il fournit la proportion de valeurs aberrantes dans l'ensemble de données. Si nous le définissons par défaut, c'est-à-dire auto, il déterminera le seuil comme dans l'article original. S'il est défini sur float, la gamme de contamination sera dans la gamme de [0,0.5].
- **random_state** − int, RandomState instance or None, optional, default = none - Ce paramètre représente la graine du nombre pseudo-aléatoire généré qui est utilisé lors du brassage des données. Les options suivantes sont disponibles
    - **int** − Dans ce cas, random_state est la graine utilisée par le générateur de nombres aléatoires.
    - **RandomState instance** − Dans ce cas, random_state est le générateur de nombres aléatoires.
    - **None** − Dans ce cas, le générateur de nombres aléatoires est l'instance RandonState utilisée par np.random.
- **max_features** − int or float, optional (default = 1.0) - Il représente le nombre de caractéristiques à tirer de X pour entraîner chaque estimateur de base. Si nous choisissons int comme valeur, il tirera les caractéristiques max_features. Si nous choisissons float comme valeur, il tirera max_features * X.shape[𝟏] échantillons.
- **bootstrap** − Boolean, optional (default = False) - Son option par défaut est False, ce qui signifie que l'échantillonnage est effectué sans remplacement. D'autre part, si elle est définie sur True, cela signifie que les arbres individuels sont ajustés sur un sous-ensemble aléatoire des données d'apprentissage échantillonné avec remplacement.
- **n_jobs** − int or None, optional (default = None) - Il représente le nombre de tâches à exécuter en parallèle pour les méthodes fit() et predict().
- **verbose** − int, optional (default = 0) - Ce paramètre contrôle la verbosité du processus de construction de l'arbre.
- **warm_start** − Bool, optional (default=False) - Si warm_start = true, nous pouvons réutiliser la solution des appels précédents pour ajuster et nous pouvons ajouter plus d'estimateurs à l'ensemble. Mais s'il est défini à false, nous devons ajuster une toute nouvelle forêt.

### Attributes

Le tableau suivant contient les attributs utilisés par la méthode ensemble.IsolationForest de sklearn -

**Attributs et description**

- **estimators_** − list of DecisionTreeClassifier - Fournir la collection de tous les sous-estimateurs adaptés.
- **max_samples_** − integer - Il fournit le nombre réel d'échantillons utilisés.
- **offset_** − float - Elle est utilisée pour définir la fonction de décision à partir des scores bruts. fonction_de_décision = score_samples -offset_

### Exemple de mise en œuvre

Le script Python ci-dessous utilisera la méthode sklearn. ensemble.IsolationForest pour ajuster 10 arbres sur des données données données.

```python
from sklearn.ensemble import IsolationForest
import numpy as np
X = np.array([[-1, -2], [-3, -3], [-3, -4], [0, 0], [-50, 60]])
OUTDClf = IsolationForest(n_estimators = 10)
OUTDclf.fit(X)
```

### Sortie

```python
IsolationForest(
    behaviour = 'old', bootstrap = False, contamination='legacy',
    max_features = 1.0, max_samples = 'auto', n_estimators = 10, n_jobs=None,
    random_state = None, verbose = 0
)
```

## Local Outlier Factor

L'algorithme LOF (Local Outlier Factor) est un autre algorithme efficace pour effectuer la détection des aberrations sur des données de haute dimension. Le scikit-learn fournit la méthode neighbors.LocalOutlierFactor qui calcule un score, appelé facteur d'aberration locale, reflétant le degré d'anomalie des observations. La logique principale de cet algorithme est de détecter les échantillons qui ont une densité sensiblement inférieure à celle de leurs voisins. C'est pourquoi il mesure l'écart de densité locale de points de données donnés par rapport à leurs voisins.

### Paramètres

Le tableau suivant contient les paramètres utilisés par la méthode sklearn. neighbors.LocalOutlierFactor

**Paramètre et description**

- **n_neighbors** − int, optional, default = 20 - Il représente le nombre de voisins utilisés par défaut pour la requête kneighbors. Tous les échantillons seront utilisés si .
- **algorithm** − optional - 
    - Quel algorithme utiliser pour calculer les plus proches voisins.
    - Si vous choisissez ball_tree, il utilisera l'algorithme BallTree.
    - Si vous choisissez kd_tree, il utilisera l'algorithme KDTree.
    - Si vous choisissez brute, il utilisera l'algorithme de recherche par force brute.
    - Si vous choisissez auto, il décidera de l'algorithme le plus approprié sur la base de la valeur que nous avons passée à la méthode fit().
- **leaf_size** − int, optional, default = 30 - The value of this parameter can affect the speed of the construction and query. It also affects the memory required to store the tree. This parameter is passed to BallTree or KdTree algorithms.
- **contamination** − auto or float, optional, default = auto - Il fournit la proportion de valeurs aberrantes dans l'ensemble de données. Si nous le définissons par défaut, c'est-à-dire auto, il déterminera le seuil comme dans l'article original. S'il est défini sur float, la gamme de contamination sera dans la gamme de [0,0.5].
- **metric** − string or callable, default - Il représente la métrique utilisée pour le calcul de la distance.
- **P** − int, optional (default = 2) - Il s'agit du paramètre de la métrique de Minkowski. P=1 équivaut à l'utilisation de la distance manhattanienne, c'est-à-dire L1, tandis que P=2 équivaut à l'utilisation de la distance euclidienne, c'est-à-dire L2.
- **novelty** − Boolean, (default = False) - Par défaut, l'algorithme LOF est utilisé pour la détection des valeurs aberrantes mais il peut être utilisé pour la détection de la nouveauté si nous définissons nouveauté = vrai.
- **n_jobs** − int or None, optional (default = None) - Il représente le nombre de tâches à exécuter en parallèle pour les méthodes fit() et predict().

### Attributs

Le tableau suivant présente les attributs utilisés par la méthode sklearn.neighbors.LocalOutlierFactor.

**Attributs et description**

- **negative_outlier_factor_** − numpy array, shape(n_samples,) - Fournir le LOF opposé des échantillons d'entraînement.
- **n_neighbors_** − integer - Il fournit le nombre réel de voisins utilisés pour les requêtes de voisins.
- **offset_** − float - Il est utilisé pour définir les étiquettes binaires à partir des scores bruts.

### Exemple de mise en œuvre

Le script Python ci-dessous utilisera la méthode

```sklearn.neighbors.LocalOutlierFactor``` pour construire la classe NeighborsClassifier à partir d'un tableau correspondant à notre ensemble de données.

```python
from sklearn.neighbors import NearestNeighbors
samples = [[0., 0., 0.], [0., .5, 0.], [1., 1., .5]]
LOFneigh = NearestNeighbors(n_neighbors = 1, algorithm = "ball_tree",p=1)
LOFneigh.fit(samples)
```

### Sortie

```python
NearestNeighbors(
    algorithm = 'ball_tree', leaf_size = 30, metric='minkowski',
    metric_params = None, n_jobs = None, n_neighbors = 1, p = 1, radius = 1.0
)
```

### Exemple

Maintenant, nous pouvons demander à partir de ce classificateur construit si le point de fermeture se situe dans [0.5, 1., 1.5] en utilisant le script python suivant -

```python
print(neigh.kneighbors([[.5, 1., 1.5]])
```

### Sortie

```python
(array([[1.7]]), array([[1]], dtype = int64))
```

## One-Class SVM

Le SVM à une classe, introduit par Schölkopf et al, permet la détection non supervisée des aberrations. Il est également très efficace dans les données à haute dimension et estime le support d'une distribution à haute dimension. Elle est implémentée dans le module Support Vector Machines dans l'objet Sklearn.svm.OneClassSVM. Pour définir une frontière, il faut un noyau (le plus souvent utilisé est le RBF) et un paramètre scalaire.

Pour une meilleure compréhension, ajustons nos données avec l'objet svm.OneClassSVM -.

### Exemple

```python
from sklearn.svm import OneClassSVM
X = [[0], [0.89], [0.90], [0.91], [1]]
OSVMclf = OneClassSVM(gamma = 'scale').fit(X)
```

Maintenant, nous pouvons obtenir le score_samples pour les données d'entrée comme suit -

```python
OSVMclf.score_samples(X)
```

### Sortie

```python
array([1.12218594, 1.58645126, 1.58673086, 1.58645127, 1.55713767])
```