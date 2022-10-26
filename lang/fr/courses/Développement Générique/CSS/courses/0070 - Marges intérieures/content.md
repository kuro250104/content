En CSS, les marges intérieures (padding, en anglais), sont utilisées afin de définir les marges intérieures dont un élément HTML peut bénéficier. 

Pour ce faire, le CSS utilise la propriété ```padding```. Cela permet un contrôle total sur les marges intérieures. 

Ce cours détaillera chacune des propriétés ```padding``` permettant de définir les marges intérieures de chaque côté d’un élément. De plus, ce cours inclut une explication détaillée de la propriété raccourcie. 

## Définir les marges intérieures de chaque côté individuellement

Le CSS utilise une propriété spécifique pour chaque côté d’un élément dont il faut définir les marges intérieures :

- ```padding-top``` : marge intérieure **supérieure**
- ```padding-right``` : marge intérieure **droite**
- ```padding-bottom``` : marge intérieure **inférieure**
- ```padding-left``` : marge intérieure **gauche**

Chacune de ces propriétés peut recevoir la valeur suivante :

- **taille** : une taille de marge intérieure en px, cm, em, pt
- **%** : définit une taille de marge intérieure en % de la largeur de l’élément contenant
- **inherit** : indique que les marges intérieures doivent être héritées de l’élément parent

__Remarque__ : Les valeurs négatives ne sont pas prises en compte.

Exemple :

```css
h1 {
    padding-top : 50px; /* marge intérieure supérieure de 50 pixels */
    padding-right : 30px; /* marge intérieure droite de 30 pixels */
    padding-bottom : 50px; /* marge intérieure inférieure de 50 pixels */
    padding-left : 30px; /* marge intérieure gauche de 30 pixels */
}

p {
    padding-top : 3%; /* marge intérieure supérieure de 3 pourcent */
    padding-left : 5%;
    padding-bottom : 3%;
    padding-right : 5%;
}

p.idee
{
    padding-left : inherit; /* Ici, la marge intérieure gauche du paragraphe de classe idee aura une valeur de 5% si l'élément parent est une balise <p> */
}
```

## Propriété raccourcie

Afin de raccourcir le code, le langage CSS permet l’utilisation de la propriété raccourcie padding, permettant de rassembler les 4 propriétés évoquées dans le point précédent en une seule.

### 4 valeurs

Exemple :

```css
p {
    padding : 4px 3px 4px 6px;
}
```

- La marge intérieure **supérieure** sera de **4 pixels**
- La marge intérieure **droite** sera de **3 pixels**
- La marge intérieure **inférieure** sera également de **4 pixels**
- La marge intérieure **gauche** sera de **6 pixels**

### 3 valeurs

Exemple :

```css
p {
    padding : 3px 7px 4px;
}
```

- La marge intérieure **supérieure** est de **3 pixels**
- Les marges intérieures **gauche** et **droite** sont de **7 pixels**
- La marge intérieure **inférieure** est de **4 pixels**


### 2 valeurs

Exemple :

```css
p {
    padding : 5px 4px;
}
```

- Les marges intérieures **supérieure** et **inférieure** sont de **5 pixels**
- Les marges intérieures **gauche** et **droite** sont de **4 pixels**

### 1 valeur

Exemple :

```css
p {
    padding : 7px;
}
```

- **Toutes les marges intérieures** sont de **7 pixels**

## Marges intérieures et largeur des éléments

Comme évoqué dans un précédent chapitre, la propriété CSS ```width``` permet de définir la largeur de l’aire de contenu d’un élément. L’aire de contenu d’un élément est la portion à l’intérieur des bordures et des marges intérieures et extérieures d’un élément. 

De là, si un élément à une largeur (*width*) spécifique, les marges intérieures définies à cet élément vont être ajoutées à la largeur totale de cet élément. 

La plupart du temps, cela produit un résultat indésirable. 

Exemple :

```css
p {
    width : 200px;
    padding : 30px;
}
```

Dans cet exemple, l’élément **paragraphe** a une **largeur définie à 200 pixels**. Cependant, sa **largeur totale** est de **260 pixels**, car **les 2 marges intérieures gauche et droite de 30 pixels chacune sont ajoutées à la largeur de cet élément**.

Afin de résoudre ce problème et de faire en sorte que l’élément garde sa largeur initiale, peu importe la taille des marges intérieures définies, la propriété CSS ```box-sizing``` doit être utilisée. 

Exemple :

```css
p {
    width : 200px;
    padding : 30px;
    box-sizing : border-box;
}
```

Ici, peu importe la taille des marges intérieures, la largeur de l’élément paragraphe restera de 200 pixels.