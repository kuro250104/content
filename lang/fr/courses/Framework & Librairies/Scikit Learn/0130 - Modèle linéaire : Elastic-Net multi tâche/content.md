Il s'agit d'un modèle Elastic-Net qui permet d'ajuster conjointement des problèmes de régression multiple en imposant que les caractéristiques sélectionnées soient les mêmes pour tous les problèmes de régression, également appelés tâches. Sklearn fournit un modèle linéaire nommé MultiTaskElasticNet, entraîné avec un mélange de L1, L2-norm et L2 pour la régularisation, qui estime les coefficients épars pour les problèmes de régression multiple conjointement. Dans ce modèle, la réponse y est un tableau 2D de forme (n_échantillons, n_tâches).

La fonction objective à minimiser est la suivante : 

![fonction objective à minimiser](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0130%20-%20Mod%C3%A8le%20lin%C3%A9aire%20%3A%20Elastic-Net%20multi%20t%C3%A2che/images/image1.png)

Comme dans MultiTaskLasso, ici aussi, Fro indique la norme de Frobenius :

![norme de Frobenius](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0130%20-%20Mod%C3%A8le%20lin%C3%A9aire%20%3A%20Elastic-Net%20multi%20t%C3%A2che/images/image2.png)

Et L1L2 conduit à ce qui suit :

![L1L2](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0130%20-%20Mod%C3%A8le%20lin%C3%A9aire%20%3A%20Elastic-Net%20multi%20t%C3%A2che/images/image3.png)

Les paramètres et les attributs de MultiTaskElasticNet sont identiques à ceux d'ElasticNet. La seule différence réside dans li_ratio, c'est-à-dire le paramètre de mélange d'ElasticNet. Dans MultiTaskElasticNet, sa plage est 0 < l1_ratio < = 1. Si l1_ratio = 1, la pénalité serait la pénalité L1/L2. Si l1_ratio = 0, la pénalité serait une pénalité L2. Si la valeur de l1_ratio est comprise entre 0 et 1, la pénalité serait la combinaison de L1/L2 et L2.

Et, contrairement à ElasticNet, MultiTaskElasticNet n'a pas d'attribut de précalcul.

## Exemple d'implémentation

Pour montrer la différence, nous implémentons le même exemple que dans Multi-task Lasso.

```python
from sklearn import linear_model
MTENReg = linear_model.MultiTaskElasticNet(alpha = 0.5)
MTENReg.fit([[0,0], [1, 1], [2, 2]], [[0, 0],[1,1],[2,2]])
```

## Sortie

```python
MultiTaskElasticNet(alpha = 0.5, copy_X = True, fit_intercept = True, l1_ratio = 0.5,
max_iter = 1000, normalize = False, random_state = None,
selection = 'cyclic', tol = 0.0001, warm_start = False)
```

## Exemple

```python
#Predicting new values
MTENReg.predict([[1,0]])
```

## Sortie

```python
array([[0.69056563, 0.69056563]])
```

## Exemple

```python
#weight vectors
MTENReg.coef_
```

## Sortie

```python
array([[0.30943437, 0.30938224],
[0.30943437, 0.30938224]])
```

## Exemple

```python
#Calculating intercept
MTENReg.intercept_
```

## Sortie

```python
array([0.38118338, 0.38118338])
```

## Exemple

```python
#Calculating number of iterations
MTENReg.n_iter_
```

## Sortie

```python
15
```