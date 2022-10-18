Bien que cette méthode ne soit que rarement utilisée de nos jours et fortement déconseillée, le langage HTML permet d’inclure du style directement dans les balises HTML. 

## Attribut style

L’attribut **style** permet d’inclure du code CSS directement au sein du HTML, dans n’importe quelle balise, sans passer par un fichier tiers. Quelques exemples vous sont présentés ci-dessous, mais référez vous aux cours sur le CSS afin de mieux cerner l’étendue des possibilités.

L’utilisation de cet attribut est assez simple : la **propriété CSS** est déclarée entre les guillemets, suivie de **deux points** (:) suivi de la **valeur** à attribuer à cette propriété, suivi d’un **point virgule** (;).

Concrètement, voici la syntaxe de l’attribut style :

``` html
<h1 style="propriété-CSS: valeur;">
```

Exemple : 

``` html
<body>
    <h1 style="background-color: red;">
        Titre du document
    </h1>
</body>
```

Dans cet exemple, le titre se voit définir un arrière plan de couleur rouge. 

## Couleur du texte

Pour définir la couleur d’un paragraphe, il faut utiliser la propriété ```color```, suivie du nom (en anglais) de la couleur à attribuer au paragraphe.

Exemple :

``` html
<p style="color: red";>Je suis un paragraphe</p>
```

## Polices

Grâce à la propriété ```font-family```, il est également possible de définir la police à utiliser pour un paragraphe. Cette propriété reçoit en valeur le nom de la police à utiliser. 

Exemple :

``` html
<p style="font-family:courier;">Je suis un paragraphe</p>
```

## Taille du texte

La propriété ```font-size``` définit la taille de la police d’un élément. Cette propriété prend en valeur la taille de la police (principalement en **pt** ou en pixels (**px**)).

``` html
<p style="font-size:14pt;">Je suis un paragraphe</p>
```

Dans cet exemple, la police a une taille définie à 14.

## Alignement du texte

Pour définir l’alignement d’un texte, la propriété ```text-align``` doit être utilisée. Cette propriété reçoit une des 4 valeurs suivantes :

- **left** : le texte est aligné à gauche
- **center** : le texte est centré
- **right** : le texte est aligné à droite
- **justify** : le texte est justifié

Exemple :

``` html
<p style="text-align:center;">Je suis un paragraphe</p>
```