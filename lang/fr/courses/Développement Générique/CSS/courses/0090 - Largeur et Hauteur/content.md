En CSS, la hauteur (*height*, en anglais) et la largeur (*width* en anglais) d’un élément HTML sont définis en utilisant les propriétés ```height``` et ```width```. 

Ces propriétés ne sont pas utilisées pour définir les marges intérieures et/ou extérieures, ni les bordures d’un élément HTML, mais bien pour définir la hauteur et la largeur d’un élément.

Pour définir la largeur maximale d’un élément, la propriété ```max-width``` est utilisée. 

Ce cours détail toutes les propriétés CSS utilisable pour régler la hauteur et la largeur d’un élément.

## Les valeurs utilisables avec height et width

Comme beaucoup d’autres propriétés CSS, ```height``` et ```width``` peuvent recevoir plusieurs types de valeurs :

- ```auto``` : valeur utilisée par défaut. Le navigateur calcule lui-même la hauteur et la largeur de l’élément
- ```taille``` : définit la hauteur/largeur d’un élément en px, pt, em, cm
- ```%``` : définit la hauteur et la largeur en pourcentage du bloc contenant. 
- ```initial``` : règle la hauteur et la largeur sur leur valeur par défaut
- ```inherit``` : la hauteur et la largeur sera héritée de l’élément parent

Exemple :

```css
p {
	background-color: red;
	width: 70%;
	height: 400px; /* Ici, le paragraphe aura une largeur de 70% et une hauteur de 400 pixels */
}
```

## Définir une largeur maximum

Comme mentionné dans l’introduction, le CSS permet également de définir une largeur maximum pour un élément HTML. Pour ce faire, il faut utiliser la propriété ```max-width```.

Cette propriété peut recevoir trois types de valeurs :

- ```taille``` : définit la largeur maximum en px, pt, cm, em
- ```%``` : définit la largeur maximum en pourcentage du block contenant
- ```none``` : valeur utilisée par défaut pour indiquer au navigateur qu’il n’y a pas de largeur maximum

Le problème qui peut être rencontré avec la propriété ```width```, c’est lorsque la fenêtre du navigateur est réduite à une largeur inférieure à la largeur de l’élément. Le navigateur va alors rajouter des barres de défilement, rendant la lecture moins agréable. 

Ce problème est manié en utilisant la propriété ```max-width```. Cela va attribuer une largeur maximum à l’élément, peu importe la taille de la fenêtre. 

Exemple :

```css
body {
    background-color : red;
    height : 500px;
    max-width : 400px; /* Dans cet exemple, le corps de la page HTML à une hauteur de 500 pixels et une largeur maximum de 400 pixels, peu importe la taille de la fenêtre */
}
```

__Remarque__ : La propriété ```max-width``` prend le dessus sur la propriété ```width```.