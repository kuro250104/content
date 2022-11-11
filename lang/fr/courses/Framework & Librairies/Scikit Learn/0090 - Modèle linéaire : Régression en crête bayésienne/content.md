La régression bayésienne permet un mécanisme naturel pour survivre à des données insuffisantes ou mal distribuées en formulant la régression linéaire en utilisant des distributions de probabilité plutôt que des estimations ponctuelles. La sortie ou la réponse "y" est supposée être tirée d'une distribution de probabilité plutôt qu'estimée comme une valeur unique.

Mathématiquement, pour obtenir un modèle entièrement probabiliste, la réponse y est supposée être distribuée de manière gaussienne autour de Xw𝑋 comme suit :

![modèle mathématique probabiliste](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0090%20-%20Mod%C3%A8le%20lin%C3%A9aire%20%3A%20R%C3%A9gression%20en%20cr%C3%AAte%20bay%C3%A9sienne/images/image1.png)

L'un des types de régression bayésienne les plus utiles est la régression bayésienne de crête qui estime un modèle probabiliste du problème de régression. Ici, l'antériorité du coefficient w est donnée par une gaussienne sphérique, comme suit -

![modèle mathématique de régression bayésienne de crête](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0090%20-%20Mod%C3%A8le%20lin%C3%A9aire%20%3A%20R%C3%A9gression%20en%20cr%C3%AAte%20bay%C3%A9sienne/images/image2.png)

Ce modèle résultant est appelé Bayesian Ridge Regression et dans scikit-learn **sklearn.linear_model.BeyesianRidge**  est le module utilisé.

## Paramètres

La liste suivante présente les paramètres utilisés par le module BayesianRidge :

- **n_iter** - int, facultatif. Il représente le nombre maximum d'itérations. La valeur par défaut est 300 mais la valeur définie par l'utilisateur doit être supérieure ou égale à 1.
- **fit_intercept** - Booléen, facultatif, par défaut True. Il décide si l'intercept doit être calculé pour ce modèle ou non. Aucune interception ne sera utilisée dans le calcul, si elle est définie à false.
- **tol** - float, optionnel, default=1.e-3. Il représente la précision de la solution et arrêtera l'algorithme si w a convergé.
- **alpha_1** - float, optional, default=1.e-6. C'est le 1er hyperparamètre qui est un paramètre de forme pour la distribution Gamma antérieure au paramètre alpha.
- **alpha_2** - float, optional, default=1.e-6. C'est le 2ème hyperparamètre qui est un paramètre d'échelle inverse pour la distribution Gamma antérieure au paramètre alpha.
- **lambda_1** - float, optional, default=1.e-6. C'est le 1er hyperparamètre qui est un paramètre de forme pour la distribution Gamma antérieure au paramètre lambda.
- **lambda_2** - float, optional, default=1.e-6. Il s'agit du 2ème hyperparamètre qui est un paramètre d'échelle inverse pour la priorité de la distribution Gamma sur le paramètre lambda.
- **copy_X** - Booléen, facultatif, par défaut = True. Par défaut, il est vrai, ce qui signifie que X sera copié. Mais s'il est défini à false, X peut être écrasé.
- **compute_score** - booléen, facultatif, par défaut=False. S'il est défini à true, il calcule la vraisemblance marginale logarithmique à chaque itération de l'optimisation.
- **verbose** - Booléen, facultatif, par défaut=False. Par défaut, il est faux mais s'il est vrai, le mode verbeux sera activé pendant l'ajustement du modèle.

## Attributs

La liste suivante présente les attributs utilisés par le module BayesianRidge.

- **coef_** - tableau, forme = n_features. Cet attribut fournit les vecteurs de poids.
- **intercept_** - float. Il représente le terme indépendant dans la fonction de décision.
- **alpha_** - float. Cet attribut fournit la précision estimée du bruit.
- **lambda_** - float. Cet attribut fournit la précision estimée du poids.
- **n_iter_** - int. Il fournit le nombre réel d'itérations prises par l'algorithme pour atteindre le critère d'arrêt.
- **sigma_** - tableau, forme = (n_features, n_features). Il fournit la matrice de variance-covariance estimée des poids.
- **scores_** - tableau, forme = (n_iter_+1). Il fournit la valeur de la vraisemblance marginale logarithmique à chaque itération de l'optimisation. Dans le score résultant, le tableau commence par la valeur de la vraisemblance marginale logarithmique obtenue pour les valeurs initiales de a et λ, et se termine par la valeur obtenue pour a et λ estimés.

## Exemple d'implémentation

Le script Python suivant fournit un exemple simple d'ajustement d'un modèle de régression bayésienne de crête en utilisant le module BayesianRidge de sklearn.

```python
from sklearn import linear_model
X = [[0, 0], [1, 1], [2, 2], [3, 3]]
Y = [0, 1, 2, 3]
BayReg = linear_model.BayesianRidge()
BayReg.fit(X, Y)
```

## Sortie

```python
BayesianRidge(alpha_1 = 1e-06, alpha_2 = 1e-06, compute_score = False, copy_X = True,
    fit_intercept = True, lambda_1 = 1e-06, lambda_2 = 1e-06, n_iter = 300,
    normalize = False, tol=0.001, verbose = False)
```

A partir de la sortie ci-dessus, nous pouvons vérifier les paramètres du modèle utilisés dans le calcul.

## Exemple

Maintenant, une fois ajusté, le modèle peut prédire de nouvelles valeurs comme suit :

```python
BayReg.predict([[1,1]])
```

## Sortie

```python
array([1.00000007])
```

## Exemple

De même, nous pouvons accéder au coefficient w du modèle de la manière suivante :

```python
BayReg.coef_
```

## Sortie

```python
array([0.49999993, 0.49999993])
```