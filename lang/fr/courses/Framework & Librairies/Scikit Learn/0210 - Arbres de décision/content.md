## Introduction

Dans ce chapitre, nous allons apprendre la méthode d'apprentissage dans Sklearn qui est appelée arbres de décision.

Les arbres de décision (DT) sont la méthode d'apprentissage supervisé non paramétrique la plus puissante. Elles peuvent être utilisées pour les tâches de classification et de régression. L'objectif principal des arbres de décision est de créer un modèle prédisant la valeur de la variable cible en apprenant des règles de décision simples déduites des caractéristiques des données. Les arbres de décision ont deux entités principales : le nœud racine, où les données sont divisées, et les nœuds de décision ou feuilles, où l'on obtient la sortie finale.

## Decision Tree Algorithms

Les différents algorithmes d'arbre de décision sont expliqués ci-dessous -

### ID3

Il a été développé par Ross Quinlan en 1986. Il est également appelé Iterative Dichotomiser 3. L'objectif principal de cet algorithme est de trouver les caractéristiques catégorielles, pour chaque nœud, qui apporteront le plus grand gain d'information pour les cibles catégorielles. Il permet à l'arbre de croître jusqu'à sa taille maximale puis, pour améliorer la capacité de l'arbre sur des données non vues, il applique une étape d'élagage. Le résultat de cet algorithme est un arbre à plusieurs voies.

### C4.5

Il succède à ID3 et définit dynamiquement un attribut discret qui partitionne la valeur de l'attribut continu en un ensemble discret d'intervalles. C'est la raison pour laquelle il a supprimé la restriction des caractéristiques catégorielles. Il convertit l'arbre formé par ID3 en ensembles de règles "SI-ALORS".
Afin de déterminer l'ordre dans lequel ces règles doivent être appliquées, la précision de chaque règle sera d'abord évaluée.

### C5.0

Il fonctionne de la même manière que le C4.5 mais il utilise moins de mémoire et construit des jeux de règles plus petits. Il est plus précis que le C4.5.

### CART

Il s'agit de l'algorithme des arbres de classification et de régression. Il génère essentiellement des divisions binaires en utilisant les caractéristiques et le seuil donnant le plus grand gain d'information à chaque nœud (appelé indice de Gini). L'homogénéité dépend de l'indice de Gini, plus la valeur de l'indice de Gini est élevée, plus l'homogénéité est grande. Il ressemble à l'algorithme C4.5, mais à la différence qu'il ne calcule pas les ensembles de règles et ne prend pas en charge les variables cibles numériques (régression).

## Classification with decision trees

Dans ce cas, les variables de décision sont catégoriques.

**Sklearn Module** - La bibliothèque Scikit-learn fournit le module DecisionTreeClassifier pour effectuer une classification multiclasse sur un ensemble de données.

### Parameters

Le tableau suivant présente les paramètres utilisés par le module sklearn.tree.DecisionTreeClassifier.

**Paramètre et description**

- **criterion** − string, optional default= “gini” - Il représente la fonction permettant de mesurer la qualité d'un fractionnement. Les critères supportés sont "gini" et "entropie". La valeur par défaut est gini qui correspond à l'impureté de Gini tandis que l'entropie correspond au gain d'information.
- **splitter** − string, optional default= “best” - Il indique au modèle la stratégie "meilleure" ou "aléatoire" pour choisir le fractionnement à chaque nœud.
- **max_depth** − int or None, optional default=None - Ce paramètre détermine la profondeur maximale de l'arbre. La valeur par défaut est None, ce qui signifie que les noeuds se développeront jusqu'à ce que toutes les feuilles soient pures ou jusqu'à ce que toutes les feuilles contiennent moins de min_smaples_split échantillons.
- **min_samples_split** − int, float, optional default=2 - Ce paramètre fournit le nombre minimum d'échantillons requis pour diviser un nœud interne.
- **min_samples_leaf** − int, float, optional default=1 - Ce paramètre fournit le nombre minimum d'échantillons requis pour être à un noeud feuille.
- **min_weight_fraction_leaf** − float, optional default=0. - Avec ce paramètre, le modèle obtiendra la fraction pondérée minimale de la somme des poids requise pour être à un nœud feuille.
- **max_features** − int, float, string or None, optional default=None - Il donne au modèle le nombre de caractéristiques à prendre en compte lors de la recherche de la meilleure répartition.
- **random_state** − int, RandomState instance or None, optional, default = none - Ce paramètre représente la graine du nombre pseudo-aléatoire généré qui est utilisé lors du brassage des données. Les options suivantes sont disponibles
    - **int** − Dans ce cas, random_state est la graine utilisée par le générateur de nombres aléatoires.
    - **RandomState instance** − Dans ce cas, random_state est le générateur de nombres aléatoires.
    - **None** − Dans ce cas, le générateur de nombres aléatoires est l'instance RandonState utilisée par np.random.
- **max_leaf_nodes** − int or None, optional default=None - Ce paramètre permet de faire croître un arbre avec max_leaf_nodes de la manière la plus efficace possible. La valeur par défaut est none, ce qui signifie qu'il y aura un nombre illimité de nœuds de feuilles.
- **min_impurity_decrease** − float, optional default=0. - Cette valeur fonctionne comme un critère pour le fractionnement d'un nœud car le modèle fractionnera un nœud si ce fractionnement induit une diminution de l'impureté supérieure ou égale à la valeur min_impurity_decrease.
- **min_impurity_split** − float, default=1e-7 - Il représente le seuil d'arrêt précoce de la croissance des arbres.
- **class_weight** − dict, list of dicts, “balanced” or None, default=None - Il représente les poids associés aux classes. La forme est {class_label : weight}. Si nous utilisons l'option par défaut, cela signifie que toutes les classes sont censées avoir un poids de un. Par contre, si vous choisissez class_weight : balanced, il utilisera les valeurs de y pour ajuster automatiquement les poids.
- **presort** − bool, optional default=False - Il indique au modèle s'il doit trier les données au préalable afin d'accélérer la recherche des meilleures répartitions dans l'ajustement. La valeur par défaut est false, mais si elle est réglée sur true, elle peut ralentir le processus d'apprentissage.

### Attributs

Le tableau suivant présente les attributs utilisés par le module sklearn.tree.DecisionTreeClassifier.

**Paramètre et description**

- **feature_importances_** − array of shape =[n_features] - Cet attribut renvoie l'importance de la caractéristique.
- **classes_** − array of shape = [n_classes] or a list of such arrays - Il représente les étiquettes de classes, c'est-à-dire le problème à sortie unique, ou une liste de tableaux d'étiquettes de classes, c'est-à-dire le problème à sorties multiples.
- **max_features_** − int - Il représente la valeur déduite du paramètre max_features.
- **n_classes_** − int or list - Il représente le nombre de classes, c'est-à-dire le problème à sortie unique, ou une liste du nombre de classes pour chaque sortie, c'est-à-dire le problème à sorties multiples.
- **n_features_** − int - Il donne le nombre de caractéristiques lorsque la méthode fit() est exécutée.
- **n_outputs_** − int - Il donne le nombre de sorties lorsque la méthode fit() est exécutée.

### Méthodes

Le tableau suivant présente les méthodes utilisées par le module sklearn.tree.DecisionTreeClassifier.

**Paramètre et description**

- **apply(self, X[, check_input])** - Cette méthode renvoie l'index de la feuille.
- **decision_path(self, X[, check_input])** - Comme son nom l'indique, cette méthode renvoie le chemin de décision dans l'arbre.
- **fit(self, X, y[, sample_weight, …])** - La méthode fit() construit un classificateur à arbre de décision à partir d'un ensemble d'apprentissage donné (X, y).
- **get_depth(self)** - Comme son nom l'indique, cette méthode renvoie la profondeur de l'arbre de décision.
- **get_n_leaves(self)** - Comme son nom l'indique, cette méthode renvoie le nombre de feuilles de l'arbre de décision.
- **get_params(self[, deep])** - Nous pouvons utiliser cette méthode pour obtenir les paramètres de l'estimateur.
- **predict(self, X[, check_input])** - Il prédit la valeur de la classe pour X.
- **predict_log_proba(self, X)** - Il prédit les log-probabilités de classe des échantillons d'entrée fournis par nous, X.
- **predict_proba(self, X[, check_input])** - Il va prédire les probabilités de classe des échantillons d'entrée fournis par nous, X.
- **score(self, X, y[, sample_weight])** - Comme son nom l'indique, la méthode score() renvoie la précision moyenne sur les données de test données et les étiquettes...
- **set_params(self, \*\*params)** - Nous pouvons définir les paramètres de l'estimateur avec cette méthode.

### Implementation Example

Le script Python ci-dessous utilisera le module sklearn.tree.DecisionTreeClassifier pour construire un classificateur permettant de prédire s'il s'agit d'un homme ou d'une femme à partir de notre ensemble de données comprenant 25 échantillons et deux caractéristiques, à savoir la "taille" et la "longueur des cheveux".

```python
from sklearn import tree
from sklearn.model_selection import train_test_split
X=[[165,19],[175,32],[136,35],[174,65],[141,28],[176,15]
,[131,32],[166,6],[128,32],[179,10],[136,34],[186,2],[12
6,25],[176,28],[112,38],[169,9],[171,36],[116,25],[196,2
5], [196,38], [126,40], [197,20], [150,25], [140,32],[136,35]]
Y=['Man','Woman','Woman','Man','Woman','Man','Woman','Ma
n','Woman','Man','Woman','Man','Woman','Woman','Woman','
Man','Woman','Woman','Man', 'Woman', 'Woman', 'Man', 'Man', 'Woman', 'Woman']
data_feature_names = ['height','length of hair']
X_train, X_test, y_train, y_test = train_test_split(X, Y, test_size = 0.3, random_state = 1)
DTclf = tree.DecisionTreeClassifier()
DTclf = clf.fit(X,Y)
prediction = DTclf.predict([[135,29]])
print(prediction)
```

### Sortie

```python
['Woman']
```

Nous pouvons également prédire la probabilité de chaque classe en utilisant la méthode python predict_proba() suivante -

### Exemple

```python
prediction = DTclf.predict_proba([[135,29]])
print(prediction)
```

### Sortie

```python
[[0. 1.]]
```

## Régression avec arbres de décision

Dans ce cas, les variables de décision sont continues.

**Sklearn Module** - La bibliothèque Scikit-learn fournit le nom de module DecisionTreeRegressor pour l'application des arbres de décision aux problèmes de régression.

### Paramètres

Les paramètres utilisés par DecisionTreeRegressor sont presque les mêmes que ceux utilisés dans le module DecisionTreeClassifier. La différence réside dans le paramètre 'criterion'. Pour les modules DecisionTreeRegressor, le paramètre 'criterion : string, optional default="mse"' a les valeurs suivantes -

- **mse** − Il s'agit de l'erreur quadratique moyenne. Elle est égale à la réduction de la variance comme critère de sélection des caractéristiques. Il minimise la perte L2 en utilisant la moyenne de chaque nœud terminal.
- **freidman_mse** − Elle utilise également l'erreur quadratique moyenne mais avec le score d'amélioration de Friedman.
- **mae** − Il s'agit de l'erreur absolue moyenne. Elle minimise la perte L1 en utilisant la médiane de chaque nœud terminal.

Une autre différence est qu'il n'a pas de paramètre "class_weight".

### Attributs

Les attributs du module DecisionTreeRegressor sont également les mêmes que ceux du module DecisionTreeClassifier. La différence est qu'il ne possède pas les attributs 'classes_' et 'n_classes_'.

### Méthodes

Les méthodes du module DecisionTreeRegressor sont également les mêmes que celles du module DecisionTreeClassifier. La différence est qu'il ne possède pas les attributs ```predict_log_proba()``` et ```predict_proba()```.

#### Exemple de mise en œuvre

La méthode ```fit()``` dans le modèle de régression de l'arbre de décision prendra les valeurs à virgule flottante de y. Voyons un exemple de mise en œuvre simple en utilisant Sklearn.tree.DecisionTreeRegressor -.

```python
from sklearn import tree
X = [[1, 1], [5, 5]]
y = [0.1, 1.5]
DTreg = tree.DecisionTreeRegressor()
DTreg = clf.fit(X, y)
```

Une fois ajusté, nous pouvons utiliser ce modèle de régression pour faire des prédictions comme suit -

```python
DTreg.predict([[4, 5]])
```

#### Sortie

```python
array([1.5])
```