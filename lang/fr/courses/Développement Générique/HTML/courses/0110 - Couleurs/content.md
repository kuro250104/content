Le langage HTML permet de définir des couleurs pour les différents éléments de la page web, en utilisant les propriétés appropriées dans l’attribut style. 

## Couleurs

Le langage HTML met à disposition plusieurs moyens de définir la couleur d’un élément. En effet, il est possible de préciser directement le nom de la couleur, en anglais (red, green, blue, orange, etc., ou encore en utilisant une valeur hexadécimale, une valeur RGB ou RGBA.

Une couleur hexadécimale est un ensemble de lettres et de chiffres, précédé du signe dièse (**#**), représentant la quantité de vert de rouge et de bleu composant la couleur en question. La couleur blanche, en hexadécimale est la suivante : #FFFFFF (souvent raccourcie #fff).

Le RGB (pour red, green, blue) est également la quantité de rouge, de vert et de bleu présent dans une couleur. La différence avec la notation hexadécimale, est que le RGB reçoit, pour chaque couleur (rouge, vert, bleu), un chiffre entre 0 et 255. Par exemple, en RGB, la couleur rouge serait définie ainsi : RGB(255, 0, 0).

RGBA est presque identique à RGB, à la différence près qu’en plus, il reçoit un chiffre entre 0 et 1 pour définir le degré d’opacité de la couleur ; 0 étant une transparence totale, 1 une opacité totale.

Exemple avec les noms de couleurs en anglais :

``` html
<body>
    <!-- Paragraphe avec fond couleur Tomato -->
    <p style="background-color:Tomato;">Tomato</p>
    <!-- Paragraphe avec fond couleur Orange -->
    <p style="background-color:Orange;">Orange</p>
    <!-- Paragraphe avec fond couleur DodgerBlue -->
    <p style="background-color:DodgerBlue;">DodgerBlue</p>
    <!-- Paragraphe avec fond couleur MediumSeaGreen -->
    <p style="background-color:MediumSeaGreen;">MediumSeaGreen</p>
    <!-- Paragraphe avec fond couleur Gray -->
    <p style="background-color:Gray;">Gray</p>
    <!-- Paragraphe avec fond couleur Slate Blue -->
    <p style="background-color:SlateBlue;">SlateBlue</p>
    <!-- Paragraphe avec fond couleur Light Gray -->
    <p style="background-color:LightGray;">LightGray</p>
</body>
```

Exemple avec l’hexadécimale, le RGB et le RGBA :

```html
<body>
    <p>D'autres valeurs pour la couleur Tomato :</p>
 
    <!-- Paragraphe avec fond Tomata en rgb -->
    <p style="background-color:rgb(255, 99, 71);">rgb(255, 99, 71)</p>
    <!-- Paragraphe avec fond Tomata en hexadécimal -->
    <p style="background-color:#ff6347;">#ff6347</p>
    <!-- Paragraphe avec fond Tomata en RGBA -->
    <p style="background-color:rgba(0, 0, 255, 0,5);">rgba(0, 0, 255, 0,5)</p>
</body>
```

## Couleur du texte

Pour définir la couleur du texte, il suffit passer la propriété color à l’attribut style, suivie de la couleur à attribuer à l’élément.

Exemple :

```html
<!-- Texte de couleur Tomato -->
<p style="color:Tomato;">Tomato</p>
<!-- Texte de couleur DodgerBlue -->
<p style="color:DodgerBlue;">DodgerBlue</p>
<!-- Texte de couleur MediumSeaGreen -->
<p style="color:MediumSeaGreen;">MediumSeaGreen</p>
```

## Couleur de la bordure

L’attribut style permet également d’ajouter une bordure autour d’un élément. Pour ce faire, la propriété border doit être utilisée, suivie de l’épaisseur de la bordure (1 pixel, par exemple), puis du style de la bordure (solid, pour une bordure au trait plein, ou dashed pour une bordure en pointillés), puis, enfin, du nom de la couleur à attribuer à la bordure. 

Exemple :

```html
<!-- Bordure de couleur Tomato large de 2px et de type solid -->
<p style="border:2px solid Tomato;">Tomato</p>
<!-- Bordure de couleur DodgerBlue large de 2px -->
<p style="border:2px solid DodgerBlue;">DodgerBlue</p>
<!-- Bordure de couleur MediumSeaGreen large de 2px -->
<p style="border:2px solid MediumSeaGreen;">MediumSeaGreen</p>
```