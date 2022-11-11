C'est l'un des meilleurs modèles statistiques qui étudie la relation entre une variable dépendante (Y) et un ensemble donné de variables indépendantes (X). La relation peut être établie à l'aide de l'ajustement d'une meilleure ligne.

```sklearn.linear_model.LinearRegression``` est le module utilisé pour implémenter la régression linéaire.

## Paramètres

la liste suivante présente les paramètres utilisés par le module de régression linéaire :

- **fit_intercept** - Booléen, facultatif, par défaut True : Utilisé pour calculer l'intercept du modèle. Aucune ordonnée à l'origine ne sera utilisée dans le calcul si cette option est définie sur false.
- **normalize** - Booléen, facultatif, par défaut False : Si ce paramètre est défini sur True, le régresseur X sera normalisé avant la régression. La normalisation sera effectuée en soustrayant la moyenne et en la divisant par la norme L2. Si fit_intercept = False, ce paramètre sera ignoré.
- **copy_X** - Booléen, facultatif, par défaut True : Par défaut, il est vrai, ce qui signifie que X sera copié. Mais s'il est défini à false, X peut être écrasé.
- **n_jobs** - int ou None, facultatif(default = None) : Il représente le nombre de jobs à utiliser pour le calcul.

## Attributs

La liste suivante présente les attributs utilisés par le module de régression linéaire :

- **coef_** - tableau, shape(n_features,) ou (n_targets, n_features) : Il est utilisé pour estimer les coefficients pour le problème de régression linéaire. Il s'agit d'un tableau 2D de forme (n_targets, n_features) si des cibles multiples sont transmises pendant l'ajustement. Ex. (y 2D). D'autre part, il s'agirait d'un tableau 1D de longueur (n_caractéristiques) si une seule cible est passée pendant l'ajustement.
- **Intercept_** - tableau : Il s'agit d'un terme indépendant dans ce modèle linéaire.

### Exemple

Tout d'abord, importez les paquets nécessaires.

```python
import numpy as np
from sklearn.linear_model import LinearRegression
```

Maintenant, fournissez les valeurs de la variable indépendante X.

```python
X = np.array([[1,1],[1,2],[2,2],[2,3]])
```

Ensuite, la valeur de la variable dépendante y peut être calculée de la manière suivante.

```python
y = np.dot(X, np.array([1,2])) + 3
```

Maintenant, créez un objet de régression linéaire comme suit.

```python
regr = LinearRegression(
    fit_intercept = True, normalize = True, copy_X = True, n_jobs = 2
)
.fit(X,y)
```

Utilisez la méthode ```predict()``` pour prédire en utilisant ce modèle linéaire comme suit :

```python
regr.predict(np.array([[3,5]]))
```

### Sortie

```python
array([16.])
```

### Exemple

Pour obtenir le coefficient de détermination de la prédiction, nous pouvons utiliser la méthode ```Score()``` comme suit :

```python
regr.score(X,y)
```

### Sortie

```python
1.0
```

### Exemple

Nous pouvons estimer les coefficients en utilisant l'attribut nommé 'coef' comme suit :

```python
regr.coef_
```

### Sortie

```python
tableau([1., 2.])
```

### Exemple

Nous pouvons calculer l'ordonnée à l'origine, c'est-à-dire la valeur moyenne attendue de Y lorsque tous les X = 0, en utilisant l'attribut nommé 'intercept', comme suit :

```python
In [24]: regr.intercept_
```

### Sortie

```python
3.0000000000000018
```

## Code complet de l'exemple de mise en œuvre

```python
import numpy as np
from sklearn.linear_model import LinearRegression
X = np.array([[1,1],[1,2],[2,2],[2,3]])
y = np.dot(X, np.array([1,2])) + 3
regr = LinearRegression(
    fit_intercept = True, normalize = True, copy_X = True, n_jobs = 2
).fit(X,y)
regr.predict(np.array([[3,5]]))
regr.score(X,y)
regr.coef_
regr.intercept_
```