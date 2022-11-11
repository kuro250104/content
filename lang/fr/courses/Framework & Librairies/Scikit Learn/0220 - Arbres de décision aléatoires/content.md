## Randomized Decision Tree algorithms

Comme nous savons qu'un arbre de décision aléatoire est généralement formé en divisant les données de manière récursive, mais comme il est enclin à être surajusté, il a été transformé en forêt aléatoire en formant de nombreux arbres sur divers sous-échantillons de données. Le module sklearn.ensemble contient les deux algorithmes suivants, basés sur des arbres de décision aléatoires.

## The Random Forest algorithm

Pour chaque caractéristique considérée, il calcule la combinaison caractéristique/split localement optimale. Dans la forêt aléatoire, chaque arbre de décision de l'ensemble est construit à partir d'un échantillon tiré avec remplacement de l'ensemble d'apprentissage, puis obtient la prédiction de chacun d'eux et enfin sélectionne la meilleure solution au moyen d'un vote. Il peut être utilisé pour les tâches de classification et de régression.

## Classification avec Random Forest

Pour créer un classificateur de forêt aléatoire, le module Scikit-learn fournit sklearn.ensemble.RandomForestClassifier. Lors de la création d'un classificateur de forêt aléatoire, les principaux paramètres utilisés par ce module sont "max_features" et "n_estimators".

Ici, 'max_features' est la taille des sous-ensembles aléatoires de caractéristiques à prendre en compte lors de la division d'un nœud. Si la valeur de ce paramètre est nulle, toutes les caractéristiques seront prises en compte plutôt qu'un sous-ensemble aléatoire. D'autre part, n_estimateurs est le nombre d'arbres dans la forêt. Plus le nombre d'arbres est élevé, meilleur sera le résultat. Mais le calcul sera également plus long.

### Exemple de mise en œuvre

Dans l'exemple suivant, nous construisons un classificateur de forêt aléatoire en utilisant sklearn.ensemble.RandomForestClassifier et nous vérifions également sa précision en utilisant le module cross_val_score.

```python
from sklearn.model_selection import cross_val_score
from sklearn.datasets import make_blobs
from sklearn.ensemble import RandomForestClassifier
X, y = make_blobs(n_samples = 10000, n_features = 10, centers = 100,random_state = 0) RFclf = RandomForestClassifier(n_estimators = 10,max_depth = None,min_samples_split = 2, random_state = 0)
scores = cross_val_score(RFclf, X, y, cv = 5)
scores.mean()
```

### Sortie

```python
0.9997
```

### Exemple

Nous pouvons également utiliser le jeu de données sklearn pour construire un classificateur Random Forest. Comme dans l'exemple suivant, nous utilisons le jeu de données de l'iris. Nous allons également trouver son score de précision et sa matrice de confusion.

```python
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report, confusion_matrix, accuracy_score

path = "https://archive.ics.uci.edu/ml/machine-learning-database
s/iris/iris.data"
headernames = ['sepal-length', 'sepal-width', 'petal-length', 'petal-width', 'Class']
dataset = pd.read_csv(path, names = headernames)
X = dataset.iloc[:, :-1].values
y = dataset.iloc[:, 4].values
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.30)
RFclf = RandomForestClassifier(n_estimators = 50)
RFclf.fit(X_train, y_train)
y_pred = RFclf.predict(X_test)
result = confusion_matrix(y_test, y_pred)
print("Confusion Matrix:")
print(result)
result1 = classification_report(y_test, y_pred)
print("Classification Report:",)
print (result1)
result2 = accuracy_score(y_test,y_pred)
print("Accuracy:",result2)
```

### Sortie

```bash
Confusion Matrix:
[[14 0 0]
[ 0 18 1]
[ 0 0 12]]
Classification Report:
        precision recall f1-score support
Iris-setosa       1.00        1.00  1.00     14
Iris-versicolor   1.00        0.95  0.97     19
Iris-virginica    0.92        1.00  0.96     12

micro avg         0.98        0.98  0.98     45
macro avg         0.97        0.98  0.98     45
weighted avg      0.98        0.98  0.98     45

Accuracy: 0.9777777777777777
```

## Régression avec Random Forest

Pour créer une régression de forêt aléatoire, le module Scikit-learn fournit sklearn.ensemble.RandomForestRegressor. Lors de la construction du régresseur de forêt aléatoire, il utilisera les mêmes paramètres que ceux utilisés par sklearn.ensemble.RandomForestClassifier.

### Exemple de mise en œuvre

Dans l'exemple suivant, nous construisons un régresseur de forêt aléatoire en utilisant sklearn.ensemble.RandomForestregressor et nous prédisons également de nouvelles valeurs en utilisant la méthode predict().

```python
from sklearn.ensemble import RandomForestRegressor
from sklearn.datasets import make_regression
X, y = make_regression(n_features = 10, n_informative = 2,random_state = 0, shuffle = False)
RFregr = RandomForestRegressor(max_depth = 10,random_state = 0,n_estimators = 100)
RFregr.fit(X, y)
```

### Sortie

```python
RandomForestRegressor(
    bootstrap = True, criterion = 'mse', max_depth = 10,
    max_features = 'auto', max_leaf_nodes = None,
    min_impurity_decrease = 0.0, min_impurity_split = None,
    min_samples_leaf = 1, min_samples_split = 2,
    min_weight_fraction_leaf = 0.0, n_estimators = 100, n_jobs = None,
    oob_score = False, random_state = 0, verbose = 0, warm_start = False
)
```

Une fois ajusté, nous pouvons prédire à partir du modèle de régression comme suit -

```python
print(RFregr.predict([[0, 2, 3, 0, 1, 1, 1, 1, 2, 2]]))
```

### Sortie

```python
[98.47729198]
```

## Extra-Tree Methods

Pour chaque caractéristique considérée, il sélectionne une valeur aléatoire pour la division. L'avantage d'utiliser des méthodes d'arbres supplémentaires est que cela permet de réduire un peu plus la variance du modèle. L'inconvénient de l'utilisation de ces méthodes est qu'elle augmente légèrement le biais.

## Classification avec la méthode Extra-Tree

Pour créer un classificateur utilisant la méthode Extra-tree, le module Scikit-learn fournit sklearn.ensemble.ExtraTreesClassifier. Il utilise les mêmes paramètres que ceux utilisés par sklearn.ensemble.RandomForestClassifier. La seule différence réside dans la manière, évoquée plus haut, dont ils construisent les arbres.

### Exemple de mise en œuvre

Dans l'exemple suivant, nous construisons un classificateur de forêt aléatoire en utilisant sklearn.ensemble.ExtraTreeClassifier et nous vérifions également sa précision en utilisant le module cross_val_score.

```python
from sklearn.model_selection import cross_val_score
from sklearn.datasets import make_blobs
from sklearn.ensemble import ExtraTreesClassifier
X, y = make_blobs(n_samples = 10000, n_features = 10, centers=100,random_state = 0)
ETclf = ExtraTreesClassifier(n_estimators = 10,max_depth = None,min_samples_split = 10, random_state = 0)
scores = cross_val_score(ETclf, X, y, cv = 5)
scores.mean()
```

### Sortie

```python
1.0
```

### Exemple

Nous pouvons également utiliser le jeu de données sklearn pour construire un classificateur en utilisant la méthode Extra-Tree. Dans l'exemple suivant, nous utilisons le jeu de données Pima-Indian.

```python
from pandas import read_csv

from sklearn.model_selection import KFold
from sklearn.model_selection import cross_val_score
from sklearn.ensemble import ExtraTreesClassifier
path = r"C:\pima-indians-diabetes.csv"
headernames = ['preg', 'plas', 'pres', 'skin', 'test', 'mass', 'pedi', 'age', 'class']
data = read_csv(path, names=headernames)
array = data.values
X = array[:,0:8]
Y = array[:,8]
seed = 7
kfold = KFold(n_splits=10, random_state=seed)
num_trees = 150
max_features = 5
ETclf = ExtraTreesClassifier(n_estimators=num_trees, max_features=max_features)
results = cross_val_score(ETclf, X, Y, cv=kfold)
print(results.mean())
```

### Sortie

```python
0.7551435406698566
```

## Régression avec la méthode Extra-Tree

Pour créer une régression Extra-Tree, le module Scikit-learn fournit sklearn.ensemble.ExtraTreesRegressor. Lors de la construction du régresseur de la forêt aléatoire, il utilisera les mêmes paramètres que ceux utilisés par sklearn.ensemble.ExtraTreesClassifier.

### Exemple de mise en œuvre

Dans l'exemple suivant, nous appliquons sklearn.ensemble.ExtraTreesregressor sur les mêmes données que celles utilisées lors de la création du régresseur de la forêt aléatoire. Voyons la différence dans la sortie

```python
from sklearn.ensemble import ExtraTreesRegressor
from sklearn.datasets import make_regression
X, y = make_regression(n_features = 10, n_informative = 2,random_state = 0, shuffle = False)
ETregr = ExtraTreesRegressor(max_depth = 10,random_state = 0,n_estimators = 100)
ETregr.fit(X, y)
```

### Sortie

```python
ExtraTreesRegressor(bootstrap = False, criterion = 'mse', max_depth = 10,
    max_features = 'auto', max_leaf_nodes = None,
    min_impurity_decrease = 0.0, min_impurity_split = None,
    min_samples_leaf = 1, min_samples_split = 2,
    min_weight_fraction_leaf = 0.0, n_estimators = 100, n_jobs = None,
    oob_score = False, random_state = 0, verbose = 0, warm_start = False
)
```

### Exemple

Une fois ajusté, nous pouvons prédire à partir du modèle de régression comme suit -

```python
print(ETregr.predict([[0, 2, 3, 0, 1, 1, 1, 1, 2, 2]]))
```

### Sortie

```python
[85.50955817]
```