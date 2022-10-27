Comme mentionné dans le chapitre des largeurs et hauteurs en CSS, il est possible de régler la largeur d’un élément. 

## Utilisation de width, max-width et margin: auto

Par défaut, un élément de type block prendra toute la largeur disponible au sein de son conteneur, s’étirant autant que possible à gauche et à droite.

Afin de remédier à ce problème, le langage CSS permet de spécifier une largeur à un élément enfant. Pour ce faire, il faut utiliser la propriété ```width``` et lui attribuer une valeur. Ensuite, il est possible de passer la valeur ```auto``` à la propriété ```margin```, afin que l’élément HTML soit centré dans son conteneur. 

__Remarque__ : La valeur ```auto``` est importante pour les marges extérieures gauches et droites, mais pas pour celles supérieures et inférieures.

![Représentation du centrage d'un élément HTML grâce à l'utilisation de max-width et margin: auto](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/CSS/courses/0190%20-%20Largeur%20maximale/images/image1.jpg)

Exemple :

```css
h1 {
	width : 500px; /* Le titre h1 a une largeur définie à 500 pixels */
	margin : auto; /* En attribuant la valeur auto à margin, le titre sera centré dans son conteneur */
}
```

__Remarque__ : Le problème dans l’exemple ci-dessus survient lorsque la fenêtre est réduite à moins de 500 pixels. Le navigateur ajoute des barres de défilement horizontales pour que l’utilisateur puisse voir le reste de la page. 

Pour remédier au problème cité dans la remarque ci-dessus, afin de permettre au navigateur de mieux gérer l’affichage en cas de réduction de la taille de la fenêtre, il est recommandé d’utiliser la propriété ```max-width```. Cela devient essentiel lorsque le site web est consulté depuis un téléphone mobile, par exemple. Cette propriété permet de définir une largeur maximale pour un élément.

Exemple :

```css
h1 {
	max-width : 500px; /* En cas de réduction de la taille de la fenêtre, la largeur du titre sera mieux gérée par le navigateur */
	margin : auto; /* En attribuant la valeur auto à margin, le titre sera centré dans son conteneur */
}
```