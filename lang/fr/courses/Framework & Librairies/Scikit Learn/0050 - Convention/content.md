Les objets de Scikit-learn partagent une API de base uniforme, qui se compose des trois interfaces complémentaires suivantes : - l'interface Estimator - Elle permet de construire des modèles et de les ajuster.

- **Interface de l'estimateur** - Elle sert à construire et à ajuster les modèles.
- **Interface de prédiction** - Elle permet de faire des prédictions.
- **Interface Transformer** - Elle permet de convertir les données.

Les API adoptent des conventions simples et les choix de conception ont été guidés de manière à éviter la prolifération du code cadre.

## Objectif des conventions

L'objectif des conventions est de s'assurer que l'API respecte les grands principes suivants :

- **Cohérence** - Tous les objets, qu'ils soient de base ou composites, doivent partager une interface cohérente qui se compose en outre d'un ensemble limité de méthodes.
- **Inspection** - Les paramètres des constructeurs et les valeurs des paramètres déterminés par l'algorithme d'apprentissage doivent être stockés et exposés en tant qu'attributs publics.
- **Non-prolifération des classes** - Les ensembles de données doivent être représentés sous forme de tableaux NumPy ou de matrices éparses Scipy, tandis que les noms et valeurs des hyperparamètres doivent être représentés sous forme de chaînes Python standard afin d'éviter la prolifération du code du framework.
- **Composition** - Les algorithmes, qu'ils soient exprimables sous la forme de séquences ou de combinaisons de transformations des données ou qu'ils soient naturellement considérés comme des méta-algorithmes paramétrés sur d'autres algorithmes, doivent être mis en œuvre et composés à partir de blocs de construction existants.
- **Valeurs par défaut sensibles** - Dans scikit-learn, chaque fois qu'une opération nécessite un paramètre défini par l'utilisateur, une valeur par défaut appropriée est définie. Cette valeur par défaut doit permettre d'effectuer l'opération d'une manière raisonnable, par exemple, en donnant une solution de base pour la tâche à accomplir.

## Conventions diverses

Les conventions disponibles dans Sklearn sont expliquées ci-dessous.

### Distribution de type

Il indique que l'entrée doit être convertie en float64. Dans l'exemple suivant, dans lequel le module **sklearn.random_projection** est utilisé pour réduire la dimensionnalité des données, nous allons l'expliquer.

#### Exemple

```python
import numpy as np
from sklearn import random_projection
rannge = np.random.RandomState(0)
X = range.rand(10,2000)
X = np.array(X, dtype = 'float32')
X.dtype
Transformer_data = random_projection.GaussianRandomProjection()
X_new = transformer.fit_transform(X)
X_new.dtype
```

#### Sortie

```python
dtype('float32')
dtype('float64')
```

Dans l'exemple ci-dessus, nous pouvons voir que X est un **float32** qui est converti en float64 par ```fit_transform(X)```.

### Réajustement et mise à jour des paramètres

Les hyper-paramètres d'un estimateur peuvent être mis à jour et réajustés après qu'il ait été construit via la méthode ```set_params()```. Voyons l'exemple suivant pour le comprendre.

#### Exemple

```python
import numpy as np
from sklearn.datasets import load_iris
from sklearn.svm import SVC
X, y = load_iris(return_X_y = True)
clf = SVC()
clf.set_params(kernel = 'linear').fit(X, y)
clf.predict(X[:5])
```

#### Sortie

```python
array([0, 0, 0, 0, 0])
```

Une fois que l'estimateur a été construit, le code ci-dessus va changer le noyau par défaut rbf en linéaire via ```SVC.set_params()```.

Maintenant, le code suivant changera à nouveau le noyau en **rbf** pour réajuster l'estimateur et faire une deuxième prédiction.

#### Exemple

```python
clf.set_params(kernel = 'rbf', gamma = 'scale').fit(X, y)
clf.predict(X[:5])
```

#### Sortie

```python
array([0, 0, 0, 0, 0])
```

### Code complet

Voici le programme exécutable complet.

```python
import numpy as np
from sklearn.datasets import load_iris
from sklearn.svm import SVC
X, y = load_iris(return_X_y = True)
clf = SVC()
clf.set_params(kernel = 'linear').fit(X, y)
clf.predict(X[:5])
clf.set_params(kernel = 'rbf', gamma = 'scale').fit(X, y)
clf.predict(X[:5])
```

### Ajustement multi-classes et multi-labels

Dans le cas de l'ajustement multiclasse, les tâches d'apprentissage et de prédiction dépendent du format des données cibles sur lesquelles l'ajustement est effectué. Le module utilisé est sklearn.multiclass. Regardez l'exemple ci-dessous, où un classificateur multiclasse est ajusté sur un tableau 1d.

#### Exemple

```python
from sklearn.svm import SVC
from sklearn.multiclass import OneVsRestClassifier
from sklearn.preprocessing import LabelBinarizer
X = [[1, 2], [3, 4], [4, 5], [5, 2], [1, 1]]
y = [0, 0, 1, 1, 2]
classif = OneVsRestClassifier(estimator = SVC(gamma = 'scale',random_state = 0))
classif.fit(X, y).predict(X)
```

#### Sortie

```python
array([0, 0, 1, 1, 2])
```

Dans l'exemple ci-dessus, le classifieur est ajusté sur un tableau unidimensionnel d'étiquettes multi-classes et la méthode ```predict()``` fournit donc la prédiction multi-classes correspondante. Mais d'un autre côté, il est également possible d'ajuster le classifieur sur un tableau bidimensionnel d'indicateurs d'étiquettes binaires, comme suit :

#### Exemple

```python
from sklearn.svm import SVC
from sklearn.multiclass import OneVsRestClassifier
from sklearn.preprocessing import LabelBinarizer
X = [[1, 2], [3, 4], [4, 5], [5, 2], [1, 1]]
y = LabelBinarizer().fit_transform(y)
classif.fit(X, y).predict(X)
```

#### Sortie

```python
array(
    [
        [0, 0, 0],
        [0, 0, 0],
        [0, 1, 0],
        [0, 1, 0],
        [0, 0, 0]
    ]
)
```

De même, dans le cas d'un ajustement multi-labels, une instance peut se voir attribuer plusieurs étiquettes comme suit.

#### Exemple

```python
from sklearn.preprocessing import MultiLabelBinarizer
y = [[0, 1], [0, 2], [1, 3], [0, 2, 3], [2, 4]]
y = MultiLabelBinarizer().fit_transform(y)
classif.fit(X, y).predict(X)
```

#### Sortie

```python
array(
    [
        [1, 0, 1, 0, 0],
        [1, 0, 1, 0, 0],
        [1, 0, 1, 1, 0],
        [1, 0, 1, 1, 0],
        [1, 0, 1, 0, 0]
    ]
)
```

Dans l'exemple ci-dessus, ```sklearn.MultiLabelBinarizer``` est utilisé pour binariser le tableau bidimensionnel de multiétiquettes afin de l'adapter. C'est pourquoi la fonction ```predict()``` donne un tableau 2d en sortie avec des étiquettes multiples pour chaque instance.