Comme tout langage informatique, le CSS contient un ensemble de règles syntaxiques à respecter. 

En premier lieu, le CSS se compose d’un sélecteur et d’un bloc de déclaration. Le bloc de déclaration commence avec une accolade ouvrante et se termine avec une accolade fermante. 

Ceci est illustré par l’image ci-dessous :

![Représentation des règles syntaxiques du CSS](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/CSS/courses/0010%20-%20Syntaxe/images/image1.jpg)

Le sélecteur est le nom de l’élément HTML à styliser. 

Le bloc de déclaration contient des propriétés CSS suivies de valeurs. Le nom de la propriété CSS est séparé de la valeur assignée par deux points “:” ; chaque couple propriété CSS/valeur est séparé par un point virgule. 

Exemple :

```css
h2 {
    text-align : left;
    color : blue;
    font-size : 16px;
}
```

Dans l’exemple ci-dessus, les règles syntaxiques sont respectées.

h2 est le sélecteur et désigne l’élément HTML à styliser, ici un titre de niveau 2.

Tout de suite après le sélecteur, l’accolade ouvrante marque le début du bloc de déclaration. Dans ce bloc se trouve les différentes propriétés CSS :

- ```text-align``` : left; aligne le titre à gauche
- ```color``` : blue; permet de colorer le titre en bleu
- ```font-size``` : 16px; indique la taille en pixels à donner au titre. Ici, 16 pixels.

Il est important de remarquer que chaque propriété CSS est séparée de la valeur assignée par deux points “:”, et que chaque couple propriété/valeur est séparé par un point-virgule. 

Enfin, le bloc de déclaration se termine par une accolade fermante.