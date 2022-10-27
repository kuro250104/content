La propriété CSS ```opacity``` définit la transparence (appelée aussi opacité) d’un élément. Sa valeur varie entre **0.0** et **1.0**. Plus la valeur est faible, plus l’élément est opaque.

## Opacité au survol de la souris

```opacity``` est fréquemment utilisée avec la pseudo-classe ```:hover``` afin de rendre un élément plus opaque au passage de la souris. 

Exemple :

```css
img:hover {
    opacity: 0.5; /* Lorsque la souris survole l'image, cette dernière est rendu plus opaque */
}
```

## Transparence et héritage sur des éléments emboîtés

Lorsque ```opacity``` est utilisée pour rendre opaque l’arrière-plan d’un élément, tous les éléments enfants de cet élément héritent de cette opacité. Cela rend difficile le fait de lire le texte à l’intérieur d’un élément. 

Exemple :

```css
div {
    opacity: 0.5 /* Ici, la div et tous ses éléments enfants se voient appliquer une opacité de 0.5 */
}
```

## Transparence avec RGBA

Afin d’éviter les problèmes d’héritage avec la propriété ```opacity```, le langage CSS permet d’utiliser le RGBA pour définir l’opacité d’un élément. 

Dans le chapitre sur les couleurs en CSS, **RGB** avait été évoqué pour définir une couleur en fonction de sa quantité de rouge, de vert et de bleu. **RGBA** s’utilise de la manière, à ceci près qu’il prend en compte un élément supplémentaire : la valeur **Alpha** (d’où RGBA) permettant de **définir l’opacité d’un élément**.

Lorsque RGBA est utilisé pour définir l’opacité d’un élément, le texte contenu dans cet élément n’est pas impacté.

Exemple :

```css
#titre {
    background: rgba(255, 0, 0, 0.5); /* l'élément div #titre se voit attribuer un arrière-plan rouge avec une transparence de 50% */
}
```