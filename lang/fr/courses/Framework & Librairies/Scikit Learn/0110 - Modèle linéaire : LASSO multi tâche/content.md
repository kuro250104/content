Il permet d'ajuster conjointement des problèmes de régression multiple en imposant que les caractéristiques sélectionnées soient les mêmes pour tous les problèmes de régression, également appelés tâches. Sklearn fournit un modèle linéaire nommé MultiTaskLasso, entraîné avec une norme mixte L1, L2 pour la régularisation, qui estime les coefficients épars pour les problèmes de régression multiple conjointement. Dans ce modèle, la réponse y est un tableau 2D de forme (n_échantillons, n_tâches).

Les paramètres et les attributs de MultiTaskLasso sont similaires à ceux de Lasso. La seule différence réside dans le paramètre alpha. Dans Lasso, le paramètre alpha est une constante qui multiplie la norme L1, alors que dans Multi-task Lasso, c'est une constante qui multiplie les termes L1/L2.

Et, contrairement à Lasso, MultiTaskLasso n'a pas d'attribut de précalcul.

## Exemple d'implémentation

Le script Python suivant utilise le modèle linéaire MultiTaskLasso qui utilise ensuite la descente de coordonnées comme algorithme pour ajuster les coefficients.

```python
from sklearn import linear_model
MTLReg = linear_model.MultiTaskLasso(alpha=0.5)
MTLReg.fit([[0,0], [1, 1], [2, 2]], [[0, 0],[1,1],[2,2]])
```

## Sortie

```python
MultiTaskLasso(alpha = 0.5, copy_X = True, fit_intercept = True, max_iter = 1000,
    normalize = False, random_state = None, selection = 'cyclic', tol = 0.0001,
    warm_start = False)
```

## Exemple

Maintenant, une fois ajusté, le modèle peut prédire de nouvelles valeurs comme suit :

```python
MTLReg.predict([[0,1]])
```

## Sortie

```python
array([[0.53033009, 0.53033009]])
```

## Exemple

Pour l'exemple ci-dessus, nous pouvons obtenir le vecteur de poids à l'aide du script python suivant :

```python
MTLReg.coef_
```

## Sortie

```python
array([[0.46966991, 0. ],
[0.46966991, 0. ]])
```

## Exemple

De même, nous pouvons obtenir la valeur d'intercept à l'aide du script python suivant :

```python
MTLReg.intercept_
```

## Sortie

```python
array([0.53033009, 0.53033009])
```

## Exemple

Nous pouvons obtenir le nombre total d'itérations pour obtenir la tolérance spécifiée à l'aide du script python suivant :

```python
MTLReg.n_iter_
```

## Sortie

```python
2
```

Nous pouvons modifier les valeurs des paramètres pour obtenir la sortie souhaitée du modèle.