Les compteurs sont des “variables” tenues par le langage CSS dont la valeur est incrémentée (augmente) par des règles utilisées par le langage, chaque fois que la variable en question est utilisée. 

En informatique, une variable est une case de mémoire, étiquetée, dans laquelle le développeur peut stocker une information à utiliser plus tard dans le programme. Une variable est “détruite” à chaque fermeture du programme et la case mémoire dans laquelle l’information a été stockée est libérée. 

En CSS, les compteurs permettent en plus d’ajuster le style de l’élément en fonction de là où ce dernier est placé. 

## Numérotation automatique avec les compteurs 

Pour pouvoir profiter des compteurs en CSS, les propriétés suivantes doivent être utilisées :

- ```counter-reset``` : permet de créer ou de remettre à zéro un compteur
- ```counter-increment``` : permet d’incrémenter (d’augmenter) un compteur
- ```content``` : permet d’insérer le contenu généré
- ```counter()``` ou ```counters()``` : ces fonctions permettent d’ajouter la valeur d’un compteur à un élément.

Pour utiliser un compteur, il faut d’abord le créer, en utilisant la propriété ```counter-reset```.

Exemple :

```css
body {
	counter-reset: section; /* Création du compteur "section" */
}

h1::before {
	counter-increment: section; /* Chaque fois que le navigateur rencontrera un titre h1, le compteur section est incrémenté */
	content: "Section " counter(section) " : "; /* Affichage du contenu */
}
```

## Compteurs d’imbrication

Les compteurs CSS permettent également de créer des compteurs dits “d’imbrication”, c'est-à-dire des compteurs qui affichent 1.1, 1.2, etc. 

Pour ce faire, il suffit de créer un compteur général pour le corps de la page (```<body>```) avec counter-reset, puis de le remettre à zéro pour les éléments ```h1```. Ainsi, cela permettra d’afficher le compteur devant chaque titre ```h1```, par exemple, et d’afficher un compteur d’imbrication devant les titres ```h2```.

Exemple :

```css
body {
	counter-reset: section; /* Création d'un compteur général appelé "section" */
}

h1 {
	counter-reset: subsection; /* Création d'un second compteur appelé subsection */
}

h1::before {
	counter-increment: section; /* Chaque fois que le navigateur rencontrera un titre h1, le compteur section est incrémenté */
	content: "Section " counter(section) " : "; /* Affichage du contenu */
}

h2::before {
	counter-increment: subsection; /* Incrémentation du compteur "subsection" pour créer un compteur d'imbrication */
	content: counter(section) ". " counter(subsection) " ";
}
```

Les compteurs CSS sont généralement utilisés pour créer des sous-listes. Pour ce faire, il faut utiliser la fonction counters() afin de pouvoir insérer une chaîne de caractères entre les différents niveaux de listes imbriquées.

Exemple :

HTML :

```html
<body>

<ol>
    <li>item</li>
    <li>item   
        <ol>
            <li>item</li>
            <li>item</li>
            <li>
                item
                <ol>
                    <li>item</li>
                    <li>item</li>
                    <li>item</li>
                </ol>
            </li>
            <li>item</li>
        </ol>
    </li>
    <li>item</li>
    <li>item</li>
</ol>

<ol>
    <li>item</li>
    <li>item</li>
</ol>

</body>
```

CSS :

```css
ol {
    counter-reset: section;
    list-style-type: none;
}

li::before {
    counter-increment: section;
    content: counters(section,".") " ";
}
```