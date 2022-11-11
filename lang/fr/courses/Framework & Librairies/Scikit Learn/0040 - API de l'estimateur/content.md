## Qu'est-ce que l'API Estimator ?

Il s'agit de l'une des principales API mises en œuvre par Scikit-learn. Elle fournit une interface cohérente pour un large éventail d'applications ML. C'est pourquoi tous les algorithmes d'apprentissage automatique de Scikit-Learn sont mis en œuvre via l'API Estimator. L'objet qui apprend à partir des données (ajustement des données) est un estimateur. Il peut être utilisé avec n'importe quel algorithme comme la classification, la régression, le regroupement ou même avec un transformateur, qui extrait des caractéristiques utiles des données brutes.

Pour l'ajustement des données, tous les objets estimateurs exposent une méthode d'ajustement qui prend un ensemble de données comme suit :

```python
estimator.fit(data)
```

Ensuite, tous les paramètres d'un estimateur peuvent être définis, comme suit, lorsqu'il est instancié par l'attribut correspondant.

```python
estimator = Estimator (param1=1, param2=2)
estimator.param1
```

Le résultat de l'opération ci-dessus serait 1.

Une fois que les données sont ajustées avec un estimateur, les paramètres sont estimés à partir des données disponibles. Tous les paramètres estimés seront les attributs de l'objet estimateur se terminant par un trait de soulignement, comme suit :

```python
estimator.estimated_param_
```

## Utilisation de l'API Estimator

Les principales utilisations des estimateurs sont les suivantes.

### Estimation et décodage d'un modèle

L'objet Estimator est utilisé pour l'estimation et le décodage d'un modèle. De plus, le modèle est estimé en tant que fonction déterministe des éléments suivants :

- Les paramètres qui sont fournis dans la construction de l'objet.
- Les paramètres qui sont fournis dans la construction de l'objet.
- L'état aléatoire global (numpy.random) si le paramètre random_state de l'estimateur est défini à none.
- Toute donnée passée à l'appel le plus récent à fit, fit_transform, ou fit_predict.
- Toutes les données passées dans une séquence d'appels à partial_fit.

### Mappage d'une représentation de données non rectangulaires en données rectangulaires

Cette fonction permet de convertir une représentation de données non rectangulaires en données rectangulaires. En d'autres termes, elle prend une entrée où chaque échantillon n'est pas représenté comme un objet de type tableau de longueur fixe, et produit un objet de type tableau de caractéristiques pour chaque échantillon.

### Distinction entre les échantillons centraux et les échantillons périphériques

Il modélise la distinction entre les échantillons centraux et les échantillons périphériques à l'aide des méthodes suivantes :

- fit
- fit_predict if transductive
- predict if inductive

## Principes directeurs

Lors de la conception de l'API Scikit-Learn, nous avons gardé à l'esprit les principes directeurs suivants.

### Cohérence

Ce principe stipule que tous les objets doivent partager une interface commune tirée d'un ensemble limité de méthodes. La documentation doit également être cohérente.

### Une hiérarchie d'objets limitée

Ce principe directeur dit :

- Les algorithmes doivent être représentés par des classes Python.
- Les ensembles de données doivent être représentés dans un format standard comme les tableaux NumPy, les DataFrames Pandas, les matrices éparses SciPy.
- Les noms des paramètres doivent utiliser des chaînes Python standard.

### Composition

Comme nous le savons, les algorithmes ML peuvent être exprimés comme la séquence de nombreux algorithmes fondamentaux. Scikit-learn utilise ces algorithmes fondamentaux chaque fois que nécessaire.

### Défauts raisonnables

Selon ce principe, la bibliothèque Scikit-learn définit une valeur par défaut appropriée chaque fois que les modèles ML nécessitent des paramètres spécifiés par l'utilisateur.

### Inspection

Selon ce principe directeur, chaque valeur de paramètre spécifiée est exposée en tant qu'attribut public.

## Étapes d'utilisation de l'API Estimator

Voici les étapes de l'utilisation de l'API d'estimation de Scikit-Learn. 

### Étape 1 : Choisir une classe de modèle

Dans cette première étape, nous devons choisir une classe de modèle. Cela peut être fait en important la classe Estimator appropriée de Scikit-learn.

### Étape 2 : Choisir les hyperparamètres du modèle

Dans cette étape, nous devons choisir les hyperparamètres du modèle de classe. Cela peut être fait en instanciant la classe avec les valeurs souhaitées.

### Étape 3 : organiser les données

Ensuite, nous devons organiser les données en matrice de caractéristiques (X) et vecteur cible (y).

### Étape 4 : Ajustement du modèle

Maintenant, nous devons ajuster le modèle à vos données. Cela peut être fait en appelant la méthode ```fit()``` de l'instance du modèle.

### Étape 5 : Application du modèle

Après avoir ajusté le modèle, nous pouvons l'appliquer à de nouvelles données. Pour l'apprentissage supervisé, utilisez la méthode ```predict()``` pour prédire les étiquettes des données inconnues. Pour l'apprentissage non supervisé, utilisez la méthode ```predict()``` ou ```transform()``` pour déduire les propriétés des données.

## Exemple d'apprentissage supervisé

Ici, comme exemple de ce processus, nous prenons le cas commun de l'ajustement d'une ligne aux données (x,y), c'est-à-dire la **régression linéaire simple**.

Tout d'abord, nous devons charger le jeu de données, nous utilisons le jeu de données de l'iris.

### Exemple

```python
import seaborn as sns
iris = sns.load_dataset('iris')
X_iris = iris.drop('species', axis = 1)
X_iris.shape
```

### Sortie

```python
(150, 4)
```
### Exemple

```python
y_iris = iris['species']
y_iris.shape
```

### Sortie

```python
(150,)
```

### Exemple

Maintenant, pour cet exemple de régression, nous allons utiliser l'échantillon de données suivant :

```python
%matplotlib inline
import matplotlib.pyplot as plt
import numpy as np
rng = np.random.RandomState(35)
x = 10*rng.rand(40)
y = 2*x-1+rng.randn(40)
plt.scatter(x,y);
```

### Sortie

![Représentation du code ci-dessus](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0040%20-%20API%20de%20l'estimateur/images/image1.png)

Nous avons donc les données ci-dessus pour notre exemple de régression linéaire.

Maintenant, avec ces données, nous pouvons appliquer les étapes mentionnées ci-dessus.

### Choisir une classe de modèle

Ici, pour calculer un modèle de régression linéaire simple, nous devons importer la classe de régression linéaire comme suit :

```python
from sklearn.linear_model import LinearRegression
```

### Choisir les hyperparamètres du modèle

Une fois que nous avons choisi une classe de modèle, nous devons faire certains choix importants qui sont souvent représentés comme des hyperparamètres, ou les paramètres qui doivent être définis avant que le modèle ne soit ajusté aux données. Ici, pour cet exemple de régression linéaire, nous souhaitons ajuster l'intercept en utilisant l'hyperparamètre fit_intercept comme suit.

#### Exemple

```python
model = LinearRegression(fit_intercept = True)
model
```

#### Sortie

```python
LinearRegression(copy_X = True, fit_intercept = True, n_jobs = None, normalize = False)
```

### Organisation des données

Maintenant, comme nous savons que notre variable cible y est sous une forme correcte, c'est-à-dire un tableau de longueur n_échantillons de 1-D. Nous devons cependant remodeler la matrice de caractéristiques X pour en faire une matrice de taille [n_échantillons, n_caractères]. Mais, nous devons remodeler la matrice des caractéristiques X pour en faire une matrice de taille [n_échantillons, n_caractéristiques]. Cela peut être fait comme suit.

#### Exemple

```python
X = x[:, np.newaxis]
X.shape
```

#### Sortie

```python
(40, 1)
```

### Ajustement du modèle

Une fois les données organisées, il est temps d'ajuster le modèle, c'est-à-dire d'appliquer notre modèle aux données. Ceci peut être fait avec l'aide de la méthode ```fit()``` comme suit.

#### Exemple

```python
model.fit(X, y)
```

#### Sortie

```python
LinearRegression(copy_X = True, fit_intercept = True, n_jobs = None,normalize = False)
```

Dans Scikit-learn, le processus ```fit()``` comporte des traits de soulignement à la fin.

Dans cet exemple, le paramètre ci-dessous indique la pente de l'ajustement linéaire simple des données.

#### Exemple

```python
model.coef_
```

#### Sortie

```python
array([1.99839352])
```

Le paramètre ci-dessous représente l'intercept de l'ajustement linéaire simple aux données.

#### Exemple

```python
model.intercept_
```

#### Sortie

```python
-0.9895459457775022
```

### Application du modèle à de nouvelles données

Après avoir formé le modèle, nous pouvons l'appliquer à de nouvelles données. La tâche principale de l'apprentissage automatique supervisé est d'évaluer le modèle sur la base de nouvelles données qui ne font pas partie de l'ensemble d'apprentissage. Cela peut être fait à l'aide de la méthode predict() comme suit.

#### Exemple

```python
xfit = np.linspace(-1, 11)
Xfit = xfit[:, np.newaxis]
yfit = model.predict(Xfit)
plt.scatter(x, y)
plt.plot(xfit, yfit);
```

#### Sortie

![Représentation du code ci-dessus](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0040%20-%20API%20de%20l'estimateur/images/image3.png)

### Exemple complet de travail/exécutable

```python
%matplotlib inline
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns

iris = sns.load_dataset('iris')
X_iris = iris.drop('species', axis = 1)
X_iris.shape
y_iris = iris['species']
y_iris.shape

rng = np.random.RandomState(35)
x = 10*rng.rand(40)
y = 2*x-1+rng.randn(40)
plt.scatter(x,y);
from sklearn.linear_model import LinearRegression
model = LinearRegression(fit_intercept=True)
model
X = x[:, np.newaxis]
X.shape

model.fit(X, y)
model.coef_
model.intercept_

xfit = np.linspace(-1, 11)
Xfit = xfit[:, np.newaxis]
yfit = model.predict(Xfit)
plt.scatter(x, y)
plt.plot(xfit, yfit);
```

## Exemple d'apprentissage non supervisé

Ici, nous prenons comme exemple de ce processus le cas commun de la réduction de la dimensionnalité de l'ensemble de données Iris afin de pouvoir le visualiser plus facilement. Pour cet exemple, nous allons utiliser l'analyse en composantes principales (ACP), une technique de réduction de la dimensionnalité rapide et linéaire.

Comme dans l'exemple ci-dessus, nous pouvons charger et tracer les données aléatoires de l'ensemble de données sur l'iris. Ensuite, nous pouvons suivre les étapes suivantes.

### Choisir une classe de modèle

```python
from sklearn.decomposition import PCA
```

### Choisir les hyperparamètres du modèle

#### Exemple

```python
model = PCA(n_components=2)
model
```

#### Sortie

```python
PCA(copy = True, iterated_power = 'auto', n_components = 2, random_state = None,
    svd_solver = 'auto', tol = 0.0, whiten = False)
```

### Modèle de raccord

#### Exemple

```python
model.fit(X_iris)
```

#### Sortie

```python
PCA(copy = True, iterated_power = 'auto', n_components = 2, random_state = None,
    svd_solver = 'auto', tol = 0.0, whiten = False)
```

### Transformer les données en deux dimensions

#### Exemple

```python
X_2D = model.transform(X_iris)
```

Maintenant, nous pouvons tracer le résultat comme suit.

```python
iris['PCA1'] = X_2D[:, 0]
iris['PCA2'] = X_2D[:, 1]
sns.lmplot("PCA1", "PCA2", hue = 'species', data = iris, fit_reg = False);
```

#### Sortie

![Représentation du code ci-dessus](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0040%20-%20API%20de%20l'estimateur/images/image2.png)

### Exemple complet de travail/exécutable

```python
%matplotlib inline
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns

iris = sns.load_dataset('iris')
X_iris = iris.drop('species', axis = 1)
X_iris.shape
y_iris = iris['species']
y_iris.shape
rng = np.random.RandomState(35)
x = 10*rng.rand(40)
y = 2*x-1+rng.randn(40)
plt.scatter(x,y);
from sklearn.decomposition import PCA

model = PCA(n_components=2)
model
model.fit(X_iris)
X_2D = model.transform(X_iris)
iris['PCA1'] = X_2D[:, 0]
iris['PCA2'] = X_2D[:, 1]
sns.lmplot("PCA1", "PCA2", hue='species', data=iris, fit_reg=False);
```