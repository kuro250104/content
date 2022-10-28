Les dégradés en CSS permettent de faire une jolie transition entre plusieurs couleurs. Il existe deux types de dégradés :

- **Les dégradés linéaires** : haut, bas, gauche droite ou en diagonales 
- **Les dégradés radiaux** : définis par leurs centres

## Les dégradés linéaires

Pour créer un dégradé linéaire, il faut définir au moins deux couleurs. Il est également possible de définir un point de départ et une direction (ou un angle). 

### Syntaxe

```css
#degrade {
    background-image: linear-gradient(direction, couleur1, couleur2);
}
```

#### Du haut vers le bas

Par défaut, la direction du dégradé est du haut vers le bas. 

Exemple :

```css
#degrade {
	height: 100px;
	background-image: linear-gradient(black, grey);
}
```

#### De la gauche vers la droite

Pour faire un dégradé allant de la gauche vers la droite, il suffit d’ajouter ```to right``` comme premier paramètre de la fonction ```linear-gradient```.

Exemple :

```css
#degrade {
	height: 100px;
	background-image: linear-gradient(to right, black, grey);
}
```

#### En diagonal

Le langage CSS permet également de faire un dégradé dont la direction serait diagonale. Pour ce faire, il faut à la fois préciser le point de départ en diagonale et le point de départ à l’horizontal.

Exemple :

```css
#degrade {
	height: 100px;
	background-image: linear-gradient(to bottom right, black, grey);
}
```

### Utiliser les angles

Pour avoir plus de contrôle sur la direction du dégradé, il est également possible de définir un angle, plutôt que d’utiliser les directions prédéfinies. Une valeur de ```0deg``` équivaut à ```to top```, une valeur de ```90deg``` équivaut à ```to right``` et une valeur de ```180deg``` équivaut à ```to bottom```. 

La syntaxe reste la même, à la différence près qu’en premier paramètre, la fonction CSS linear-gradient, prend la valeur de l’angle, plutôt que la direction. 

Exemple : 

```css
#degrade {
	height: 100px;
	background-image: linear-gradient(90deg, black, grey); /* 90deg = "to right" */
}
```

L’exemple ci-dessus donne un dégradé de la gauche vers la droite, car ```90deg``` d’angle équivaut à ```to right```.

### Utiliser plusieurs couleurs

Il est également possible de créer un dégradé avec plus de 2 couleurs. Pour ce faire, il suffit de préciser toutes les couleurs à utiliser pour le dégradé. 

Exemple :

```css
#degrade {
	height: 100px;
	background-image: linear-gradient(90deg, black, grey, white);
}
```

### Combiner la transparence avec les dégradés

Le langage CSS permet également d’utiliser les dégradés en combinaison avec la transparence. Cela permet de créer des effets de fondu.

Pour ce faire, il suffit d’utiliser la fonction ```rgba()```, afin de préciser les couleurs à utiliser pour le dégradé, ainsi que le paramètre *Alpha*, une valeur entre 0 et 1, permettant de préciser le niveau de transparence. 

Exemple :

```css
#degrade {
	height: 100px;
	background-image: linear-gradient(90deg, rgba(0, 255, 0, 0), rgba(0, 255, 0, 1));
}
```

### Répéter un dégradé linéaire

Pour répéter un dégradé linéaire, la fonction CSS ```repeat-linear-gradient()``` doit être utilisée. 

Exemple :

```css
#degrade {
    background-image: repeating-linear-gradient(red, green 10%, blue 10%);
}
```

## Les dégradés en radial

Les dégradés en radial sont définis par leurs centres. Comme pour les dégradés linéaires, il faut que deux couleurs au moins soient définies pour utiliser les dégradés en radial. 

### Syntaxe

Pour utiliser les dégradés en radial, la syntaxe est la suivante :

```background-image: radial-gradient(taille de la forme at position, couleur1, couleur2, ...);```

Par défaut, la forme du dégradé est elliptique, la taille est le coin le plus éloigné et la position est centrée. 

#### Dégradé en radial - couleurs éloignées uniformément

Si aucune valeur d’éloignement n’est précisée, les couleurs sont, par défaut, éloignées uniformément. 

Exemple :

```css
#degrade {
	height: 100px;
	background-image: radial-gradient(white, grey, black);
}
```

#### Dégradé en radial - Espaces différents entre les couleurs

Le langage CSS permet de créer des dégradés en radial et d’attribuer une valeur d’espace différente pour chaque couleur. 

Pour ce faire, il suffit de préciser, à côté du nom de la couleur, le pourcentage de place que cette dernière doit prendre. 

Exemple :

```css
#degrade {
	height: 100px;
	background-image: radial-gradient(white 5%, grey 25%, black 60%);
}
```

### Définir la forme

Un dégradé radial peut soit avoir une forme de cercle (*circle*, en anglais), soit une forme elliptique - qui est la forme par défaut. 

Exemple :

```css
#degrade {
	height: 100px;
	background-image: radial-gradient(circle, white, grey, black);
}
```

### Paramètres de taille

Les paramètres de tailles définissent la taille du dégradé. Pour les dégradés en radial, il existe 4 paramètres de taille possibles :

- ```closest-side``` : le côté le plus proche
- ```farthest-side``` : le côté le plus éloigné
- ```closest-corner``` : le coin le plus proche
- ```farthest-corner``` : le coin le plus éloigné

Ci-dessous, les exemples utilisant chacun des paramètres de taille.

Exemple pour ```closest-side``` :

```css
#degrade {
	height: 100px;
	background-image: radial-gradient(closest-side at 60% 50%, white, grey, black); /* Les pourcentages après "at" définissent la position */
}
```

Exemple pour ```farthest-side``` :

```css
#degrade {
	height: 100px;
	background-image: radial-gradient(farthest-side at 60% 50%, white, grey, black); /* Les pourcentages après "at" définissent la position */
}
```

Exemple pour ```closest-corner``` :

```css
#degrade {
	height: 100px;
	background-image: radial-gradient(closest-corner at 60% 50%, white, grey, black); 
}
```

Exemple pour ```farthest-side``` :

```css
#degrade {
	height: 100px;
	background-image: radial-gradient(farthest-corner at 60% 50%, white, grey, black); 
}
```

### Répéter un dégradé radial

Comme pour les dégradés linéaires, le langage CSS permet la répétition d’un dégradé en radial. Pour ce faire, il faut utiliser la fonction ```repeating-radial-gradient()```.

Exemple :

```css
#degrade {
	height: 100px;
	background-image: repeating-radial-gradient(white, grey 10%, black 20%); 
}
```