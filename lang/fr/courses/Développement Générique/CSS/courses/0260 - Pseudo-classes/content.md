Une pseudo-classe est utilisée pour définir l’état spécifique d’un élément. Par exemple, on peut l’utiliser pour :

- Styliser un élément quand la souris clique dessus
- Styliser les liens visités et non visités
- Styliser un élément quand le curseur est mis dans un champ de texte

## Syntaxe

Voici la syntaxe d’une pseudo-classe :

```css
selecteur:pseudo-classe {
    propriété : valeur;
}
```

## Pseudo-classes et classes CSS

Les pseudo-classes peuvent se combiner avec les classes CSS.

Exemple :

```css
div.xy:hover {
    color: blue;
}
```

## Survol d’une <div>

Les pseudo-classes permettent également de styliser une ```<div>``` au survol de la souris. Pour ce faire, il faut utiliser la pseudo-classe ```:hover```.

Exemple :

```css
div:hover {
    background-color: grey; /* Au survol de la souris, l'arrière-plan de la div est de couleur grise */
}
```

## Survol de la souris pour afficher du texte

Les pseudo-classes, de manière générale, et ```:hover``` plus particulièrement permettent aussi de faire apparaître des éléments lors du survol de la souris. 

Exemple :

```css
p {
    display: none;
}

div:hover p {
    display: block; /* Au survol de la souris sur le div, les paragraphes s'affichent */
}
```

## La pseudo-classe :first-child

La pseudo-classe ```:first-child``` désigne un élément qui est le premier enfant d’un élément parent.

Exemple :

```css
div p:first-child {
    background-color: grey; /* Le premier paragraphe enfant de la div a l'arrière-plan gris */
}
```

## La pseudo-classe :lang

La pseudo-classe ```:lang``` permet de définir des règles particulières pour différentes langues (lang pour *language* signifiant *langage* en anglais) 

Exemple :

```html
<!DOCTYPE html>
<html>
<head>
    <style type="text/css">
        q:lang(fr) {
            quotes: "<<" ">>"
        }
    </style>
    <title>Mon site</title>
</head>
<body>
    <p>
        Voici une citation en français : <q lang="fr"> citation avec :lang </q>
    </p>
</body>
</html>
```

