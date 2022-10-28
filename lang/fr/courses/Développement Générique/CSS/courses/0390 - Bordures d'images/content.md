Le langage CSS met à disposition une propriété permettant d’utiliser une image comme pouvant être utilisée comme bordure autour d’un élément.

## La propriété border-image

La propriété ```border-image``` permet d’utiliser une image comme bordure autour d’un élément, plutôt que d’utiliser une border classique.

Cette propriété reçoit les trois valeurs suivantes, dans cet ordre :

- L’image à utiliser pour la bordure
- L’endroit où l’image doit être coupée
- Indiquer si la section centrale de l’image doit être répétée ou étirée. 

Pour les différents exemples de ce cours, l’image ci-dessous sera utilisée :

![Image de base servant de modèle pour ce cours](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/CSS/courses/0390%20-%20Bordures%20d'images/images/image2.jpg)

La propriété ```border-image``` découpe l’image en 9 parties, place les coins orange au niveau des coins et les carrés blancs sont soit répétés, soit étirés, en fonction de la valeur spécifiée à la propriété.

__Remarque :__ Pour que la propriété ```border-image``` fonctionne, la propriété ```border``` doit d’abord être définie. 

Exemple :

```css
#border {
    border: 10px solid transparent;
    padding: 15px;
    border-image: url(border.png) 30 round;
}
```

L’exemple ci-dessus donne le résultat suivant :

![Représentation de l'utilisation de border-image round](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/CSS/courses/0390%20-%20Bordures%20d'images/images/image4.jpg)

Exemple :

```css
#border {
    border: 10px solid transparent;
    padding: 15px;
    border-image: url(border_img.png) 30 stretch;
}
```

L’exemple ci-dessus montre comment utiliser la propriété pour étirer la partie centrale. Cela donne le résultat suivant :

![Représentation de l'utilisation de border-image stretch](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/CSS/courses/0390%20-%20Bordures%20d'images/images/image6.jpg)

__Remarque__ : La propriété border-image est en fait la propriété raccourcie rassemblant les propriétés ```border-image-source```, ```border-image-slice```, ```border-image-width```, ```border-image-outset``` et ```border-image-repeat```.

## Différentes valeurs de découpage

### Exemple 1

Code :

```css
#border {
    border: 10px solid transparent;
    padding: 15px;
    border-image: url(border_img.png) 50 round;
}
```

Rendu :

![Représentation de l'utilisation de border-image avec l'exemple de code ci-dessus](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/CSS/courses/0390%20-%20Bordures%20d'images/images/image3.jpg)

### Exemple 2

Code :

```css
#border {
    border: 10px solid transparent;
    padding: 15px;
    border-image: url(border_img.png) 20% round;
}
```

Rendu :

![Représentation de l'utilisation de border-image avec l'exemple de code ci-dessus](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/CSS/courses/0390%20-%20Bordures%20d'images/images/image1.jpg)

### Exemple 3

Code :

```css
#border {
    border: 10px solid transparent;
    padding: 15px;
    border-image: url(border_img.png) 30% round;
}
```

Rendu :

![Représentation de l'utilisation de border-image avec l'exemple de code ci-dessus](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/CSS/courses/0390%20-%20Bordures%20d'images/images/image5.jpg)