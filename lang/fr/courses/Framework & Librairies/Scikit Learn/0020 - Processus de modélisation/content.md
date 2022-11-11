## Chargement d'un ensemble de données

Une collection de données est appelée ensemble de données. Il est composé des deux éléments suivants :

- **Caractéristiques** - Les variables des données sont appelées caractéristiques. Elles sont également appelées prédicteurs, entrées ou attributs.
    - **Matrice des caractéristiques** - C'est la collection des caractéristiques, s'il y en a plus d'une.
    - **Noms des caractéristiques** - C'est la liste de tous les noms des caractéristiques.
- **Réponse** - C'est la variable de sortie qui dépend essentiellement des variables des caractéristiques. Elle est également connue sous le nom de cible, d'étiquette ou de sortie.
    - **Vecteur de réponse** - Il est utilisé pour représenter la colonne de réponse. En général, nous n'avons qu'une seule colonne de réponse.
    - **Noms de cible** - Ils représentent les valeurs possibles prises par un vecteur de réponse.

Scikit-learn dispose de quelques ensembles de données d'exemple comme l'iris et les chiffres pour la classification et les prix des maisons à Boston pour la régression.

### Exemple

Voici un exemple de chargement d'un ensemble de données sur l'iris.

```python
from sklearn.datasets import load_iris
iris = load_iris()
X = iris.data
y = iris.target
feature_names = iris.feature_names
target_names = iris.target_names
print("Feature names:", feature_names)
print("Target names:", target_names)
print("\nFirst 10 rows of X:\n", X[:10])
```

### Sortie

```bash
Feature names: ['sepal length (cm)', 'sepal width (cm)', 'petal length (cm)', 'petal width (cm)']
Target names: ['setosa' 'versicolor' 'virginica']
First 10 rows of X:
[
   [5.1 3.5 1.4 0.2]
   [4.9 3. 1.4 0.2]
   [4.7 3.2 1.3 0.2]
   [4.6 3.1 1.5 0.2]
   [5. 3.6 1.4 0.2]
   [5.4 3.9 1.7 0.4]
   [4.6 3.4 1.4 0.3]
   [5. 3.4 1.5 0.2]
   [4.4 2.9 1.4 0.2]
   [4.9 3.1 1.5 0.1]
]
```

## Fractionnement de l'ensemble de données

Pour vérifier la précision de notre modèle, nous pouvons diviser l'ensemble de données en deux parties : un ensemble d'entraînement et un ensemble de test. Utilisez l'ensemble d'entraînement pour former le modèle et l'ensemble de test pour tester le modèle. Ensuite, nous pouvons évaluer l'efficacité de notre modèle.

### Exemple

Dans l'exemple suivant, les données sont réparties dans un rapport 70:30, c'est-à-dire que 70 % des données sont utilisées comme données d'entraînement et 30 % comme données de test. Le jeu de données est celui de l'iris, comme dans l'exemple précédent.

```python
from sklearn.datasets import load_iris
iris = load_iris()

X = iris.data
y = iris.target

from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size = 0.3, random_state = 1
)

print(X_train.shape)
print(X_test.shape)

print(y_train.shape)
print(y_test.shape)
```

### Sortie

```bash
(105, 4)
(45, 4)
(105,)
(45,)
```

Comme on le voit dans l'exemple ci-dessus, il utilise la fonction train_test_split() de scikit-learn pour diviser l'ensemble de données. Cette fonction a les arguments suivants :

- **X, y** - Ici, X est la matrice des caractéristiques et y est le vecteur de réponse, qui doivent être divisés.
- **test_size** - Cela représente le rapport entre les données de test et le total des données données. Dans l'exemple ci-dessus, nous définissons test_data = 0,3 pour 150 lignes de X. Cela produira des données de test de 150*0,3 = 45 lignes.
- **random_size** - Il est utilisé pour garantir que la répartition sera toujours la même. Ceci est utile dans les situations où vous voulez des résultats reproductibles.

## Entraînement du modèle

Ensuite, nous pouvons utiliser notre ensemble de données pour entraîner un modèle de prédiction. Comme nous l'avons vu, scikit-learn dispose d'une large gamme d'algorithmes de Machine Learning (ML) qui ont une interface cohérente pour l'ajustement, la prédiction de la précision, le rappel, etc.

### Exemple

Dans l'exemple ci-dessous, nous allons utiliser le classificateur KNN (K nearest neighbors). N'entrez pas dans les détails des algorithmes KNN, car il y aura un chapitre séparé pour cela. Cet exemple est utilisé pour vous faire comprendre la partie implémentation uniquement.

```python
from sklearn.datasets import load_iris
iris = load_iris()
X = iris.data
y = iris.target
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size = 0.4, random_state=1
)
from sklearn.neighbors import KNeighborsClassifier
from sklearn import metrics
classifier_knn = KNeighborsClassifier(n_neighbors = 3)
classifier_knn.fit(X_train, y_train)
y_pred = classifier_knn.predict(X_test)
# Finding accuracy by comparing actual response values(y_test)with predicted response value(y_pred)
print("Accuracy:", metrics.accuracy_score(y_test, y_pred))
# Providing sample data and the model will make prediction out of that data

sample = [[5, 5, 3, 2], [2, 4, 3, 5]]
preds = classifier_knn.predict(sample)
pred_species = [iris.target_names[p] for p in preds] print("Predictions:", pred_species)
```

### Sortie

```bash
Accuracy: 0.9833333333333333
Predictions: ['versicolor', 'virginica']
```

## Persistance du modèle

Une fois que vous avez formé le modèle, il est souhaitable que le modèle soit persistant pour une utilisation future afin que nous n'ayons pas besoin de le former à nouveau. Cela peut être fait avec l'aide des fonctions dump et load du package joblib.

Prenons l'exemple ci-dessous, dans lequel nous allons sauvegarder le modèle formé ci-dessus (classifier_knn) pour une utilisation ultérieure.

```python
from sklearn.externals import joblib
joblib.dump(classifier_knn, 'iris_classifier_knn.joblib')
```

Le code ci-dessus enregistrera le modèle dans un fichier nommé ```iris_classifier_knn.joblib```. Maintenant, l'objet peut être rechargé à partir du fichier avec l'aide du code suivant :

```python
joblib.load('iris_classifier_knn.joblib')
```

## Prétraitement des données

Comme nous traitons un grand nombre de données et que celles-ci sont sous forme brute, nous devons les convertir en données significatives avant de les introduire dans les algorithmes d'apprentissage automatique. Ce processus s'appelle le prétraitement des données. Scikit-learn dispose d'un paquet nommé preprocessing à cette fin. Le paquet de prétraitement dispose des techniques suivantes :

### Binarisation

Cette technique de prétraitement est utilisée lorsque nous devons convertir nos valeurs numériques en valeurs booléennes.

#### Exemple

```python
import numpy as np
from sklearn import preprocessing
Input_data = np.array(
    [2.1, -1.9, 5.5],
    [-1.5, 2.4, 3.5],
    [0.5, -7.9, 5.6],
    [5.9, 2.3, -5.8]]
)
data_binarized = preprocessing.Binarizer(threshold=0.5).transform(input_data)
print("\nBinarized data:\n", data_binarized)
```

Dans l'exemple ci-dessus, nous avons utilisé la valeur seuil = 0,5 et c'est pourquoi, toutes les valeurs supérieures à 0,5 seront converties en 1, et toutes les valeurs inférieures à 0,5 seront converties en 0.

#### Sortie

```python
Binarized data:
[
    [ 1. 0. 1.]
    [ 0. 1. 1.]
    [ 0. 0. 1.]
    [ 1. 1. 0.]
]
```

## Suppression de la moyenne

Cette technique est utilisée pour éliminer la moyenne du vecteur de caractéristiques afin que chaque caractéristique soit centrée sur zéro.

### Exemple

```python
import numpy as np
from sklearn import preprocessing
Input_data = np.array(
    [2.1, -1.9, 5.5],
    [-1.5, 2.4, 3.5],
    [0.5, -7.9, 5.6],
    [5.9, 2.3, -5.8]]
)

#displaying the mean and the standard deviation of the input data
print("Mean =", input_data.mean(axis=0))
print("Stddeviation = ", input_data.std(axis=0))
#Removing the mean and the standard deviation of the input data

data_scaled = preprocessing.scale(input_data)
print("Mean_removed =", data_scaled.mean(axis=0))
print("Stddeviation_removed =", data_scaled.std(axis=0))
```

### Sortie

```python
Mean = [ 1.75 -1.275 2.2 ]
Stddeviation = [ 2.71431391 4.20022321 4.69414529]
Mean_removed = [ 1.11022302e-16 0.00000000e+00 0.00000000e+00]
Stddeviation_removed = [ 1. 1. 1.]
```

## Mise à l'échelle

Nous utilisons cette technique de prétraitement pour mettre à l'échelle les vecteurs de caractéristiques. La mise à l'échelle des vecteurs de caractéristiques est importante, car les caractéristiques ne doivent pas être synthétiquement grandes ou petites.

### Exemple

```python
import numpy as np
from sklearn import preprocessing
Input_data = np.array(
    [
        [2.1, -1.9, 5.5],
        [-1.5, 2.4, 3.5],
        [0.5, -7.9, 5.6],
        [5.9, 2.3, -5.8]
    ]
)
data_scaler_minmax = preprocessing.MinMaxScaler(feature_range=(0,1))
data_scaled_minmax = data_scaler_minmax.fit_transform(input_data)
print ("\nMin max scaled data:\n", data_scaled_minmax)
```

### Sortie

```python
Min max scaled data:
[
    [ 0.48648649 0.58252427 0.99122807]
    [ 0. 1. 0.81578947]
    [ 0.27027027 0. 1. ]
    [ 1. 0.99029126 0. ]
]
```

## Normalisation

Nous utilisons cette technique de prétraitement pour modifier les vecteurs de caractéristiques. La normalisation des vecteurs de caractéristiques est nécessaire pour que les vecteurs de caractéristiques puissent être mesurés à une échelle commune. Il existe deux types de normalisation : - la normalisation des vecteurs de caractéristiques.

### Normalisation L1

Elle est également appelée " moindres écarts absolus ". Elle modifie la valeur de telle manière que la somme des valeurs absolues reste toujours égale à 1 dans chaque ligne. L'exemple suivant montre la mise en œuvre de la normalisation L1 sur les données d'entrée.

#### Exemple

```python
import numpy as np
from sklearn import preprocessing
Input_data = np.array(
    [
        [2.1, -1.9, 5.5],
        [-1.5, 2.4, 3.5],
        [0.5, -7.9, 5.6],
        [5.9, 2.3, -5.8]
    ]
)
data_normalized_l1 = preprocessing.normalize(input_data, norm='l1')
print("\nL1 normalized data:\n", data_normalized_l1)
```

#### Sortie

```bash
L1 normalized data:
[
    [ 0.22105263 -0.2 0.57894737]
    [-0.2027027 0.32432432 0.47297297]
    [ 0.03571429 -0.56428571 0.4 ]
    [ 0.42142857 0.16428571 -0.41428571]
]
```

### Normalisation L2

Également appelée " moindres carrés ". Elle modifie la valeur de manière à ce que la somme des carrés soit toujours égale à 1 dans chaque ligne. L'exemple suivant montre la mise en œuvre de la normalisation L2 sur les données d'entrée.

#### Exemple

```python
import numpy as np
from sklearn import preprocessing
Input_data = np.array(
    [
        [2.1, -1.9, 5.5],
        [-1.5, 2.4, 3.5],
        [0.5, -7.9, 5.6],
        [5.9, 2.3, -5.8]
    ]
)
data_normalized_l2 = preprocessing.normalize(input_data, norm='l2')
print("\nL1 normalized data:\n", data_normalized_l2)
```

#### Sortie

```bash
L2 normalized data:
[
    [ 0.33946114 -0.30713151 0.88906489]
    [-0.33325106 0.53320169 0.7775858 ]
    [ 0.05156558 -0.81473612 0.57753446]
    [ 0.68706914 0.26784051 -0.6754239 ]
]
```