En CSS, les marges extérieures (*margin*, en anglais), sont utilisées afin de définir les marges extérieures dont un élément HTML peut bénéficier. 

Pour ce faire, le CSS met une propriété à disposition : ```margin```. Cela permet un contrôle total sur les marges extérieures. 

Ce cours détail l’ensemble des propriétés de type ```margin``` utilisables pour gérer les marges extérieures d’un élément, ainsi que les valeurs ```auto``` et ```inherit```.

## Définir les marges extérieures de chaque côté individuellement 

Le CSS met à disposition des propriétés spécifiques pour définir les marges extérieures de chaque côté, individuellement, d’un élément HTML :

- ```margin-top``` : définit la marge extérieure supérieure
- ```margin-right``` : définit la marge extérieure droite
- ```margin-bottom``` : définit la marge extérieure inférieure
- ```margin-left``` : définit la marge extérieure gauche

Chacune de ces propriétés peut recevoir une des valeurs suivantes :

- ```auto``` : le navigateur calcule lui-même les marges extérieures
- ```taille``` : une taille de marge extérieure en px, pt, cm, em
- ```%``` : une taille de marge en pourcentage de la largeur de l’élément contenant
- ```inherit``` : indique que les marges extérieures doivent être héritées de l’élément parent

__Remarque__ : Les valeurs négatives sont autorisées et prises en compte.

Exemple : 

```css
p {
    margin-top : 20px; /* Marge extérieure supérieure de 20 pixels */
    margin-right : 400px; /* Marge extérieure droite de 400 pixels */
    margin-bottom : 30px; /* Marge extérieure inférieure de 30 pixels */
    margin-left : 50px; /* Marge extérieure gauche de 50 pixels */
}

h1 {
    margin-top : 20%; /* Marge supérieure extérieure de 20 pourcent */
    margin-right : auto; /* Le navigateur calcul lui-même la marge      extérieure droite */
    margin-bottom : 20%;
    margin-left : auto;
}

p.quote {
    margin-top : inherit; /* La marge extérieure supérieure des paragraphes de classe quote sera de 20 pixels car ils héritent de la valeur de margin-top de l'élément parent p */
    margin-right : inherit;
}
```

## Propriété raccourcie

Comme pour beaucoup d’autres propriétés, le CSS permet d’utiliser la propriété raccourcie ```margin``` afin de rassembler les 4 propriétés évoquées au point précédent en une seule. Cela permet de raccourcir le code, de le rendre plus clair, plus lisible et de gagner du temps. 

### Si la propriété reçoit 4 valeurs

Exemple : 

```css
p {
    margin : 20px 400px 30px 50px;
}
```

- La marge extérieure **supérieure** est de **20 pixels**
- La marge extérieure **droite** est de **400 pixels**
- La marge extérieure **inférieure** est de **30 pixels**
- La marge extérieure **gauche** est de **50 pixels**

### Si la propriété reçoit 3 valeurs

Exemple : 

```css
p {
    margin : 20px 250px 40px;
}
```

- La marge extérieure **supérieure** est de **20 pixels**
- Les marges extérieures **gauche** et **droite** sont de **250 pixels** chacune
- La marge extérieure **inférieure** est de **40 pixels**

### Si la propriété reçoit 2 valeurs

Exemple : 

```css
p {
    margin : 20px 250px;
}
```

- Les marges extérieures **supérieures** et **inférieures** sont de **20 pixels** chacune
- Les marges extérieures **gauche** et **droite** sont de **250 pixels** chacune

### Si la propriété reçoit 1 valeur

Exemple : 

```css
p {
    margin : 10px;
}
```

- **Toutes les marges** extérieures sont de **10 pixels**

## La valeur Auto

Le langage CSS permet d’assigner la valeur ```auto``` à la propriété raccourcie. Grâce à cela, l’élément sera automatiquement centré horizontalement au sein de son conteneur. 

Cela fonctionne de la manière suivante : l’élément HTML va prendre la largeur spécifiée, tandis que l’espace restant sera divisé en deux, de manière égale, entre les marges extérieures gauche et droite. 

Exemple :

```css
p {
    width : 400px;
    margin : auto; /* Les paragraphes seront automatiquement centrés en fonction de l'espace restant */
}
```

## La valeur inherit

Exemple : 

```css
div {
    margin-right : 250px;
}

p.citation {
    margin-right : inherit;
}
```

Dans cet exemple, le paragraphe de classe citation hérite de la valeur attribuée à ```margin-right``` de l'élément parent ```div``` et prend donc comme valeur **250px**.