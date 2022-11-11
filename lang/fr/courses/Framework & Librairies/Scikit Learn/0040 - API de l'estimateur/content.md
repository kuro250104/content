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