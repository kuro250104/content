## Introduction

NumPy possède une fonction ```numpy.histogram()``` qui est une représentation graphique de la distribution de fréquence des données. Des rectangles de taille horizontale égale correspondant à l'intervalle de classe appelé bin et de hauteur variable correspondant à la fréquence.

## numpy.histogram()

La fonction ```numpy.histogram()``` prend le tableau d'entrée et les bins comme deux paramètres. Les éléments successifs dans le tableau bin agissent comme la limite de chaque bin.

```python
import numpy as np 

a = np.array([22,87,5,43,56,73,55,54,11,20,51,5,79,31,27]) 
np.histogram(a,bins = [0,20,40,60,80,100]) 
hist,bins = np.histogram(a,bins = [0,20,40,60,80,100]) 
print hist 
print bins
```

Il produira le résultat suivant -

```python
[3 4 5 2 1]
[0 20 40 60 80 100]
```

## plt()

Matplotlib peut convertir cette représentation numérique de l'histogramme en un graphique. La fonction plt() du sous-module pyplot prend le tableau contenant les données et le tableau bin comme paramètres et le convertit en un histogramme.

```python
from matplotlib import pyplot as plt 
import numpy as np  

a = np.array([22,87,5,43,56,73,55,54,11,20,51,5,79,31,27]) 
plt.hist(a, bins = [0,20,40,60,80,100]) 
plt.title("histogram") 
plt.show()
```