Les pseudo-éléments sont utilisés pour cibler une partie d’un élément.

Par exemple, les pseudo-éléments sont utilisés pour styliser la première lettre ou la première ligne d’un élément paragraphe, ou encore pour insérer du contenu avant ou après un autre contenu. 

## Syntaxe

Voici la syntaxe d’un pseudo-élément :

```css
selecteur::pseudo-element {
    propriété: valeur;
}
```

## Le pseudo-élément ::first-line

Ce pseudo-élément est utilisé pour styliser la première ligne d’un paragraphe. 

__Remarque__ : ```::first-line``` ne s’applique qu’à des **éléments de type block**.

Les propriétés suivantes s’utilisent avec ce pseudo-élément :

- ```font properties```
- ```color properties```
- ```background properties```
- ```word-spacing```
- ```letter-spacing```
- ```text-decoration```
- ```vertical-align```
- ```text-transform```
- ```line-height```
- ```clear```

Exemple :

```css
p::first-line {
    text-transform: uppercase; /* La première ligne des paragraphes est mise en majuscules */
}
```

## Le pseudo-élément ::first-letter

```::first-letter``` s’utilise pour styliser la première lettre d’un paragraphe.

Ci-dessous, la liste des propriétés utilisables avec ```::first-letter``` :

- ```font properties```
- ```color properties ```
- ```background properties```
- ```margin properties```
- ```padding properties```
- ```border properties```
- ```text-decoration```
- ```vertical-align (seulement si float est définit à none)```
- ```text-transform```
- ```line-height```
- ```float```
- ```clear```

Exemple :

```css
p::first-letter {
    padding-left: 10px; /* La première lettre sera décalée de 10 pixels sur la droite pour créer un alinéa
}
```

## Pseudo-éléments et classes CSS

Les pseudos-éléments peuvent être associés à des classes CSS.

Exemple :

```css
p.quote::first-letter {
    text-transform: uppercase; /* La première lettre des paragraphes de classe "quote" est mise en majuscule */
}
```

## Combiner les pseudo-éléments

Plusieurs pseudo-éléments peuvent être utilisés. Pour ce faire, il suffit de les déclarer dans deux blocs CSS différents. 

Exemple :

```css
p::first-line {
    text-transform: uppercase;
}

p::first-letter {
    color: red;
}
```

## Le pseudo-élément ::before

```::before``` s’utilise pour insérer du contenu **avant** un autre contenu. 

Exemple :

```css
h3::before {
    content: url("image.jpg"); /* Une image est insérée avant le titre de niveau 3 */
}
```

## Le pseudo-élément ::after

Comme ```::before```, le pseudo-élément ```::after``` s’utilise pour insérer du contenu après un autre contenu. 

Exemple :

```css
h3::after {
    content: url("image.jpg");
}
```

## Le pseudo-élément ::marker

```::marker``` permet de sélectionner les marqueurs d’un élément. Pour des items d’une liste, par exemple, cela permet de sélectionner le ```<li>``` d’un item de la liste. 

Exemple :

```css
::marker {
    color: blue; /* Les puces de la liste sont de couleur bleu */
}
```

## Le pseudo-élément ::selection

```::selection``` permet d’appliquer un style particulier à un élément sélectionné par l’utilisateur - avec la souris, par exemple.

Seules les propriétés suivantes sont utilisables avec ```::selection``` :

- ```color```
- ```background```
- ```cursor```
- ```outline```

Exemple :

```css
::selection {
    background-color: red; /* Lorsqu'une partie du document est sélectionnée par l'utilisateur, l'arrière-plan sera de couleur rouge
}
```

__Remarque__ : Les pseudo-éléments ```::marker``` et ```::selection``` ont cette particularité de pouvoir être utilisés sans marqueur avant.