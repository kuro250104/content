## Introduction

Dans ce chapitre, nous allons apprendre les méthodes de boosting dans Sklearn, qui permettent de construire un modèle d'ensemble.

Les méthodes de boosting construisent un modèle d'ensemble de manière incrémentale. Le principe principal est de construire le modèle de manière incrémentale en entraînant séquentiellement chaque estimateur du modèle de base. Afin de construire un ensemble puissant, ces méthodes combinent essentiellement plusieurs apprenants hebdomadaires qui sont formés séquentiellement sur plusieurs itérations de données d'entraînement. Le module sklearn.ensemble comporte les deux méthodes de boosting suivantes.

## AdaBoost

Il s'agit de l'une des méthodes d'ensemble de boosting les plus réussies, dont la clé principale réside dans la façon dont elles donnent des poids aux instances de l'ensemble de données. C'est pourquoi l'algorithme doit accorder moins d'attention aux instances lors de la construction des modèles suivants.

### Classification avec AdaBoost

Pour créer un classificateur AdaBoost, le module Scikit-learn fournit sklearn.ensemble.AdaBoostClassifier. Lors de la construction de ce classificateur, le principal paramètre utilisé par ce module est base_estimator. Ici, base_estimator est la valeur de l'estimateur de base à partir duquel l'ensemble boosté est construit. Si la valeur de ce paramètre est nulle, l'estimateur de base sera DecisionTreeClassifier(max_depth=1).

#### Exemple de mise en œuvre

Dans l'exemple suivant, nous construisons un classificateur AdaBoost en utilisant sklearn.ensemble.AdaBoostClassifier, puis nous prédisons et vérifions son score.

```python
from sklearn.ensemble import AdaBoostClassifier
from sklearn.datasets import make_classification
X, y = make_classification(n_samples = 1000, n_features = 10,n_informative = 2, n_redundant = 0,random_state = 0, shuffle = False)
ADBclf = AdaBoostClassifier(n_estimators = 100, random_state = 0)
ADBclf.fit(X, y)
```

#### Sortie

```python
AdaBoostClassifier(algorithm = 'SAMME.R', base_estimator = None,
learning_rate = 1.0, n_estimators = 100, random_state = 0)
```

#### Exemple

Une fois ajusté, nous pouvons prédire pour de nouvelles valeurs comme suit -

```python
print(ADBclf.predict([[0, 2, 3, 0, 1, 1, 1, 1, 2, 2]]))
```

#### Sortie

```python
[1]
```

#### Exemple

Maintenant, nous pouvons vérifier le score comme suit -

```python
ADBclf.score(X, y)
```

#### Sortie

```python
0.995
```

#### Exemple

Nous pouvons également utiliser le jeu de données sklearn pour construire un classificateur en utilisant la méthode Extra-Tree. Par exemple, dans un exemple donné ci-dessous, nous utilisons le jeu de données Pima-Indian.

```python
from pandas import read_csv
from sklearn.model_selection import KFold
from sklearn.model_selection import cross_val_score
from sklearn.ensemble import AdaBoostClassifier
path = r"C:\pima-indians-diabetes.csv"
headernames = ['preg', 'plas', 'pres', 'skin', 'test', 'mass', 'pedi', 'age', 'class']
data = read_csv(path, names = headernames)
array = data.values
X = array[:,0:8]
Y = array[:,8]
seed = 5
kfold = KFold(n_splits = 10, random_state = seed)
num_trees = 100
max_features = 5
ADBclf = AdaBoostClassifier(n_estimators = num_trees, max_features = max_features)
results = cross_val_score(ADBclf, X, Y, cv = kfold)
print(results.mean())
```

#### Sortie

```python
0.7851435406698566
```

### Régression avec AdaBoost

Pour créer un régresseur avec la méthode Ada Boost, la bibliothèque Scikit-learn fournit sklearn.ensemble.AdaBoostRegressor. Lors de la construction du régresseur, il utilisera les mêmes paramètres que ceux utilisés par sklearn.ensemble.AdaBoostClassifier.

#### Implementation example

Dans l'exemple suivant, nous construisons un régresseur AdaBoost en utilisant sklearn.ensemble.AdaBoostregressor et nous prédisons également de nouvelles valeurs en utilisant la méthode predict().

```python
from sklearn.ensemble import AdaBoostRegressor
from sklearn.datasets import make_regression
X, y = make_regression(n_features = 10, n_informative = 2,random_state = 0, shuffle = False)
ADBregr = RandomForestRegressor(random_state = 0,n_estimators = 100)
ADBregr.fit(X, y)
```

#### Sortie

```python
AdaBoostRegressor(base_estimator = None, learning_rate = 1.0, loss = 'linear',
n_estimators = 100, random_state = 0)
```

#### Exemple

Une fois ajusté, nous pouvons prédire à partir du modèle de régression comme suit -

```python
print(ADBregr.predict([[0, 2, 3, 0, 1, 1, 1, 1, 2, 2]]))
```

#### Sortie

```python
[85.50955817]
```

## Arbre de gradient Boost

On l'appelle aussi arbres de régression boostés par le gradient (GRBT). Il s'agit essentiellement d'une généralisation du boosting à des fonctions de perte différentiables arbitraires. Il produit un modèle de prédiction sous la forme d'un ensemble de modèles de prédiction hebdomadaire. Il peut être utilisé pour les problèmes de régression et de classification. Leur principal avantage réside dans le fait qu'ils traitent naturellement les données de type mixte.

### Classification avec l'arbre de gradient Boost

Pour créer un classificateur Gradient Tree Boost, le module Scikit-learn fournit sklearn.ensemble.GradientBoostingClassifier. Lors de la construction de ce classificateur, le principal paramètre utilisé par ce module est la "perte". Ici, 'loss' est la valeur de la fonction de perte à optimiser. Si nous choisissons perte = déviance, cela fait référence à la déviance pour la classification avec des sorties probabilistes.

D'autre part, si nous choisissons la valeur exponentielle de ce paramètre, l'algorithme AdaBoost est récupéré. Le paramètre n_estimateurs contrôlera le nombre d'apprenants hebdomadaires. Un hyper-paramètre nommé learning_rate (dans la plage de (0,0, 1,0]) contrôlera le surajustement via le rétrécissement.

#### Exemple de mise en œuvre

Dans l'exemple suivant, nous construisons un classificateur Gradient Boosting en utilisant sklearn.ensemble.GradientBoostingClassifier. Nous adaptons ce classifieur avec 50 apprenants hebdomadaires.

```python
from sklearn.datasets import make_hastie_10_2
from sklearn.ensemble import GradientBoostingClassifier
X, y = make_hastie_10_2(random_state = 0)
X_train, X_test = X[:5000], X[5000:]
y_train, y_test = y[:5000], y[5000:]

GDBclf = GradientBoostingClassifier(n_estimators = 50, learning_rate = 1.0,max_depth = 1, random_state = 0).fit(X_train, y_train)
GDBclf.score(X_test, y_test)
```

#### Sortie

```python
0.8724285714285714
```

#### Exemple

Nous pouvons également utiliser le jeu de données sklearn pour construire un classificateur en utilisant le Gradient Boosting Classifier. Dans l'exemple suivant, nous utilisons le jeu de données Pima-Indian.

```python
from pandas import read_csv
from sklearn.model_selection import KFold
from sklearn.model_selection import cross_val_score
from sklearn.ensemble import GradientBoostingClassifier
path = r"C:\pima-indians-diabetes.csv"
headernames = ['preg', 'plas', 'pres', 'skin', 'test', 'mass', 'pedi', 'age', 'class']
data = read_csv(path, names = headernames)
array = data.values
X = array[:,0:8]
Y = array[:,8]
seed = 5
kfold = KFold(n_splits = 10, random_state = seed)
num_trees = 100
max_features = 5
ADBclf = GradientBoostingClassifier(n_estimators = num_trees, max_features = max_features)
results = cross_val_score(ADBclf, X, Y, cv = kfold)
print(results.mean())
```

#### Sortie

```python
0.7946582356674234
```

### Régression avec l'arbre de gradient Boost

Pour créer un régresseur avec la méthode Gradient Tree Boost, la bibliothèque Scikit-learn fournit sklearn.ensemble.GradientBoostingRegressor. Il peut spécifier la fonction de perte pour la régression via le nom du paramètre loss. La valeur par défaut de loss est 'ls'.

#### Exemple de mise en œuvre

Dans l'exemple suivant, nous construisons un régresseur Gradient Boosting en utilisant sklearn.ensemble.GradientBoostingregressor et nous trouvons également l'erreur quadratique moyenne en utilisant la méthode mean_squared_error().

```python
import numpy as np
from sklearn.metrics import mean_squared_error
from sklearn.datasets import make_friedman1
from sklearn.ensemble import GradientBoostingRegressor
X, y = make_friedman1(n_samples = 2000, random_state = 0, noise = 1.0)
X_train, X_test = X[:1000], X[1000:]
y_train, y_test = y[:1000], y[1000:]
GDBreg = GradientBoostingRegressor(n_estimators = 80, learning_rate=0.1,
max_depth = 1, random_state = 0, loss = 'ls').fit(X_train, y_train)
```

Une fois ajusté, nous pouvons trouver l'erreur quadratique moyenne comme suit -

```python
mean_squared_error(y_test, GDBreg.predict(X_test))
```

#### Sortie

```python
5.391246106657164
```