## Introduction

La réduction de la dimensionnalité, une méthode d'apprentissage automatique non supervisée, est utilisée pour réduire le nombre de variables caractéristiques pour chaque échantillon de données en sélectionnant un ensemble de caractéristiques principales. L'analyse en composantes principales (ACP ou PCA) est l'un des algorithmes populaires de réduction de la dimensionnalité.

## Exact PCA

L'analyse en composantes principales (ACP ou PCA) est utilisée pour la réduction linéaire de la dimensionnalité en utilisant la décomposition en valeurs singulières (SVD) des données pour les projeter dans un espace de dimension inférieure. Lors de la décomposition par ACP, les données d'entrée sont centrées mais pas mises à l'échelle pour chaque caractéristique avant d'appliquer la SVD.

La bibliothèque Scikit-learn ML fournit le module sklearn.decomposition.PCA qui est implémenté comme un objet transformateur qui apprend n composantes dans sa méthode fit(). Il peut également être utilisé sur de nouvelles données pour les projeter sur ces composantes.

### Exemple

L'exemple ci-dessous utilisera le module sklearn.decomposition.PCA pour trouver les 5 meilleures composantes principales du jeu de données Pima Indians Diabetes.

```python
from pandas import read_csv
from sklearn.decomposition import PCA
path = r'C:\Users\Leekha\Desktop\pima-indians-diabetes.csv'
names = ['preg', 'plas', 'pres', 'skin', 'test', 'mass', 'pedi', 'age', 'class']
dataframe = read_csv(path, names = names)
array = dataframe.values
X = array[:,0:8]
Y = array[:,8]
pca = PCA(n_components = 5)
fit = pca.fit(X)
print(("Explained Variance: %s") % (fit.explained_variance_ratio_))
print(fit.components_)
```

### Sortie

```python
Explained Variance: [0.88854663 0.06159078 0.02579012 0.01308614 0.00744094]
[
    [-2.02176587e-03 9.78115765e-02 1.60930503e-02 6.07566861e-029.93110844e-01 1.40108085e-02 5.37167919e-04 -3.56474430e-03]
    [-2.26488861e-02 -9.72210040e-01 -1.41909330e-01 5.78614699e-029.46266913e-02 -4.69729766e-02 -8.16804621e-04 -1.40168181e-01]
    [-2.24649003e-02 1.43428710e-01 -9.22467192e-01 -3.07013055e-012.09773019e-02 -1.32444542e-01 -6.39983017e-04 -1.25454310e-01]
    [-4.90459604e-02 1.19830016e-01 -2.62742788e-01 8.84369380e-01-6.55503615e-02 1.92801728e-01 2.69908637e-03 -3.01024330e-01]
    [ 1.51612874e-01 -8.79407680e-02 -2.32165009e-01 2.59973487e-01-1.72312241e-04 2.14744823e-02 1.64080684e-03 9.20504903e-01]
]
```

## Incremental PCA

Incremental Principal Component Analysis (IPCA) is used to address the biggest limitation of Principal Component Analysis (PCA) and that is PCA only supports batch processing, means all the input data to be processed should fit in the memory.

La bibliothèque Scikit-learn ML fournit le module sklearn.decomposition.IPCA qui permet de mettre en œuvre l'ACP hors cœur, soit en utilisant sa méthode partial_fit sur des morceaux de données extraits séquentiellement, soit en permettant l'utilisation de np.memmap, un fichier mappé en mémoire, sans charger le fichier entier en mémoire.

Comme pour l'ACP, lors de la décomposition par l'IPCA, les données d'entrée sont centrées mais pas mises à l'échelle pour chaque caractéristique avant d'appliquer la SVD.

### Exemple

L'exemple ci-dessous utilise le module sklearn.decomposition.IPCA sur le jeu de données Sklearn digit.

```python
from sklearn.datasets import load_digits
from sklearn.decomposition import IncrementalPCA
X, _ = load_digits(return_X_y = True)
transformer = IncrementalPCA(n_components = 10, batch_size = 100)
transformer.partial_fit(X[:100, :])
X_transformed = transformer.fit_transform(X)
X_transformed.shape
```

### Sortie

```python
(1797, 10)
```

Ici, nous pouvons effectuer un ajustement partiel sur de plus petits lots de données (comme nous l'avons fait sur 100 par lot) ou vous pouvez laisser la fonction fit() diviser les données en lots.

## Kernel PCA

L'analyse en composantes principales à noyau, une extension de l'ACP, réalise une réduction non linéaire de la dimensionnalité en utilisant des noyaux. Elle supporte à la fois transform et inverse_transform.

La bibliothèque Scikit-learn ML fournit le module sklearn.decomposition.KernelPCA.

### Exemple

L'exemple ci-dessous utilise le module sklearn.decomposition.KernelPCA sur le jeu de données Sklearn digit. Nous utilisons un noyau sigmoïde.

```python
from sklearn.datasets import load_digits
from sklearn.decomposition import KernelPCA
X, _ = load_digits(return_X_y = True)
transformer = KernelPCA(n_components = 10, kernel = 'sigmoid')
X_transformed = transformer.fit_transform(X)
X_transformed.shape
```

### Sortie

```python
(1797, 10)
```

## ACP en utilisant SVD aléatoire

L'Analyse en Composantes Principales (ACP ou PCA) utilisant la SVD randomisée est utilisée pour projeter les données dans un espace de dimension inférieure préservant la plupart de la variance en abandonnant le vecteur singulier des composantes associées aux valeurs singulières inférieures. Ici, le module sklearn.decomposition.PCA avec le paramètre optionnel svd_solver='randomized' va être très utile.

### Exemple

L'exemple ci-dessous utilise le module sklearn.decomposition.PCA avec le paramètre optionnel svd_solver='randomized' pour trouver les 7 meilleures composantes principales de l'ensemble de données Pima Indians Diabetes.

```python
from pandas import read_csv
from sklearn.decomposition import PCA
path = r'C:\Users\Leekha\Desktop\pima-indians-diabetes.csv'
names = ['preg', 'plas', 'pres', 'skin', 'test', 'mass', 'pedi', 'age', 'class']
dataframe = read_csv(path, names = names)
array = dataframe.values
X = array[:,0:8]
Y = array[:,8]
pca = PCA(n_components = 7,svd_solver = 'randomized')
fit = pca.fit(X)
print(("Explained Variance: %s") % (fit.explained_variance_ratio_))
print(fit.components_)
```

### Sortie

```python
Explained Variance: [8.88546635e-01 6.15907837e-02 2.57901189e-02 1.30861374e-027.44093864e-03 3.02614919e-03 5.12444875e-04]
[
    [-2.02176587e-03 9.78115765e-02 1.60930503e-02 6.07566861e-029.93110844e-01 1.40108085e-02 5.37167919e-04 -3.56474430e-03]
    [-2.26488861e-02 -9.72210040e-01 -1.41909330e-01 5.78614699e-029.46266913e-02 -4.69729766e-02 -8.16804621e-04 -1.40168181e-01]
    [-2.24649003e-02 1.43428710e-01 -9.22467192e-01 -3.07013055e-012.09773019e-02 -1.32444542e-01 -6.39983017e-04 -1.25454310e-01]
    [-4.90459604e-02 1.19830016e-01 -2.62742788e-01 8.84369380e-01-6.55503615e-02 1.92801728e-01 2.69908637e-03 -3.01024330e-01]
    [ 1.51612874e-01 -8.79407680e-02 -2.32165009e-01 2.59973487e-01-1.72312241e-04 2.14744823e-02 1.64080684e-03 9.20504903e-01]
    [-5.04730888e-03 5.07391813e-02 7.56365525e-02 2.21363068e-01-6.13326472e-03 -9.70776708e-01 -2.02903702e-03 -1.51133239e-02]
    [ 9.86672995e-01 8.83426114e-04 -1.22975947e-03 -3.76444746e-041.42307394e-03 -2.73046214e-03 -6.34402965e-03 -1.62555343e-01]
]
```