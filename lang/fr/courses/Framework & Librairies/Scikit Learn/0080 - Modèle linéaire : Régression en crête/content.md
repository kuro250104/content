La régression en crête ou régularisation de Tikhonov est la technique de régularisation qui effectue une régularisation L2. Elle modifie la fonction de perte en ajoutant la pénalité (quantité de rétrécissement) équivalente au carré de la magnitude des coefficients.

![Formule mathématique de la régression en crête](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0080%20-%20Mod%C3%A8le%20lin%C3%A9aire%20%3A%20R%C3%A9gression%20en%20cr%C3%AAte/images/image1.png)

```sklearn.linear_model.Ridge``` est le module utilisé pour résoudre un modèle de régression où la fonction de perte est la fonction linéaire des moindres carrés et la régularisation est L2.

## Paramètres

La liste suivante présente les paramètres utilisés par le module Ridge :

- **alpha** - {float, array-like}, shape(n_targets). Alpha est le paramètre d'ajustement qui détermine dans quelle mesure nous voulons pénaliser le modèle.
- **fit_intercept** - Booléen. Ce paramètre spécifie si une constante (biais ou intercept) doit être ajoutée à la fonction de décision. Aucun intercept ne sera utilisé dans le calcul, s'il est défini à false.
- **tol** - float, facultatif, default=1e-4. Il représente la précision de la solution.
- **normalize** - booléen, facultatif, valeur par défaut = False. Si ce paramètre est défini sur True, le régresseur X sera normalisé avant la régression. La normalisation sera effectuée en soustrayant la moyenne et en la divisant par la norme L2. Si fit_intercept = False, ce paramètre sera ignoré.
- **copy_X** - Booléen, facultatif, par défaut = True. Par défaut, il est vrai, ce qui signifie que X sera copié. Mais s'il est défini à false, X peut être écrasé.
- **max_iter** - int, facultatif. Comme son nom l'indique, il représente le nombre maximum d'itérations prises pour les solveurs de gradient conjugué.
- **solver** - str, {'auto', 'svd', 'cholesky', 'lsqr', 'sparse_cg', 'sag', 'saga'}. Ce paramètre indique le solveur à utiliser dans les routines de calcul. Les propriétés des options de ce paramètre sont les suivantes :
    - **auto** - Il permet de choisir automatiquement le solveur en fonction du type de données.
    - **svd** - Afin de calculer les coefficients de Ridge, ce paramètre utilise une décomposition en valeurs singulières de X.
    - **cholesky** - Ce paramètre utilise la fonction standard scipy.linalg.solve() pour obtenir une solution à forme fermée.
    - **lsqr** - Ce paramètre est le plus rapide et utilise la routine de moindres carrés régularisés dédiée scipy.sparse.linalg.lsqr.
    - **sag** - Elle utilise un processus itératif et une descente de gradient moyenne stochastique.
    - **saga** - Il utilise également un processus itératif et une descente de gradient moyenne stochastique améliorée.
- **random_state** - int, RandomState instance ou None, facultatif, par défaut = none. Ce paramètre représente la graine du nombre pseudo-aléatoire généré qui est utilisé lors du brassage des données. Les options suivantes sont disponibles :
    - **int** - Dans ce cas, random_state est la graine utilisée par le générateur de nombres aléatoires.
    - **RandomState instance** - Dans ce cas, random_state est le générateur de nombres aléatoires.
    - **None** - Dans ce cas, le générateur de nombres aléatoires est l'instance RandonState utilisée par np.random.

## Attributs

La liste suivante présente les attributs utilisés par le module Ridge :

- **coef_** - tableau, shape(n_features,) ou (n_target, n_features). Cet attribut fournit les vecteurs de poids.
- **Intercept_** - float | tableau, shape = (n_targets). Il représente le terme indépendant dans la fonction de décision.
- **n_iter_** - tableau ou None, forme (n_targets). Disponible uniquement pour les solveurs 'sag' et 'lsqr', renvoie le nombre réel d'itérations pour chaque cible.

## Exemple d'implémentation

Le script Python suivant fournit un exemple simple de mise en œuvre de la régression de Ridge. Nous utilisons 15 échantillons et 10 caractéristiques. La valeur de alpha est de 0.5 dans notre cas. Deux méthodes, fit() et score(), sont utilisées respectivement pour ajuster ce modèle et calculer le score.

```python
from sklearn.linear_model import Ridge
import numpy as np
n_samples, n_features = 15, 10
rng = np.random.RandomState(0)
y = rng.randn(n_samples)
X = rng.randn(n_samples, n_features)
rdg = Ridge(alpha = 0.5)
rdg.fit(X, y)
rdg.score(X,y)
```

## Sortie

```python
0.76294987
```

La sortie montre que le modèle de régression de crête ci-dessus a donné un score d'environ 76 %. Pour plus de précision, nous pouvons augmenter le nombre d'échantillons et de caractéristiques.

## Exemple

Dans l'exemple ci-dessus, nous pouvons obtenir le vecteur de poids à l'aide du script python suivant

```python
rdg.coef_
```

## Sortie

```python
array([ 0.32720254, -0.34503436, -0.2913278 , 0.2693125 , -0.22832508,
    -0.8635094 , -0.17079403, -0.36288055, -0.17241081, -0.43136046])
```

## Exemple

De même, nous pouvons obtenir la valeur d'intercept à l'aide du script python suivant :

```python
rdg.intercept_
```

## Sortie

```python
0.527486
```