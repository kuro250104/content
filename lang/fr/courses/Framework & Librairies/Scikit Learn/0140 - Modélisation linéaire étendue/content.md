## Introduction aux caractéristiques polynomiales

Les modèles linéaires entraînés sur des fonctions non linéaires de données conservent généralement les performances rapides des méthodes linéaires. Cela leur permet également de s'adapter à un éventail de données beaucoup plus large. C'est la raison pour laquelle les modèles linéaires formés sur des fonctions non linéaires sont utilisés dans l'apprentissage automatique.

Par exemple, une régression linéaire simple peut être étendue en construisant des caractéristiques polynomiales à partir des coefficients.

Mathématiquement, supposons que nous ayons un modèle de régression linéaire standard, alors, pour des données bidimensionnelles, il ressemblerait à ceci :

![modèle de régression linéaire standard pour des données bidimensionnelles](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0140%20-%20Mod%C3%A9lisation%20lin%C3%A9aire%20%C3%A9tendue/images/image2.png)

Maintenant, nous pouvons combiner les caractéristiques dans des polynômes du second ordre et notre modèle ressemblera à ce qui suit :

![combinaison les caractéristiques dans des polynômes du second ordre](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Scikit%20Learn/0140%20-%20Mod%C3%A9lisation%20lin%C3%A9aire%20%C3%A9tendue/images/image1.png)

Le modèle ci-dessus est toujours un modèle linéaire. Ici, nous avons vu que la régression polynomiale résultante est dans la même classe de modèles linéaires et peut être résolue de manière similaire.

Pour ce faire, scikit-learn fournit un module nommé **PolynomialFeatures**. Ce module transforme une matrice de données d'entrée en une nouvelle matrice de données de degré donné.

## Paramètres

La liste suivante présente les paramètres utilisés par le module **PolynomialFeatures** :

- **degree** - nombre entier, par défaut = 2. Il représente le degré des caractéristiques polynomiales.
- **interaction_only** - booléen, par défaut = false. Par défaut, il est faux mais s'il est défini comme vrai, les caractéristiques qui sont des produits de caractéristiques d'entrée distinctes au degré le plus élevé, sont produites. Ces caractéristiques sont appelées caractéristiques d'interaction.
- **include_bias** - Booléen, par défaut = true. Il inclut une colonne de biais, c'est-à-dire la caractéristique dans laquelle toutes les puissances des polynômes sont nulles.
- **order** - str dans {'C', 'F'}, par défaut = 'C'. Ce paramètre représente l'ordre du tableau de sortie dans le cas dense. L'ordre 'F' est plus rapide à calculer, mais d'un autre côté, il peut ralentir les estimateurs suivants.

## Attributs

Le tableau suivant présente les attributs utilisés par le module **PolynomialFeatures** :

- **powers_** - tableau, forme (n_output_features, n_input_features). Il montre que powers_ [i,j] est l'exposant de la jème entrée dans la ème sortie.
- **n_input_features_** - int. Comme son nom l'indique, elle donne le nombre total de caractéristiques d'entrée.
- **n_output_features_** - int. Comme son nom l'indique, il donne le nombre total de caractéristiques polynomiales en sortie.

## Exemple

Le script Python suivant utilise le transformateur PolynomialFeatures pour transformer un tableau de 8 en forme (4,2).

```python
from sklearn.preprocessing import PolynomialFeatures
import numpy as np
Y = np.arange(8).reshape(4, 2)
poly = PolynomialFeatures(degree=2)
poly.fit_transform(Y)
```

## Sortie

```python
array(
    [
        [ 1., 0., 1., 0., 0., 1.],
        [ 1., 2., 3., 4., 6., 9.],
        [ 1., 4., 5., 16., 20., 25.],
        [ 1., 6., 7., 36., 42., 49.]
    ]
)
```

## Rationalisation à l'aide des outils Pipeline

Le type de prétraitement ci-dessus, c'est-à-dire la transformation d'une matrice de données d'entrée en une nouvelle matrice de données d'un degré donné, peut être rationalisé à l'aide des outils Pipeline, qui sont essentiellement utilisés pour enchaîner plusieurs estimateurs en un seul.

### Exemple

Les scripts python ci-dessous utilisent les outils Pipeline de Scikit-learn pour rationaliser le prétraitement (s'adaptera à des données polynomiales d'ordre 3).

```python
#First, import the necessary packages.
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression
from sklearn.pipeline import Pipeline
import numpy as np

#Next, create an object of Pipeline tool
Stream_model = Pipeline([('poly', PolynomialFeatures(degree=3)), ('linear', LinearRegression(fit_intercept=False))])

#Provide the size of array and order of polynomial data to fit the model.
x = np.arange(5)
y = 3 - 2 * x + x ** 2 - x ** 3
Stream_model = model.fit(x[:, np.newaxis], y)

#Calculate the input polynomial coefficients.
Stream_model.named_steps['linear'].coef_
```

### Sortie

```python
array([ 3., -2., 1., -1.])
```

La sortie ci-dessus montre que le modèle linéaire formé sur les caractéristiques polynomiales est capable de récupérer les coefficients polynomiaux d'entrée exacts.