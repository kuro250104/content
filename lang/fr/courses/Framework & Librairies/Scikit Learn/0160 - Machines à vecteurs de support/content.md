## Introduction

Les machines à vecteurs de support (SVM) sont des méthodes d'apprentissage supervisé puissantes et flexibles utilisées pour la classification, la régression et la détection des valeurs aberrantes. Les SVM sont très efficaces dans les espaces de grande dimension et sont généralement utilisés dans les problèmes de classification. Les SVM sont populaires et économes en mémoire car ils utilisent un sous-ensemble de points d'apprentissage dans la fonction de décision.

L'objectif principal des SVM est de diviser les ensembles de données en un certain nombre de classes afin de trouver un **hyperplan marginal maximal (MMH)**, ce qui peut être fait en deux étapes : 1.

- Les machines à vecteurs de support génèrent d'abord itérativement des hyperplans qui séparent les classes de la meilleure façon.
- Ensuite, il choisira l'hyperplan qui sépare correctement les classes.

Quelques concepts importants dans le SVM sont les suivants .

- **Support Vectors** − Ils peuvent être définis comme les points de données les plus proches de l'hyperplan. Les vecteurs de support aident à décider de la ligne de séparation.
- **Hyperplane** − Le plan ou l'espace de décision qui divise un ensemble d'objets ayant des classes différentes.
- **Margin** − L'écart entre deux lignes sur les points de données rapprochés de classes différentes est appelé marge.

Le SVM de Scikit-learn prend en charge les vecteurs d'échantillons épars et denses comme entrée.

## Classification of SVM

Scikit-learn fournit trois classes, à savoir SVC, NuSVC et LinearSVC, qui peuvent effectuer une classification multi-classes.

## SVC

Il s'agit d'une classification vectorielle de support en C dont l'implémentation est basée sur libsvm. Le module utilisé par scikit-learn est ```sklearn.svm.SVC```. Cette classe gère le support multi classe selon le schéma one-vs-one.

### Paramètres

La liste suivante présente les paramètres utilisés par la classe ```sklearn.svm.SVC```.

**Paramètre et description**

- **C** − float, optional, default = 1.0 - C'est le paramètre de pénalité du terme d'erreur.
- **kernel** − string, optional, default = ‘rbf’ - Ce paramètre spécifie le type de noyau à utiliser dans l'algorithme. Nous pouvons choisir n'importe lequel parmi 'linear', 'poly', 'rbf', 'sigmoïde', 'precomputed'. La valeur par défaut du noyau est "rbf".
- **degree** − int, optional, default = 3 - Il représente le degré de la fonction noyau 'poly' et sera ignoré par tous les autres noyaux.
- **gamma** − {‘scale’, ‘auto’} or float, - Il s'agit du coefficient du noyau pour les noyaux 'rbf', 'poly' et 'sigmoïde'.
- **optinal default** − = ‘scale’ - Si vous choisissez la valeur par défaut, c'est-à-dire gamma = 'scale', la valeur du gamma à utiliser par le SVC est 1/(𝑛_𝑓𝑒𝑎𝑡𝑢𝑟𝑒𝑠∗𝑋.𝑣𝑎𝑟()). En revanche, si gamma= 'auto', il utilise 1/𝑛_𝑓𝑒𝑎𝑡𝑢𝑟𝑒𝑠.
- **coef0** − float, optional, Default=0.0 - Un terme indépendant dans la fonction noyau qui n'est significatif que dans 'poly' et 'sigmoïde'.
- **tol** − float, optional, default = 1.e-3 - Ce paramètre représente le critère d'arrêt des itérations.
- **shrinking** − Boolean, optional, default = True - Ce paramètre indique si nous voulons utiliser l'heuristique de réduction ou non.
- **verbose** − Boolean, default: false - Il active ou désactive la sortie verbeuse. Sa valeur par défaut est false.
- **probability** − boolean, optional, default = true - Ce paramètre active ou désactive les estimations de probabilité. La valeur par défaut est false, mais il doit être activé avant d'appeler fit.
- **max_iter** − int, optional, default = -1 - Comme son nom l'indique, elle représente le nombre maximum d'itérations dans le solveur. La valeur -1 signifie qu'il n'y a pas de limite au nombre d'itérations.
- **cache_size** − float, optional - Ce paramètre spécifie la taille du cache du noyau. La valeur sera en MB (MegaBytes).
- **random_state** − int, RandomState instance or None, optional, default = none - Ce paramètre représente la graine du nombre pseudo-aléatoire généré qui est utilisé lors du brassage des données. Les options suivantes sont disponibles
    - **int** − Dans ce cas, random_state est la graine utilisée par le générateur de nombres aléatoires.
    - **RandomState instance** − Dans ce cas, random_state est le générateur de nombres aléatoires.
    - **None** − Dans ce cas, le générateur de nombres aléatoires est l'instance RandonState utilisée par np.random.
- **class_weight** − {dict, ‘balanced’}, optional - Ce paramètre va fixer le paramètre C de la classe j à 𝑐𝑙𝑎𝑠𝑠_𝑤𝑒𝑖𝑔ℎ𝑡[𝑗]∗𝐶 pour le SVC. Si nous utilisons l'option par défaut, cela signifie que toutes les classes sont censées avoir le poids un. En revanche, si vous choisissez class_weight:balanced, il utilisera les valeurs de y pour ajuster automatiquement les poids.
- **decision_function_shape** − ovo’, ‘ovr’, default = ‘ovr’ - Ce paramètre décidera si l'algorithme retournera la fonction de décision 'ovr' (one-vs-rest) de la forme comme tous les autres classificateurs, ou la fonction de décision originale ovo(one-vs-one) de libsvm.
- **break_ties** − boolean, optional, default = false - 
    - **Véritable** − La prédiction départagera les ex-aequo en fonction des valeurs de confiance de la fonction décisionnelle.
    - **Faux** − Le prédicteur renverra la première classe parmi les classes ex aequo.

### Attributs

Followings table consist the attributes used by sklearn.svm.SVC class −

**Attributs et description**

- **support_** − array-like, shape = [n_SV] - Elle renvoie les indices des vecteurs de support.
- **support_vectors_** − array-like, shape = [n_SV, n_features] - Elle renvoie les vecteurs de support.
- **n_support_** − array-like, dtype=int32, shape = [n_class] - Il représente le nombre de vecteurs de support pour chaque classe.
- **dual_coef_** − array, shape = [n_class-1,n_SV] - Ce sont les coefficients des vecteurs de support dans la fonction de décision.
- **coef_** − array, shape = [n_class * (n_class-1)/2, n_features] - Cet attribut, disponible uniquement en cas de noyau linéaire, fournit le poids attribué aux caractéristiques.
- **intercept_** − array, shape = [n_class * (n_class-1)/2] - Il représente le terme indépendant (constante) dans la fonction de décision.
- **fit_status_** − int - La sortie serait 0 si elle est correctement installée. La sortie sera de 1 si elle est incorrectement installée.
- **classes_** − array of shape = [n_classes] - Il donne les étiquettes des classes.

### Exemple de mise en œuvre

Comme d'autres classificateurs, le SVC doit également être équipé des deux tableaux suivants -

- Un tableau X contenant les échantillons d'apprentissage. Il est de taille [n_samples, n_features]. 
- Un tableau Y contenant les valeurs cibles, c'est-à-dire les étiquettes de classe pour les échantillons d'apprentissage. Il est de taille [n_échantillons].

Le script Python suivant utilise la classe sklearn.svm.SVC.

```python
import numpy as np
X = np.array([[-1, -1], [-2, -1], [1, 1], [2, 1]])
y = np.array([1, 1, 2, 2])
from sklearn.svm import SVC
SVCClf = SVC(kernel = 'linear',gamma = 'scale', shrinking = False,)
SVCClf.fit(X, y)
```

### Sortie

```python
SVC(C = 1.0, cache_size = 200, class_weight = None, coef0 = 0.0,
    decision_function_shape = 'ovr', degree = 3, gamma = 'scale', kernel = 'linear',
    max_iter = -1, probability = False, random_state = None, shrinking = False,
    tol = 0.001, verbose = False)
```

### Exemple

Maintenant, une fois ajusté, nous pouvons obtenir le vecteur de poids à l'aide du script python suivant -.

```python
SVCClf.coef_
```

### Sortie

```python
array([[0.5, 0.5]])
```

### Exemple

De la même manière, nous pouvons obtenir la valeur des autres attributs comme suit -

```python
SVCClf.predict([[-0.5,-0.8]])
```

### Sortie

```python
array([1])
```

### Exemple

```python
SVCClf.n_support_
```

### Sortie

```python
array([1, 1])
```

### Exemple

```python
SVCClf.support_vectors_
```

### Sortie

```python
array(
    [
        [-1., -1.],
        [ 1., 1.]
    ]
)
```

### Exemple

```python
SVCClf.support_
```

### Sortie

```python
array([0, 2])
```

### Exemple

```python
SVCClf.intercept_
```

### Sortie

```python
array([-0.])
```

### Exemple

```python
SVCClf.fit_status_
```

### Sortie

```python
0
```

## NuSVC

NuSVC est Nu Support Vector Classification. C'est une autre classe fournie par scikit-learn qui peut effectuer une classification multi-classes. C'est comme la SVC mais NuSVC accepte des jeux de paramètres légèrement différents. Le paramètre qui est différent de SVC est le suivant : ```nu - flotteur, facultatif, par défaut = 0,5```

Il représente une limite supérieure de la fraction des erreurs de formation et une limite inférieure de la fraction des vecteurs de support. Sa valeur doit être comprise dans l'intervalle (o,1). Les autres paramètres et attributs sont les mêmes que ceux du SVC.

### Exemple de mise en œuvre

Nous pouvons également mettre en œuvre le même exemple en utilisant la classe ```sklearn.svm.NuSVC```.

```python
import numpy as np
X = np.array([[-1, -1], [-2, -1], [1, 1], [2, 1]])
y = np.array([1, 1, 2, 2])
from sklearn.svm import NuSVC
NuSVCClf = NuSVC(kernel = 'linear',gamma = 'scale', shrinking = False,)
NuSVCClf.fit(X, y)
```

### Sortie

```python
NuSVC(cache_size = 200, class_weight = None, coef0 = 0.0,
    decision_function_shape = 'ovr', degree = 3, gamma = 'scale', kernel = 'linear',
    max_iter = -1, nu = 0.5, probability = False, random_state = None,
    shrinking = False, tol = 0.001, verbose = False)
```

Nous pouvons obtenir les sorties du reste des attributs comme dans le cas du SVC.

## LinearSVC

Il s'agit de la classification linéaire par vecteurs de support. Elle est similaire à la SVC avec un noyau = 'linear'. La différence entre eux est que LinearSVC est implémenté en termes de liblinear alors que SVC est implémenté en libsvm. C'est la raison pour laquelle LinearSVC a plus de flexibilité dans le choix des pénalités et des fonctions de perte. Il s'adapte également mieux à un grand nombre d'échantillons.

Si nous parlons de ses paramètres et attributs, il ne prend pas en charge le "noyau" car il est supposé être linéaire et il lui manque également certains attributs comme support_, support_vectors_, n_support_, fit_status_ et dual_coef_.

Cependant, il prend en charge les paramètres de pénalité et de perte comme suit -

- **penalty** - chaîne de caractères, L1 ou L2(default = 'L2') -  Ce paramètre est utilisé pour spécifier la norme (L1 ou L2) utilisée dans la pénalisation (régularisation).
- **loss** - string, hinge, squared_hinge (default = squared_hinge) - Il représente la fonction de perte où 'hinge' est la perte SVM standard et 'squared_hinge' est le carré de la perte hinge.

### Exemple de mise en œuvre

Le script Python suivant utilise la classe sklearn.svm.LinearSVC.

```python
from sklearn.svm import LinearSVC
from sklearn.datasets import make_classification
X, y = make_classification(n_features = 4, random_state = 0)
LSVCClf = LinearSVC(dual = False, random_state = 0, penalty = 'l1',tol = 1e-5)
LSVCClf.fit(X, y)
```

### Sortie

```python
LinearSVC(C = 1.0, class_weight = None, dual = False, fit_intercept = True,
    intercept_scaling = 1, loss = 'squared_hinge', max_iter = 1000,
    multi_class = 'ovr', penalty = 'l1', random_state = 0, tol = 1e-05, verbose = 0)
```

### Exemple

Maintenant, une fois ajusté, le modèle peut prédire de nouvelles valeurs comme suit -

```python
LSVCClf.predict([[0,0,0,0]])
```

### Sortie

```python
[1]
```

### Exemple

Pour l'exemple ci-dessus, nous pouvons obtenir le vecteur poids à l'aide du script python suivant -

```python
LSVCClf.coef_
```

### Sortie

```python
[[0. 0. 0.91214955 0.22630686]]
```

### Exemple

De même, nous pouvons obtenir la valeur d'intercept à l'aide du script python suivant -

```python
LSVCClf.intercept_
```

### Sortie

```python
[0.26860518]
```

## Regression with SVM

Comme nous l'avons vu précédemment, le SVM est utilisé pour les problèmes de classification et de régression. La méthode de classification par vecteurs de support (SVC) de Scikit-learn peut être étendue pour résoudre également les problèmes de régression. Cette méthode étendue est appelée Régression par vecteur de support (SVR).

### Similitude de base entre SVM et SVR

Le modèle créé par le SVC ne dépend que d'un sous-ensemble de données d'entraînement. Pourquoi ? Parce que la fonction de coût pour la construction du modèle ne se soucie pas des points de données d'apprentissage qui se trouvent en dehors de la marge.

Le modèle produit par le SVR (Support Vector Regression) ne dépend lui aussi que d'un sous-ensemble de données d'apprentissage. Pourquoi ? Parce que la fonction de coût pour construire le modèle ignore tous les points de données d'apprentissage proches de la prédiction du modèle.

Scikit-learn fournit trois classes, à savoir SVR, NuSVR et LinearSVR, qui sont trois implémentations différentes de SVR.

## SVR

Il s'agit d'une régression par vecteur support Epsilon dont l'implémentation est basée sur libsvm. Contrairement à SVC, il y a deux paramètres libres dans le modèle, à savoir 'C' et 'epsilon'.

- **epsilon** - float, optionnel, par défaut = 0.1

Il représente l'epsilon dans le modèle epsilon-SVR, et spécifie le tube epsilon à l'intérieur duquel aucune pénalité n'est associée dans la fonction de perte d'apprentissage aux points prédits à une distance epsilon de la valeur réelle.

Le reste des paramètres et attributs sont similaires à ceux que nous avons utilisés dans le SVC.

### Exemple de mise en œuvre

Le script Python suivant utilise la classe sklearn.svm.SVR.

```python
from sklearn import svm
X = [[1, 1], [2, 2]]
y = [1, 2]
SVRReg = svm.SVR(kernel = 'linear', gamma = 'auto')
SVRReg.fit(X, y)
```

### Sortie

```python
SVR(C = 1.0, cache_size = 200, coef0 = 0.0, degree = 3, epsilon = 0.1, gamma = 'auto',
    kernel = 'linear', max_iter = -1, shrinking = True, tol = 0.001, verbose = False)
```

### Exemple

Maintenant, une fois ajusté, nous pouvons obtenir le vecteur de poids à l'aide du script python suivant -.

```python
SVRReg.coef_
```

### Sortie

```python
array([[0.4, 0.4]])
```

### Exemple

De la même manière, nous pouvons obtenir la valeur des autres attributs comme suit -

```python
SVRReg.predict([[1,1]])
```

### Sortie

```python
array([1.1])
```

De même, nous pouvons obtenir les valeurs d'autres attributs.

## NuSVR

NuSVR est Nu Support Vector Regression. C'est comme NuSVC, mais NuSVR utilise un paramètre nu pour contrôler le nombre de vecteurs de support. Et de plus, contrairement à NuSVC où nu remplace le paramètre C, ici il remplace epsilon.

### Exemple de mise en œuvre

Le script Python suivant utilise la classe sklearn.svm.SVR.

```python
from sklearn.svm import NuSVR
import numpy as np
n_samples, n_features = 20, 15
np.random.seed(0)
y = np.random.randn(n_samples)
X = np.random.randn(n_samples, n_features)
NuSVRReg = NuSVR(kernel = 'linear', gamma = 'auto',C = 1.0, nu = 0.1)^M
NuSVRReg.fit(X, y)
```

### Sortie

```python
NuSVR(C = 1.0, cache_size = 200, coef0 = 0.0, degree = 3, gamma = 'auto',
    kernel = 'linear', max_iter = -1, nu = 0.1, shrinking = True, tol = 0.001,
    verbose = False)
```

### Exemple

Maintenant, une fois ajusté, nous pouvons obtenir le vecteur de poids à l'aide du script python suivant -.

```python
NuSVRReg.coef_
```

### Sortie

```python
array(
    [
        [-0.14904483, 0.04596145, 0.22605216, -0.08125403, 0.06564533,
        0.01104285, 0.04068767, 0.2918337 , -0.13473211, 0.36006765,
        -0.2185713 , -0.31836476, -0.03048429, 0.16102126, -0.29317051]
    ]
)
```

De même, nous pouvons obtenir la valeur d'autres attributs.

## LinearSVR

Il s'agit de la régression linéaire par vecteur de support. Elle est similaire à la SVR avec un noyau = 'linéaire'. La différence entre eux est que LinearSVR est implémenté en termes de liblinear, alors que SVC est implémenté en libsvm. C'est la raison pour laquelle LinearSVR a plus de flexibilité dans le choix des pénalités et des fonctions de perte. Il s'adapte également mieux à un grand nombre d'échantillons.

Si nous parlons de ses paramètres et attributs, il ne prend pas en charge le "noyau" car il est supposé être linéaire et il lui manque également certains attributs comme support_, support_vectors_, n_support_, fit_status_ et dual_coef_.

Toutefois, il prend en charge les paramètres de "perte" comme suit

- **loss** - chaîne de caractères, facultatif, par défaut = 'epsilon_insensitive'.

Il représente la fonction de perte où la perte epsilon_insensible est la perte L1 et la perte epsilon-insensible au carré est la perte L2.

### Exemple de mise en œuvre

Le script Python suivant utilise la classe sklearn.svm.LinearSVR.

```python
from sklearn.svm import LinearSVR
from sklearn.datasets import make_regression
X, y = make_regression(n_features = 4, random_state = 0)
LSVRReg = LinearSVR(dual = False, random_state = 0,
loss = 'squared_epsilon_insensitive',tol = 1e-5)
LSVRReg.fit(X, y)
```

### Sortie

```python
LinearSVR(
    C=1.0, dual=False, epsilon=0.0, fit_intercept=True,
    intercept_scaling=1.0, loss='squared_epsilon_insensitive',
    max_iter=1000, random_state=0, tol=1e-05, verbose=0
)
```

### Exemple

Maintenant, une fois ajusté, le modèle peut prédire de nouvelles valeurs comme suit -

```python
LSRReg.predict([[0,0,0,0]])
```

### Sortie

```python
array([-0.01041416])
```

### Exemple

Pour l'exemple ci-dessus, nous pouvons obtenir le vecteur poids à l'aide du script python suivant -

```python
LSRReg.coef_
```

### Sortie

```python
array([20.47354746, 34.08619401, 67.23189022, 87.47017787])
```

### Exemple

De même, nous pouvons obtenir la valeur d'intercept à l'aide du script python suivant -

```python
LSRReg.intercept_
```

### Sortie

```python
array([-0.01041416])
```