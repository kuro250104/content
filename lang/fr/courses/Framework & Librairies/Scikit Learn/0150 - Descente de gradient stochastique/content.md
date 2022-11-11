Ici, nous allons découvrir un algorithme d'optimisation dans Sklearn, appelé descente de gradient stochastique (SGD - Stochastic Gradient Descent).

La descente de gradient stochastique (SGD) est un algorithme d'optimisation simple mais efficace utilisé pour trouver les valeurs des paramètres/coefficients des fonctions qui minimisent une fonction de coût. En d'autres termes, il est utilisé pour l'apprentissage discriminant de classificateurs linéaires sous des fonctions de perte convexes, comme les SVM et la régression logistique. Il a été appliqué avec succès à des ensembles de données à grande échelle car la mise à jour des coefficients est effectuée pour chaque instance d'apprentissage, plutôt qu'à la fin des instances.

## Classificateur SGD

Le classificateur SGD (Stochastic Gradient Descent) implémente essentiellement une routine d'apprentissage SGD ordinaire prenant en charge diverses fonctions de perte et pénalités pour la classification. Scikit-learn fournit le module SGDClassifier pour implémenter la classification SGD.

### Paramètres

La liste suivante présente les paramètres utilisés par le module SGDClassifier :

- **loss** - str, default = 'hinge' (perte). Il représente la fonction de perte à utiliser lors de la mise en œuvre. La valeur par défaut est 'hinge' qui nous donnera un SVM linéaire. Les autres options qui peuvent être utilisées sont :
    - **log** - Cette perte nous donnera une régression logistique, c'est-à-dire un classificateur probabiliste.
    - **modified_huber** - une perte lisse qui apporte une tolérance aux valeurs aberrantes ainsi que des estimations de probabilité.
    - **squared_hinge** - similaire à la perte 'hinge' mais elle est pénalisée de manière quadratique.
    - **perceptron** - comme son nom l'indique, il s'agit d'une perte linéaire qui est utilisée par l'algorithme perceptron.
- **penalty** - str, 'none', 'l2', 'l1', 'elasticnet'. Il s'agit du terme de régularisation utilisé dans le modèle. Par défaut, il s'agit de L2. Nous pouvons également utiliser L1 ou 'elasticnet', mais ces deux termes risquent d'apporter de la sparsité au modèle, ce qui n'est pas réalisable avec L2.
- **alpha** - flottant, par défaut = 0,0001. Alpha, la constante qui multiplie le terme de régularisation, est le paramètre d'accord qui décide dans quelle mesure nous voulons pénaliser le modèle. La valeur par défaut est 0.0001.
- **l1_ratio** - float, default = 0.15. Il s'agit du paramètre de mélange ElasticNet. Sa plage est 0 < = l1_ratio < = 1. Si l1_ratio = 1, la pénalité serait la pénalité L1. Si l1_ratio = 0, la pénalité serait une pénalité L2.
- **fit_intercept** - Booléen, Défaut=True. Ce paramètre indique si une constante (biais ou intercept) doit être ajoutée à la fonction de décision. Aucune ordonnée à l'origine ne sera utilisée dans le calcul et les données seront supposées être déjà centrées, s'il est défini à false.
- **tol** - flottant ou aucun, facultatif, par défaut = 1.e-3. Ce paramètre représente le critère d'arrêt des itérations. Sa valeur par défaut est False mais s'il est défini sur None, les itérations s'arrêteront lorsque 𝒍loss > best_loss - tol pour n_iter_no_changesuccessives époques.
- **shuffle** - Booléen, facultatif, par défaut = True. Ce paramètre indique si nous voulons que nos données d'entraînement soient mélangées après chaque époque ou non.
- **verbose** - entier, par défaut = 0. Il représente le niveau de verbosité. Sa valeur par défaut est 0.
- **epsilon** - float, default = 0.1. Ce paramètre spécifie la largeur de la région insensible. Si loss = 'epsilon-insensitive', toute différence, entre la prédiction actuelle et l'étiquette correcte, inférieure au seuil sera ignorée.
- **max_iter** - int, optionnel, défaut = 1000. Comme son nom l'indique, il représente le nombre maximum de passages sur les époques, c'est-à-dire les données d'entraînement.
- **warm_start** - bool, optional, default = false. Avec ce paramètre réglé sur True, nous pouvons réutiliser la solution de l'appel précédent à fit comme initialisation. Si nous choisissons la valeur par défaut, c'est-à-dire false, la solution précédente sera effacée.
- **random_state** - int, RandomState instance ou None, facultatif, par défaut = none. Ce paramètre représente la graine du nombre pseudo-aléatoire généré qui est utilisé lors du brassage des données. Les options suivantes sont disponibles :
    - **int** - Dans ce cas, random_state est la graine utilisée par le générateur de nombres aléatoires.
    - **RandomState instance** - Dans ce cas, random_state est le générateur de nombres aléatoires.
    - **None** - Dans ce cas, le générateur de nombres aléatoires est l'instance RandonState utilisée par np.random.
- **n_jobs** - int ou none, optionnel, Défaut = None. Il représente le nombre de CPUs à utiliser dans le calcul OVA (One Versus All), pour les problèmes multi-classes. La valeur par défaut est none, ce qui signifie 1.
- **learning_rate** - chaîne de caractères, facultatif, par défaut = 'optimal'.
Si le taux d'apprentissage est 'constant', eta = eta0 ;
Si le taux d'apprentissage est 'optimal', eta = 1.0/(alpha*(t+t0)), où t0 est choisi par Leon Bottou ;
Si le taux d'apprentissage est 'invscalling', eta = eta0/pow(t, power_t).
Si le taux d'apprentissage = 'adaptatif', eta = eta0.
    - **eta0** - double, par défaut = 0,0. Il représente le taux d'apprentissage initial pour les options de taux d'apprentissage mentionnées ci-dessus, c'est-à-dire 'constant', 'invscalling' ou 'adaptive'.
    - **power_t** - idouble, par défaut = 0.5. C'est l'exposant pour le taux d'apprentissage 'incscalling'.
    - **early_stopping** - bool, default = False. Ce paramètre représente l'utilisation de l'arrêt précoce pour terminer l'apprentissage lorsque le score de validation ne s'améliore pas. Sa valeur par défaut est false mais lorsqu'il est réglé sur true, il met automatiquement de côté une fraction stratifiée de données d'apprentissage comme validation et arrête l'apprentissage lorsque le score de validation ne s'améliore pas.
    - **validation_fraction** - float, default = 0.1. Il n'est utilisé que lorsque early_stopping est vrai. Il représente la proportion de données d'entraînement à mettre de côté comme ensemble de validation pour l'arrêt précoce des données d'entraînement....
- **n_iter_no_change** - int, default=5. Il représente le nombre d'itérations sans amélioration que l'algorithme doit exécuter avant l'arrêt précoce.
- **class_weight** - dict, {class_label : weight} ou "balanced", ou None, optional. Ce paramètre représente les poids associés aux classes. S'il n'est pas fourni, les classes sont supposées avoir le poids 1.
- **warm_start** - bool, optionnel, par défaut = false. Avec ce paramètre réglé sur True, nous pouvons réutiliser la solution de l'appel précédent à fit comme initialisation. Si nous choisissons la valeur par défaut, c'est-à-dire false, cela effacera la solution précédente.
- **average** - iBooléen ou int, facultatif, par défaut = false. Il représente le nombre de CPU à utiliser dans le calcul OVA (One Versus All), pour les problèmes multi-classes. La valeur par défaut est none, ce qui signifie 1.

### Attributs

La liste suivante présente les attributs utilisés par le module SGDClassifier :

- **coef_** - tableau, forme (1, n_features) si n_classes==2, sinon (n_classes, n_features). Cet attribut fournit le poids attribué aux caractéristiques.
- **intercept_** - tableau, forme (1,) si n_classes==2, sinon (n_classes,). Il représente le terme indépendant dans la fonction de décision.
- **n_iter_** - int. Il donne le nombre d'itérations pour atteindre le critère d'arrêt.

### Exemples d'implémentation

Comme d'autres classificateurs, la descente par gradient stochastique (SGD) doit être équipée des deux tableaux suivants : 

- Un tableau X contenant les échantillons d'entraînement. Il est de taille [n_samples, n_features].
- Un tableau Y contenant les valeurs cibles, c'est-à-dire les étiquettes de classe pour les échantillons d'apprentissage. Il est de taille [n_échantillons].

#### Exemple

Le script Python suivant utilise le modèle linéaire SGDClassifier :

```python
import numpy as np
from sklearn import linear_model
X = np.array([[-1, -1], [-2, -1], [1, 1], [2, 1]])
Y = np.array([1, 1, 2, 2])
SGDClf = linear_model.SGDClassifier(max_iter = 1000, tol=1e-3,penalty = "elasticnet")
SGDClf.fit(X, Y)
```

#### Sortie

```python
SGDClassifier(
    alpha = 0.0001, average = False, class_weight = None,
    early_stopping = False, epsilon = 0.1, eta0 = 0.0, fit_intercept = True,
    l1_ratio = 0.15, learning_rate = 'optimal', loss = 'hinge', max_iter = 1000,
    n_iter = None, n_iter_no_change = 5, n_jobs = None, penalty = 'elasticnet',
    power_t = 0.5, random_state = None, shuffle = True, tol = 0.001,
    validation_fraction = 0.1, verbose = 0, warm_start = False
)
```

#### Exemple

Maintenant, une fois ajusté, le modèle peut prédire de nouvelles valeurs comme suit :

```python
SGDClf.predict([[2.,2.]])
```

#### Sortie

```python
array([2])
```

#### Exemple

Pour l'exemple ci-dessus, nous pouvons obtenir le vecteur poids à l'aide du script python suivant :

```python
SGDClf.coef_
```

#### Sortie

```python
array([[19.54811198, 9.77200712]])
```

#### Exemple

De même, nous pouvons obtenir la valeur d'intercept à l'aide du script python suivant :

```python
SGDClf.intercept_
```

#### Sortie

```python
array([10.])
```

#### Exemple

Nous pouvons obtenir la distance signée par rapport à l'hyperplan en utilisant SGDClassifier.decision_function, comme dans le script python suivant :

```python
SGDClf.decision_function([[2., 2.]])
```

#### Sortie

```python
array([68.6402382])
```

## Régresseur SGD

Le régresseur SGD (Stochastic Gradient Descent) implémente essentiellement une routine d'apprentissage SGD simple prenant en charge diverses fonctions de perte et pénalités pour ajuster les modèles de régression linéaire. Scikit-learn fournit le module **SGDRegressor** pour mettre en œuvre la régression SGD.

### Paramètres

Les paramètres utilisés par **SGDRegressor** sont presque les mêmes que ceux utilisés dans le module **SGDClassifier**. La différence réside dans le paramètre 'loss'. Pour le paramètre de perte du module **SGDRegressor** les valeurs positives sont les suivantes :

- **squared_loss** - Il s'agit de l'ajustement ordinaire des moindres carrés.
- **huber : SGDRegressor** - corrige les valeurs aberrantes en passant de la perte quadratique à la perte linéaire au-delà d'une distance d'epsilon. Le travail de 'huber' est de modifier 'squared_loss' pour que l'algorithme se concentre moins sur la correction des valeurs aberrantes.
- **epsilon_insensitive** - En fait, il ignore les erreurs inférieures à epsilon.
- **squared_epsilon_insensitive** - C'est la même chose que epsilon_insensitive. La seule différence est qu'elle devient une perte au carré au-delà d'une tolérance d'epsilon.

Une autre différence est que le paramètre nommé 'power_t' a la valeur par défaut de 0.25 plutôt que 0.5 comme dans SGDClassifier. De plus, il n'a pas les paramètres 'class_weight' et 'n_jobs'.

### Attributs

Les attributs de SGDRegressor sont également les mêmes que ceux du module SGDClassifier. En revanche, il possède trois attributs supplémentaires, à savoir :

- **average_coef_** - tableau, forme(n_features,). Comme son nom l'indique, il fournit les poids moyens attribués aux caractéristiques.
- **average_intercept_** - tableau, forme(1,). Comme son nom l'indique, il fournit le terme d'interception moyen.
- **t_** - int. Il fournit le nombre de mises à jour de poids effectuées pendant la phase d'apprentissage.

Les attributs average_coef_ et average_intercept_ fonctionneront après avoir activé le paramètre 'average' sur True.

### Exemple de mise en œuvre

#### Exemple

Le script Python suivant utilise le modèle linéaire SGDRegressor :

```python
import numpy as np
from sklearn import linear_model
n_samples, n_features = 10, 5
rng = np.random.RandomState(0)
y = rng.randn(n_samples)
X = rng.randn(n_samples, n_features)
SGDReg =linear_model.SGDRegressor(
    max_iter = 1000,penalty = "elasticnet",loss = 'huber',tol = 1e-3, average =  True
)
SGDReg.fit(X, y)
```

#### Sortie

```python
SGDRegressor(
    alpha = 0.0001, average = True, early_stopping = False, epsilon = 0.1,
    eta0 = 0.01, fit_intercept = True, l1_ratio = 0.15,
    learning_rate = 'invscaling', loss = 'huber', max_iter = 1000,
    n_iter = None, n_iter_no_change = 5, penalty = 'elasticnet', power_t = 0.25,
    random_state = None, shuffle = True, tol = 0.001, validation_fraction = 0.1,
    verbose = 0, warm_start = False
)
```

#### Exemple

Maintenant, une fois ajusté, nous pouvons obtenir le vecteur de poids à l'aide du script python suivant :

````python
SGDReg.coef_
````

#### Sortie

````python
array([-0.00423314, 0.00362922, -0.00380136, 0.00585455, 0.00396787])
````

#### Exemple

De même, nous pouvons obtenir la valeur d'intercept à l'aide du script python suivant -

````python
SGReg.intercept_
````

#### Sortie

````python
SGReg.intercept_
````

#### Exemple

Nous pouvons obtenir le nombre de mises à jour de poids pendant la phase de formation à l'aide du script python suivant :

````python
SGDReg.t_
````

#### Sortie

````python
61.0
````

## Avantages et inconvénients du SGD

### Avantages

- La descente de gradient stochastique (SGD) est très efficace.
- Il est très facile à mettre en œuvre car il existe de nombreuses possibilités d'ajustement du code.

### Inconvénients

- La descente stochastique par gradient (SGD) nécessite plusieurs hyperparamètres comme les paramètres de régularisation.
- Elle est sensible à l'échelle des caractéristiques.