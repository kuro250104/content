La propriété ```border-radius``` permet de définir le rayon du coin d’un élément. Cette propriété permet de créer des coins arrondis pour un élément.

## La propriété border-radius

Cette propriété est en fait le raccourci des propriétés ```border-top-left-radius```, ```border-top-right-radius```, ```border-bottom-left-radius```, ```border-bottom-right-radius```.

La propriété raccourcie ne reçoit qu’une valeur : le nombre de pixels de rayon pour arrondir les angles. 

Exemple :

```css
img {
    border-radius: 7px;
}
```

## Définir l’arrondi pour chaque coin

La propriété raccourcie border-radius peut également recevoir 1 à 4 valeurs afin de définir un arrondi pour chaque coin.

### 4 valeurs

Soit l'exemple suivant :

```css
div {
    border-radius: 10px 7px 15px 5px;
}
```

Avec 4 valeurs, l’arrondi de chaque coin vaut, dans cet ordre, les valeurs suivantes : coin supérieur gauche 10px, coin supérieur droit 7 px, coin inférieur gauche 15px, coin inférieur droit 5px.

### 3 valeurs

Soit l'exemple suivant :

```css
div {
    border-radius: 15px 8px 10px;
}
```

Le coin supérieur gauche est à 15px, le coin supérieur droit et le coin inférieur gauche sont à 10px et le coin inférieur droit vaut 10px.

### 2 valeurs

Soit l'exemple suivant :

```css
div {
    border-radius: 10px 8px;
}
```

Les coins supérieurs gauche et droit valent 10px et les coins inférieurs gauche et droit valent 8px

### 1 valeur

Soit l'exemple suivant :

```css
div {
    border-radius: 7px;
}
```

Les quatre coins ont un rayon d’arrondi définit à 7px.