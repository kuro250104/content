Comme nous le savons, l'apprentissage automatique consiste à créer un modèle à partir de données. Pour ce faire, l'ordinateur doit d'abord comprendre les données. Ensuite, nous allons discuter des différentes façons de représenter les données afin qu'elles soient comprises par l'ordinateur.

## Données sous forme de tableau

La meilleure façon de représenter les données dans Scikit-learn est sous forme de tableaux. Un tableau représente une grille bidimensionnelle de données où les lignes représentent les éléments individuels de l'ensemble de données et les colonnes représentent les quantités liées à ces éléments individuels.

### Exemple

Avec l'exemple donné ci-dessous, nous pouvons télécharger un ensemble de données sur l'iris sous la forme d'un DataFrame Pandas à l'aide de la bibliothèque python seaborn.

```python
import seaborn as sns
iris = sns.load_dataset('iris')
iris.head()
```

### Rendu

```bash
sepal_length sepal_width petal_length petal_width  species
0        5.1      3.5         1.4             0.2   setosa
1        4.9      3.0         1.4             0.2   setosa
2        4.7      3.2         1.3             0.2   setosa
3        4.6      3.1         1.5             0.2   setosa
4        5.0      3.6         1.4             0.2   setosa
```

À partir de la sortie ci-dessus, nous pouvons voir que chaque ligne des données représente une seule fleur observée et que le nombre de lignes représente le nombre total de fleurs dans l'ensemble de données. En général, nous appelons les lignes de la matrice des échantillons.

D'autre part, chaque colonne des données représente une information quantitative décrivant chaque échantillon. En général, nous appelons les colonnes de la matrice des caractéristiques.

## Données en tant que matrice de caractéristiques

La matrice des caractéristiques peut être définie comme la mise en page d'un tableau où les informations peuvent être considérées comme une matrice bidimensionnelle. Elle est stockée dans une variable nommée X et supposée être bidimensionnelle avec la forme [n_samples, n_features]. La plupart du temps, elle est contenue dans un tableau NumPy ou un DataFrame Pandas. Comme indiqué précédemment, les échantillons représentent toujours les objets individuels décrits par l'ensemble de données et les caractéristiques représentent les observations distinctes qui décrivent chaque échantillon de manière quantitative.

## Données comme tableau cible

Avec la matrice des caractéristiques, désignée par X, nous avons également un tableau cible. Il est également appelé étiquette. Il est désigné par y. L'étiquette ou le tableau cible est généralement unidimensionnel avec une longueur de n_échantillons. Il est généralement contenu dans un tableau NumPy ou une série Pandas. Le tableau cible peut avoir les deux valeurs, des valeurs numériques continues et des valeurs discrètes.

### En quoi le tableau cible diffère-t-il des colonnes de caractéristiques ?

Nous pouvons les distinguer par un point : le tableau cible est généralement la quantité que nous voulons prédire à partir des données, c'est-à-dire, en termes statistiques, la variable dépendante.

### Exemple 1

Dans l'exemple ci-dessous, à partir de l'ensemble de données sur les iris, nous prédisons l'espèce de la fleur en fonction des autres mesures. Dans ce cas, la colonne Espèce est considérée comme la caractéristique.

```python
import seaborn as sns
iris = sns.load_dataset('iris')
%matplotlib inline
import seaborn as sns; sns.set()
sns.pairplot(iris, hue='species', height=3);
```

### Rendu