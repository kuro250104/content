Les types de données numériques stockent des valeurs numériques. Ce sont des types de données immuables. Cela signifie que la modification de la valeur d'un type de données numérique entraîne l'attribution d'un nouvel objet.

Les objets numériques sont créés lorsque vous leur attribuez une valeur. Par exemple :

```python
var1 = 1
var2 = 10
```

Vous pouvez également supprimer la référence à un objet numérique en utilisant l'instruction ```del```. La syntaxe de l'instruction ```del``` est la suivante :

```python
del var1[,var2[,var3[....,varN]]]]
```

Vous pouvez supprimer un objet unique ou plusieurs objets en utilisant l'instruction ```del```. Par exemple :

```python
del var
del var_a, var_b
```

Python supporte différents types numériques :

- **int (entiers signés)** - Ils sont souvent appelés simplement entiers ou ints. Ce sont des nombres entiers positifs ou négatifs sans point décimal. Les entiers dans Python 3 sont de taille illimitée. - **Python 2 possède deux types d'entiers** - int et long. Il n'y a plus de "long integer" dans Python 3.
- **float (floating point real values)** - Également appelés floats, ils représentent des nombres réels et sont écrits avec un point décimal divisant les parties entières et fractionnaires. Les flottants peuvent également être en notation scientifique, avec E ou e indiquant la puissance de 10 (2,5e2 = 2,5 x 102 = 250).
- **complexes (nombres complexes)** - sont de la forme a + bJ, où a et b sont des flottants et J (ou j) représente la racine carrée de -1 (qui est un nombre imaginaire). La partie réelle du nombre est a, et la partie imaginaire est b. Les nombres complexes ne sont pas beaucoup utilisés en programmation Python.

Il est possible de représenter un nombre entier sous forme hexadécimale ou octale

```python
>>> number = 0xA0F #Hexadécimal
>>> number
2575

>>> number = 0o37 #Octal
>>> number
31
```

## Exemples

Voici quelques exemples de chiffres :

| **int** | **float** | **complex** |
| --- | --- | --- |
| 10 | 0.0 | 3.14j |
| 100 | 15.20 | 45.j |
| -786 | -21.9 | 9.322e-36j |
| 080 | 32.3+e18 | .876j |
| -0490 | -90. | -.6545+0J |
| -0x260 | -32.54e100 | 3e+26J |
| 0x69 | 70.2-E12 | 4.53e-7j |

Un nombre complexe consiste en une paire ordonnée de nombres réels à virgule flottante désignés par a + bj, où a est la partie réelle et b la partie imaginaire du nombre complexe.

## Numéro Type Conversion

Python convertit les nombres en interne dans une expression contenant des types mixtes vers un type commun pour l'évaluation. Parfois, il est nécessaire de convertir explicitement un nombre d'un type à un autre pour satisfaire aux exigences d'un opérateur ou d'un paramètre de fonction.

- Tapez ```int(x)``` pour convertir x en un simple entier.
- Tapez ```long(x)``` pour convertir x en un nombre entier long.
- Tapez ```float(x)``` pour convertir x en un nombre à virgule flottante.
- Tapez ```complex(x)``` pour convertir x en un nombre complexe avec la partie réelle x et la partie imaginaire zéro.
- Tapez ```complex(x, y)``` pour convertir x et y en un nombre complexe avec la partie réelle x et la partie imaginaire y. x et y sont des expressions numériques.

## Fonctions mathématiques

Python comprend les fonctions suivantes, qui permettent d'effectuer des calculs mathématiques.

- ```abs(x)``` : La valeur absolue de x : la distance (positive) entre x et zéro.
- ```ceil(x)``` : Le plafond de x : le plus petit entier non inférieur à x.
- ```cmp(x, y)``` : -1 si x < y, 0 si x == y, ou 1 si x > y. Déprécié en Python 3. Utilisez plutôt return (x>y)-(x<y).
- ```exp(x)``` : L'exponentielle de x : e.
- ```fabs(x)``` : La valeur absolue de x.
- ```floor(x)``` : Le plancher de x : le plus grand nombre entier non supérieur à x.
- ```log(x)``` : Le logarithme naturel de x, pour x > 0,$.
- ```log10(x)``` : Le logarithme en base 10 de x pour x > 0.
- ```max(x1, x2,...)``` : Le plus grand de ses arguments : la valeur la plus proche de l'infini positif.
- ```min(x1, x2,...)``` : Le plus petit de ses arguments : la valeur la plus proche de l'infini négatif.
- ```modf(x)``` : Les parties fractionnaire et entière de x dans un tuple de deux éléments. Les deux parties ont le même signe que x. La partie entière est retournée sous forme de flottant.
- ```pow(x, y)``` : La valeur de x**y.
- ```round(x [,n])``` : x arrondi à n chiffres à partir du point décimal. Python arrondit à partir de zéro en cas d'égalité : round(0.5) vaut 1.0 et round(-0.5) vaut -1.0.
- ```sqrt(x)``` : La racine carrée de x pour x > 0.

## Fonctions des nombres aléatoires

Les nombres aléatoires sont utilisés pour les jeux, les simulations, les tests et les applications de sécurité et de confidentialité. Python comprend les fonctions suivantes qui sont couramment utilisées.

- ```choice(seq)``` : Un élément choisi au hasard dans une liste, un tuple ou une chaîne.
- ```randrange ([start,] stop [,step])``` : Un élément choisi aléatoirement dans range(start, stop, step).
- ```random()``` : Un flottant aléatoire r, tel que 0 est inférieur ou égal à r et r est inférieur à 1.
- ```seed([x])``` : Définit la valeur de départ entière utilisée pour générer des nombres aléatoires. Appelez cette fonction avant d'appeler toute autre fonction du module aléatoire. Retourne None.
- ```shuffle(lst)``` : Rend aléatoire les éléments d'une liste en place. Retourne None.
- ```uniform(x, y)``` : Un flottant aléatoire r, tel que x est inférieur ou égal à r et r est inférieur à y.

## Fonctions trigonométriques

Python comprend les fonctions suivantes qui effectuent des calculs trigonométriques.

- ```acos(x)``` : Retourne l'arc cosinus de x, en radians.
- ```asin(x)``` : Retourne l'arc sinus de x, en radians.
- ```atan(x)``` : Retourne l'arc tangent de x, en radians.
- ```atan2(y, x)``` : Retourne l'atan(y / x), en radians.
- ```cos(x)``` : Retourne le cosinus de x en radians.
- ```hypot(x, y)``` : Retourne la norme euclidienne, sqrt(x*x + y*y).
- ```sin(x)``` : Retourne le sinus de x radians.
- ```tan(x)``` : Retourne la tangente de x radians.
- ```degrees(x)``` : Convertit l'angle x de radians en degrés.
- ```radians(x)``` : Convertit l'angle x de degrés en radians.

## Constantes mathématiques

Le module définit également deux constantes mathématiques :

- ```pi``` : La constante mathématique pi.
- ```e``` : La constante mathématique e.
