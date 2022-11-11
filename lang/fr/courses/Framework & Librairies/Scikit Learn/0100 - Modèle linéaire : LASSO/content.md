LASSO (Opérateur de sélection et de rétrécissement le moins absolu - Least Absolute Shrinkage and Selection Operator) est la technique de régularisation qui effectue une régularisation L1. Elle modifie la fonction de perte en ajoutant la pénalité (quantité de rétrécissement) équivalente à la somme de la valeur absolue des coefficients.

![Formule mathématique de LASSO](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0100%20-%20Mod%C3%A8le%20lin%C3%A9aire%20%3A%20LASSO/images/image1.png)

```sklearn.linear_model.lasso``` est un modèle linéaire, avec un terme de régularisation ajouté, utilisé pour estimer des coefficients épars.

## Paramètres

La liste suivante présente les paramètres utilisés par le module Lasso.

- **alpha** - flottant, facultatif, par défaut = 1,0. Alpha, la constante qui multiplie le terme L1, est le paramètre d'accord qui décide dans quelle mesure nous voulons pénaliser le modèle. La valeur par défaut est 1.0.
- **fit_intercept** - Booléen, facultatif. Par défaut=True. Ce paramètre indique qu'une constante (biais ou intercept) doit être ajoutée à la fonction de décision. Aucun intercept ne sera utilisé dans le calcul, s'il est défini à false.
- **tol** - flottant, facultatif. Ce paramètre représente la tolérance pour l'optimisation. La valeur tol et les mises à jour seront comparées et si les mises à jour trouvées sont inférieures à tol, l'optimisation vérifie l'optimalité du double écart et continue jusqu'à ce qu'il soit inférieur à tol.
- **normalize** - Booléen, facultatif, par défaut = False. Si ce paramètre est défini sur True, le régresseur X sera normalisé avant la régression. La normalisation sera effectuée en soustrayant la moyenne et en la divisant par la norme L2. Si fit_intercept = False, ce paramètre sera ignoré.
- **copy_X** - Booléen, facultatif, par défaut = True. Par défaut, il est vrai, ce qui signifie que X sera copié. Mais s'il est défini à false, X peut être écrasé.
- **max_iter** - int, facultatif. Comme son nom l'indique, il représente le nombre maximum d'itérations prises pour les solveurs à gradient conjugué.
- **precompute** - True|False|array-like, default=False. Avec ce paramètre, nous pouvons décider d'utiliser une matrice de Gram précalculée pour accélérer le calcul ou non.
- **warm_start** - bool, optionnel, par défaut = false. Avec ce paramètre réglé sur True, nous pouvons réutiliser la solution de l'appel précédent à fit comme initialisation. Si nous choisissons la valeur par défaut, c'est-à-dire false, cela effacera la solution précédente.
- **random_state** - int, RandomState instance ou None, facultatif, par défaut = none. Ce paramètre représente la graine du nombre pseudo-aléatoire généré qui est utilisé lors du brassage des données. Les options suivantes sont disponibles :
    - **int** - Dans ce cas, random_state est la graine utilisée par le générateur de nombres aléatoires.
    - **RandomState instance** - Dans ce cas, random_state est le générateur de nombres aléatoires.
    - **None** - Dans ce cas, le générateur de nombres aléatoires est l'instance RandonState utilisée par np.random.
- **selection** - str, default='cyclic' (sélection)
    - **Cyclique** - La valeur par défaut est cyclique, ce qui signifie que les caractéristiques seront bouclées séquentiellement par défaut.
    - **Random** - Si nous définissons la sélection comme aléatoire, un coefficient aléatoire sera mis à jour à chaque itération.

## Attributs

La liste suivante présente les attributs utilisés par le module Lasso :

- **coef_** - tableau, shape(n_features,) ou (n_target, n_features). Cet attribut fournit les vecteurs de poids.
- **Intercept_** - float | tableau, shape = (n_targets). Il représente le terme indépendant dans la fonction de décision.
- **n_iter_** - int ou tableau, forme (n_targets). Il donne le nombre d'itérations effectuées par le solveur de descente de coordonnées pour atteindre la tolérance spécifiée.

## Exemple d'implémentation

Le script Python suivant utilise le modèle Lasso qui utilise en outre la descente de coordonnées comme algorithme pour ajuster les coefficients.

```python
from sklearn import linear_model
Lreg = linear_model.Lasso(alpha = 0.5)
Lreg.fit([[0,0], [1, 1], [2, 2]], [0, 1, 2])
```

## Sortie

```python
Lasso(alpha = 0.5, copy_X = True, fit_intercept = True, max_iter = 1000,
    normalize = False, positive = False, precompute = False, random_state = None,
    selection = 'cyclic', tol = 0.0001, warm_start = False)
```

## Exemple

Maintenant, une fois ajusté, le modèle peut prédire de nouvelles valeurs comme suit :

```python
Lreg.predict([[0,1]])
```

## Sortie

```python
array([0.75])
```

## Exemple

Pour l'exemple ci-dessus, nous pouvons obtenir le vecteur poids à l'aide du script python suivant :

```python
Lreg.coef_
```

## Sortie

```python
array([0.25, 0. ])
```

## Exemple

De même, nous pouvons obtenir la valeur d'intercept à l'aide du script python suivant :

```python
Lreg.intercept_
```

## Sortie

```python
0.75
```

## Exemple

Nous pouvons obtenir le nombre total d'itérations pour obtenir la tolérance spécifiée à l'aide du script python suivant :

```python
Lreg.n_iter_
```

## Sortie

```python
2
```

Nous pouvons modifier les valeurs des paramètres pour obtenir la sortie souhaitée du modèle.