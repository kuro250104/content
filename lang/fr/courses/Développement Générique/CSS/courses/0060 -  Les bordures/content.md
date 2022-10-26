Ce cours va détailler toutes les propriétés CSS permettant d’ajouter une bordure à un élément HTML, de modifier le type de bordure, d’en modifier l’épaisseur, la couleur, etc.

## Le style de bordure

Avant toute chose, il faut préciser quel style de bordure appliquer à l’élément HTML en question. Pour cela, la propriété ```border-style``` doit être utilisée. 

Cette propriété peut recevoir les valeurs suivantes :

- ```dotted``` : Définit une bordure avec des points
- ```dashed``` : Définit une bordure avec des pointillés
- ```solid``` : Définit une bordure dite solide (avec des traits pleins)
- ```double``` : Définit une double bordure
- ```groove``` : Définit une bordure rainurée en 3D
- ```ridge``` : Définit une bordure striée en 3D
- ```inset``` : Définit une bordure en 3D vers l’intérieur
- ```outset``` : Définit une bordure en 3D vers l’extérieur
- ```none``` : Ne définit aucune bordure
- ```hidden``` : Définit une bordure cachée.

__Remarque__ : Toutes les propriétés CSS dans la suite de ce chapitre ne fonctionnent pas si la propriété ```border-style``` n’est pas définie.

## Taille des bordures 

Le CSS permet de donner des tailles spécifiques aux bordures. Pour ce faire, il suffit d’utiliser la propriété CSS ```border-width```.

Cette propriété peut recevoir des valeurs spécifiques (en px, pt, cm, em, etc.) ou recevoir une des quatre valeurs spécifiques prédéfinies : **thin** (mince), **medium** (moyen) ou **thick** (épais). 

__Rappel__ : la propriété ```border-style``` **doit absolument être définie** avant de pouvoir utiliser n’importe quelle autre propriété relative aux bordures. 

Exemple :

```css
p {
    border-style : solid;
    border-width : 5px;
}

h1 {
    border-style : solid;
    border-width : medium;
}
```

Dans l’exemple ci-dessus, la largeur de la bordure autour du paragraphe est définie à cinq pixels (px), tandis que pour le titre, la largeur de la bordure est définie grâce à la valeur ```medium```.

### Tailles de bordures spécifiques

En plus des valeurs prédéfinies évoquées au point précédent, le CSS permet à la propriété ```border-width``` de définir précisément des tailles pour les bordures d’un élément. 

Cette propriété peut donc recevoir entre 1 (toutes les bordures auront la même épaisseur) et 4 (chaque bordure aura l’épaisseur qui lui sera assignée) valeurs de tailles pour la bordure. Les tailles sont définies dans cet ordre : 

- Bordure **supérieure**
- Bordure de **droite **
- Bordure **inférieure**
- Bordure de **gauche**

Exemple :

```css
body {
    border-style : solid;
    border-width : 4px 2px 3px 1px;
}
```

Dans l’exemple ci-dessus :

- La bordure **supérieure** aura une épaisseur de **4 pixels**.
- La bordure **de droite** aura une épaisseur de **2 pixels**.
- La bordure **inférieure** aura une épaisseur de **3 pixels**.
- La bordure **de gauche** aura une épaisseur de **1 pixel**.

De plus, si la propriété ne reçoit que 2 valeurs :

```css
body {
    border-style : solid;
    border-width : 10px 5px;
}
```

Dans l'exemple ci-dessus :

- Les bordures **supérieure et inférieure** ont une épaisseur de **10 pixels**
- Les bordures **gauche et droite** ont une épaisseur de **5 pixels**

## La couleur des bordures

Que serait un langage de mise en forme s’il ne permettait pas de changer la couleur des bordures ? Le CSS permet justement cela, grâce à la propriété ```border-color```.

Cette propriété, pour définir la couleur à utiliser pour les bordures, peut recevoir 3 types de valeurs :

- Le nom des couleurs en **anglais** : red, green, orange
- Une couleur en **HEX** : #ff0000
- Une couleur utilisant la **valeur RGB** : rgb(255, 255, 255)

Dans les exemples de ce cours, seul le nom anglais des couleurs sera utilisé avec la propriété ```border-color```. Pour savoir comment utiliser les couleurs en HEX ou RGB, voir le cours sur les couleurs en CSS.

Exemple :

```css
p {
    border-style : solid;
    border-color : blue; /* Ici, la bordure sera de couleur bleu */
}
```

### Couleurs spécifiques 

Tout comme la propriété précédente permettait de définir une épaisseur spécifique pour chaque côté de la bordure, ```border-color``` permettait de définir une couleur spécifique pour chaque bordure entourant l’élément HTML.

Cette propriété peut donc recevoir entre 1 (toutes les bordures auront la même couleur) et 4 (chaque bordure aura la couleur qui lui sera assignée) valeurs de couleur pour la bordure. Les tailles sont définies dans cet ordre : 

- Bordure supérieure
- Bordure de droite 
- Bordure inférieure
- Bordure de gauche

Exemple : 

```css
body {
    border-style : dotted;
    border-color : red, blue, green, orange; /* haut rouge, droite bleu, bas vert, gauche orange */
}
```

## Style spécifique pour chaque côté

Dans les deux points précédents, il a été démontré que le CSS permettait aux propriétés ```border-color``` et ```border-width``` de recevoir des valeurs spécifiques pour chaque côté de la bordure entourant un élément HTML. Le CSS permet également cela avec la propriété ```border-style```. Néanmoins, son utilisation varie légèrement des deux autres propriétés citées précédemment. 

Voici comment s’utilise cette propriété pour changer le style de chacun des côtés d’une bordure :

```border-[nom_anglais_du_côté_à_modifier]-style```

Dans la pratique, il existe donc 4 propriétés différentes pour modifier le style d’un côté d’une bordure :

- ```border-top-style``` : modifie le style de la bordure **supérieur**
- ```border-right-style``` : change le style de la bordure de **droite**
- ```border-bottom-style``` : modifie le style de la bordure **inférieure**
- ```border-left-style``` : change le style de la bordure de **gauche**

Exemple :

```css
p {
    border-top-style : solid;
    border-right-style : dashed;
    border-bottom-style : solid;
    border-left-style : dashed;
}
```

### Utilisation de border-style

Plutôt que d’utiliser chacune des 4 propriétés ci-dessus pour changer le style de chacune des bordures, ce qui peut être assez redondant à écrire, CSS permet de changer le style de chacun des côtés individuellement, en utilisant directement la propriété ```border-style```.

Voici, en pratique, comment cela fonctionne :

Si les **4 valeurs** sont précisées, les valeurs de style spécifiées seront attribuées à chaque côté de la bordure, dans cet ordre :

- Bordure **supérieure**
- Bordure de **droite**
- Bordure **inférieure**
- Bordure de **gauche**

Si 3 valeurs sont spécifiées, le style de chaque côté sera modifié comme suit :

```border-style : solid dashed solid``` :

La bordure **supérieure** sera **solid**
Les bordures **droite** et **gauche** seront **dashed**
La bordure **inférieure** sera **solid**

Si **2 valeurs** sont attribuées à la propriété, les styles seront modifiés ainsi :
```border-style : solid dotted``` :

- Les bordures **supérieure** et **inférieure** seront **solid**
- Les bordures **droite** et **gauche** seront **dotted**

Si **une seule valeur** est spécifiée, **toutes les bordures** se verront attribuées le style défini. 

## Propriété raccourcie

Beaucoup de propriétés sont à prendre en considération lorsque des bordures sont ajoutées à un élément HTML et que leurs styles et leurs couleurs doivent être modifiés. 

Afin d’éviter d’utiliser toutes ces propriétés, pour raccourcir le code, pour gagner du temps, mais également pour gagner en lisibilité, le CSS permet d’utiliser une **propriété raccourcie** afin d’appliquer une bordure à un élément HTML, de modifier le style de cette bordure, d’en changer la couleur.

Cette propriété est la suivante : ```border```. Elle prend en compte les valeurs des propriétés suivantes, **dans cet ordre** :

- ```border-width```,
- ```border-style``` (obligatoire),
- ```border-color```.

Exemple :

```css
p {
    border : 5px solid black;
}
```

Dans l’exemple ci-dessus, les paragraphes seront entourés d’une bordure d’une **épaisseur de cinq pixels**, de **style solid** et de **couleur noire**. 

## Propriété raccourcie pour une seule bordure

Enfin, le langage CSS permet d'utiliser la propriété raccourcie pour seulement une seule bordure. Pour ce faire, il faut utiliser la propriété border de cette manière :

```[nom_anglais_du_côté_à_modifier]-border```

Exemple :

```css
p {
    left-border : 3px solid black;
}
```

Dans cet exemple, une bordure de **trois pixels**, de **style solid** et de **couleur noire** sera ajoutée **à gauche** de chaque paragraphe.

## Les bordures arrondies

Afin de styliser les bordures, de les rendre plus "attrayantes", le langage CSS a une propriété permettant d’arrondir les coins des bordures. 

Cette propriété est la suivante : ```border-radius```. Elle reçoit une valeur en pixels précisant le rayon d’arrondi de la bordure. 

Exemple :

```css
body {
    border : 3px solid blue;
    border-radius : 5px; /* Ici, les coins de la bordure seront arrondis avec un rayon de 5 pixels */
}
```

Il est également possible de donner à cette propriété une valeur en %.

Exemple :

```css
body {
    border : 3px solid blue;
    border-radius : 5%; /* Tous les coins seront arrondis avec un rayon de 5 % */
}
```