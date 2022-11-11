La régression logistique, malgré son nom, est un algorithme de classification plutôt qu'un algorithme de régression. Sur la base d'un ensemble donné de variables indépendantes, elle est utilisée pour estimer une valeur discrète (0 ou 1, oui/non, vrai/faux). Il est également appelé logit ou MaxEnt Classifier.

Fondamentalement, il mesure la relation entre la variable dépendante catégorielle et une ou plusieurs variables indépendantes en estimant la probabilité d'occurrence d'un événement à l'aide de sa fonction logistique.

```sklearn.linear_model.LogisticRegression``` est le module utilisé pour implémenter la régression logistique.

## Paramètres

La liste suivante montre les paramètres utilisés par le module Régression logistique :

- **penalty** - str, 'L1', 'L2', 'elasticnet' ou aucun, facultatif, par défaut = 'L2'. Ce paramètre est utilisé pour spécifier la norme (L1 ou L2) utilisée dans la pénalisation (régularisation).
- **dual** - Booléen, facultatif, par défaut = False. Il est utilisé pour la formulation duale ou primale, tandis que la formulation duale n'est mise en œuvre que pour la pénalisation L2.
- **tol** - flottant, facultatif, par défaut = 1e-4. Il représente la tolérance pour les critères d'arrêt.
- **C** - flottant, facultatif, par défaut=1.0. Il représente l'inverse de la force de régularisation, qui doit toujours être un flottant positif.
- **fit_intercept** - booléen, facultatif, par défaut = True. Ce paramètre indique qu'une constante (biais ou intercept) doit être ajoutée à la fonction de décision.
- **intercept_scaling** - float, optional, default = 1. Ce paramètre est utile lorsque : 
    - le solveur 'liblinear' est utilisé
    - fit_intercept est défini à true
- **class_weight** - dict ou 'balanced' facultatif, par défaut = none. Il représente les poids associés aux classes. Si nous utilisons l'option par défaut, cela signifie que toutes les classes sont supposées avoir un poids de 1. Par contre, si vous choisissez class_weight : balanced, il utilisera les valeurs de y pour ajuster automatiquement les poids.
- **random_state** - int, RandomState instance ou None, optionnel, par défaut = none. Ce paramètre représente la graine du nombre pseudo-aléatoire généré qui est utilisé lors du brassage des données. Les options suivantes sont disponibles :
    - **int** - dans ce cas, random_state est la graine utilisée par le générateur de nombres aléatoires.
    - **RandomState instance** - dans ce cas, random_state est le générateur de nombres aléatoires.
    - **None** - dans ce cas, le générateur de nombres aléatoires est l'instance RandonState utilisée par np.random.
- **solver** - str, {'newton-cg', 'lbfgs', 'liblinear', 'saag', 'saga'}, optionnel, par défaut = 'liblinear'. Ce paramètre représente l'algorithme à utiliser pour le problème d'optimisation. Les propriétés des options de ce paramètre sont les suivantes : 
    - **liblinear** - C'est un bon choix pour les petits ensembles de données. Il gère également la pénalité L1. Pour les problèmes multi-classes, il est limité aux schémas un-contre-un.
    - **newton-cg** - Il gère uniquement la pénalité L2.
    - **lbfgs** - Pour les problèmes multiclasses, il gère la perte multinomiale. Il ne traite également que la pénalité L2.
    - **saga** - C'est un bon choix pour les grands ensembles de données. Pour les problèmes multiclasses, il gère également la perte multinomiale. Outre la pénalité L1, il prend également en charge la pénalité 'elasticnet'.
    - **sag** - Il est également utilisé pour les grands ensembles de données. Pour les problèmes multiclasses, il gère également la perte multinomiale.
- **max_iter** - int, optionnel, par défaut = 100. Comme son nom l'indique, il représente le nombre maximum d'itérations nécessaires pour que les solveurs convergent.
- **multi_class** - str, {'ovr', 'multinomial', 'auto'}, optionnel, par défaut = 'ovr'.
    - **ovr** - Pour cette option, un problème binaire est ajusté pour chaque étiquette.
    - **multimonial** - Pour cette option, la perte minimisée est la perte multinomiale ajustée sur toute la distribution de probabilité. Nous ne pouvons pas utiliser cette option si le solveur = 'liblinear'.
    - **auto** - Cette option sélectionnera 'ovr' si le solveur = 'liblinear' ou si les données sont binaires, sinon elle choisira 'multinomial'.
- **verbose** - int, facultatif, par défaut = 0. Par défaut, la valeur de ce paramètre est 0, mais pour les solveurs liblinear et lbfgs, nous devons définir verbose à tout nombre positif.
- **warm_start** - bool, optional, default = false. Avec ce paramètre réglé sur True, nous pouvons réutiliser la solution de l'appel précédent à fit comme initialisation. Si nous choisissons la valeur par défaut, c'est-à-dire false, cela effacera la solution précédente.
- **n_jobs** - int ou None, facultatif, par défaut = None. Si multi_class = 'ovr', ce paramètre représente le nombre de cœurs de CPU utilisés lors de la parallélisation sur les classes. Il est ignoré lorsque le solveur = 'liblinear'.
- **l1_ratio** - float ou None, optionnel, default = None. Il est utilisé dans le cas où la pénalité = 'elasticnet'. C'est essentiellement le paramètre de mélange Elastic-Net avec 0 < = l1_ratio > = 1.

## Attributs

La liste suivante présente les attributs utilisés par le module de régression logistique :

- **coef_** - tableau, shape(n_features,) ou (n_classes, n_features). Il est utilisé pour estimer les coefficients des caractéristiques dans la fonction de décision. Lorsque le problème donné est binaire, il est de la forme (1, n_caractéristiques).
- **Intercept_** - tableau, forme(1) ou (n_classes). Il représente la constante, également appelée biais, ajoutée à la fonction de décision.
- **classes_** - tableau, forme(n_classes). Il fournit une liste d'étiquettes de classe connues par le classificateur.
- **n_iter_** - tableau, forme (n_classes) ou (1). Il renvoie le nombre réel d'itérations pour toutes les classes.

## Exemple de mise en œuvre

Le script Python suivant fournit un exemple simple d'implémentation de la régression logistique sur le jeu de données de l'iris de scikit-learn.

```python
from sklearn import datasets
from sklearn import linear_model
from sklearn.datasets import load_iris
X, y = load_iris(return_X_y = True)
LRG = linear_model.LogisticRegression(
    random_state = 0,solver = 'liblinear',multi class = 'auto'
)
.fit(X, y)
LRG.score(X, y)
```

## Sortie

```python
0.96
```

Le résultat montre que le modèle de régression logistique ci-dessus a donné une précision de 96 %.