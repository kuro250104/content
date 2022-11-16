## Introduction

Matplotlib est une bibliothèque de traçage pour Python. Elle est utilisée avec NumPy pour fournir un environnement qui est une alternative open source efficace pour MatLab. Elle peut également être utilisée avec des boîtes à outils graphiques comme PyQt et wxPython.

Le module Matplotlib a été initialement écrit par John D. Hunter. Depuis 2012, Michael Droettboom en est le principal développeur. Actuellement, Matplotlib ver. 1.5.1 est la version stable disponible. Le paquet est disponible en distribution binaire ainsi que sous forme de code source sur <a href="https://matplotlib.org/" title="site officiel de Matplotlib" target="_blank">https://matplotlib.org/</a>.

Par convention, le paquet est importé dans le script Python en ajoutant l'instruction suivante -

```python
from matplotlib import pyplot as plt
```

Ici, ```pyplot()``` est la fonction la plus importante de la bibliothèque matplotlib, qui est utilisée pour tracer des données 2D. Le script suivant trace l'équation ```y = 2x + 5```

### Exemple

```python
import numpy as np 
from matplotlib import pyplot as plt 

x = np.arange(1,11) 
y = 2 * x + 5 
plt.title("Matplotlib demo") 
plt.xlabel("x axis caption") 
plt.ylabel("y axis caption") 
plt.plot(x,y) 
plt.show()
```

Un objet ndarray x est créé à partir de la fonction ```np.arange()``` comme valeurs sur l'axe des x. Les valeurs correspondantes sur l'axe des y sont stockées dans un autre objet ndarray y. Ces valeurs sont tracées à l'aide de la fonction ```plot()``` du sous-module pyplot du paquet matplotlib.

La représentation graphique est affichée par la fonction ```show()```.

Au lieu du graphique linéaire, les valeurs peuvent être affichées de manière discrète en ajoutant une chaîne de format à la fonction ```plot()```. Les caractères de formatage suivants peuvent être utilisés.

**Caractère et description**

- **'-'** - Style de ligne solide
- **'--'** - Style de ligne pointillée
- **'-.'** - Style de ligne tiret-point
- **':'** - Style de ligne en pointillé
- **'.'** - Marqueur de point
- **','** - Marqueur de pixel
- **'o'** - Marqueur de cercle
- **'v'** - Marqueur Triangle_down
- **'^'** - Marqueur Triangle_up
- **'<'** - Marqueur Triangle_gauche
- **'>'** - Marqueur triangulaire_droit
- **'1'** - Marqueur Tri_down
- **'2'** - Marqueur Tri_up
- **'3'** - Marqueur Tri_left
- **'4'** - Marqueur Tri_Droit
- **'s'** - Marqueur carré
- **'p'** - Marqueur du Pentagone
- **'*'** - Marqueur d'étoiles
- **'h'** - Marqueur Hexagone1
- **'H'** - Marqueur Hexagon2
- **'+'** - Marqueur plus
- **'x'** - Marqueur X
- **'D'** - Marqueur de diamant
- **'d'** - Marqueur Thin_diamond
- **'|'** - Marqueur de ligne de V
- **'_'** - Marqueur de ligne

Les abréviations de couleur suivantes sont également définies.

**Caractère et Couleur**

- **'b'** - Blue ( Bleu)
- **'g'** - Green ( Vert)
- **'r'** - Red ( Rouge)
- **'c'** - Cyan ( Cyan)
- **'m'** - Magenta ( Magenta)
- **'y'** - Yellow ( Jaune )
- **'k'** - Black ( Noir )
- **'w'** - White ( Blanc )

Pour afficher les cercles représentant les points, au lieu de la ligne dans l'exemple ci-dessus, utilisez "**ob**" comme chaîne de format dans la fonction ```plot()```.

### Exemple

```python
import numpy as np 
from matplotlib import pyplot as plt 

x = np.arange(1,11) 
y = 2 * x + 5 
plt.title("Matplotlib demo") 
plt.xlabel("x axis caption") 
plt.ylabel("y axis caption") 
plt.plot(x,y,"ob") 
plt.show()
```

## Sine Wave Plot

Le script suivant produit le tracé de l'onde sinusoïdale en utilisant matplotlib.

### Exemple

```python
import numpy as np 
import matplotlib.pyplot as plt  

# Compute the x and y coordinates for points on a sine curve 
x = np.arange(0, 3 * np.pi, 0.1) 
y = np.sin(x) 
plt.title("sine wave form") 

# Plot the points using matplotlib 
plt.plot(x, y) 
plt.show()
```

## subplot()

La fonction ```subplot()``` vous permet de tracer différentes choses dans la même figure. Dans le script suivant, les **valeurs** de **sinus** et de **cosinus** sont tracées.

### Exemple

```python
import numpy as np 
import matplotlib.pyplot as plt  

# Compute the x and y coordinates for points on sine and cosine curves 
x = np.arange(0, 3 * np.pi, 0.1) 
y_sin = np.sin(x) 
y_cos = np.cos(x)  

# Set up a subplot grid that has height 2 and width 1, 
# and set the first such subplot as active. 
plt.subplot(2, 1, 1)

# Make the first plot 
plt.plot(x, y_sin) 
plt.title('Sine')  

# Set the second subplot as active, and make the second plot. 
plt.subplot(2, 1, 2) 
plt.plot(x, y_cos) 
plt.title('Cosine')  

# Show the figure. 
plt.show()
```

## bar()

Le sous-module pyplot fournit la fonction ```bar()``` pour générer des graphiques à barres. L'exemple suivant produit le graphique à barres de deux ensembles de tableaux x et y.

### Exemple

```python
from matplotlib import pyplot as plt 
x = [5,8,10] 
y = [12,16,6]  

x2 = [6,9,11] 
y2 = [6,15,7] 
plt.bar(x, y, align = 'center') 
plt.bar(x2, y2, color = 'g', align = 'center') 
plt.title('Bar graph') 
plt.ylabel('Y axis') 
plt.xlabel('X axis')  

plt.show()
```