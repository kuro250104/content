En CSS, les sélecteurs sont utilisés afin de désigner l'élément HTML à styliser. Les sélecteurs sont divisés en quatre catégories. 

Ce cours détaille chacune de ces catégories.

## Les sélecteurs simples

Les sélecteurs simples désignent un élément HTML, un ```id``` ou une ```class```.

### Les sélecteurs HTML

Les sélecteurs HTML utilisent le nom de l’élément HTML à styliser. Pour les utiliser, il n’y a pas de syntaxe particulière à respecter ; il suffit simplement d’écrire le nom de l’élément HTML suivi de l’accolade ouvrante. 

Exemple : 

```css
h2 {
    color : green;
}
```

Dans cet exemple, le sélecteur h2, désigne l’élément HTML ```<h2>```. ```color : green;``` permet de mettre le titre en vert.

### Les sélecteurs id

Ces sélecteurs permettent de ne styliser que l'élément de la page HTML portant le nom de l’identifiant (```id```) indiqué.

Les ```id``` sont uniques. Dans un document HTML, il ne peut pas y avoir deux éléments avec le même nom d’id. 

Pour styliser un id en CSS, il suffit d’utiliser le signe ```#``` suivi du nom de l’id.

Exemple :

```css
#firstLetter {
    font-weight : bold;
    font-size : 14px;
}
```

- ```#firstLetter``` correspond à ```id="firstLetter"``` dans le fichier HTML. 
- ```font-weight : bold;``` permet de mettre l’élément désigné en gras.
- ```font-size : 14px;``` donne une taille de 14 pixels à l’élément.

L’exemple ci-dessus permet donc de créer une lettrine en mettant la première lettre du premier paragraphe en gras.

### Les sélecteurs de classe

Ce sélecteur permet de styliser les éléments de la page HTML portant le nom d’une classe. Dans un document HTML, cela correspond à l’attribut class.

Contrairement aux id, il peut y avoir plusieurs éléments, dans un document HTML, portant le même nom de classe. 

En CSS, pour styliser une classe, il faut simplement utiliser le . suivi du nom de la classe. 

Exemple : 

```css
.important {
    font-size : bold;
}
```

```.important``` correspond à l’attribut HTML ```class=”important”```.

Ainsi, dans l’exemple ci-dessus, tous les éléments HTML ayant l’attribut ```class=”important”``` seront mis en gras. 

### Le sélecteur universel

Si tous les éléments d’une page HTML doivent avoir le même style, il est possible d’utiliser le sélecteur universel ```*```.

Exemple :

```css
* {
    font-color : red;
}
```

Ici, tous les éléments de la page seront de couleur rouge.

### Les sélecteurs groupés

Si plusieurs éléments d’une page HTML doivent avoir le même style, il est possible de les regrouper. Cela permet de réduire le code et d'éviter les répétitions inutiles de code. 

Pour cela, il suffit de séparer les sélecteurs par des virgules. 

Exemple :

```css
h1, h2 {
    font-weight : bold;
}
```

Dans cet exemple, tous les titres de niveau 1 et de niveau 2 seront en gras. Les sélecteurs ```h1``` et ```h2``` sont séparés par des virgules. Cela permet de regrouper le code et éviter une répétition de code inutile. 

## Les combinateurs

### Les sélecteurs de voisin direct

Le signe + permet de sélectionner un élément HTML qui suit directement un élément donné.

Exemple :

```css
div + p {
    text-align : center;
}
```

Dans l’exemple ci-dessus, c’est le paragraphe qui suit directement l’élément ```<div>``` qui est centré.

### Les sélecteurs de voisins

Pour sélectionner des éléments qui suivent un autre élément et qui ont le même parent, il faut utiliser ```~```.

Exemple :

```css
p ~ span {
    color : red;
}
```

Dans cet exemple, tous les éléments ```<span>``` qui suivent un ```<p>``` et qui ont le même parent seront de couleur rouge. 

### Les sélecteurs d’éléments enfants

Les sélecteurs d’éléments enfants (```><```) permettent de sélectionner des éléments qui sont les enfants directs d’un élément donné. 

Exemple :

```css
div > h3 {
    font-size : 10px;
}
```

Ici, tous les titres de niveau trois descendant directement d’une ```<div>``` sont sélectionnés et leur taille est défini à 10 pixels. 

### Les sélecteurs d’éléments descendants

Le sélecteur d’éléments descendants permet de sélectionner tous les éléments descendant d’un élément donné. 

Pour ce faire, il suffit d’utiliser “``` ```“ (espace).

Exemple :

```css
div p {
    text-align : justify;
}
```

Dans cet exemple, tous les paragraphes ```<p>``` descendants d’une ```<div>``` sont justifiés. 

## Les pseudos-classes

Les pseudos classes sont des mots-clés qui permettent de définir l’état spécifique d’un élément. 

Une pseudo classe respecte la syntaxe suivante : ```sélecteur:mot-clé```.

Par exemple, si les liens doivent être en italique au passage de la souris, il faut utiliser une pseudo classe :

```css
a:hover {
    font-style : bold;
}
```

Il existe de nombreuses autres pseudos-classes qui sont détaillées dans le cours dédié à ce sujet.

## Les pseudos-éléments

Les pseudos-éléments sont des mots-clés qui, ajoutés à un sélecteur, permettent de modifier le style d’un élément qui n’est pas défini en HTML. 

Il est important de noter qu’il ne peut y avoir qu’un seul pseudo-élément dans un sélecteur. 

Un pseudo-élément s’écrit comme suit : ```sélecteur::mot-clé```.

Exemple : 

```css
p::first-line {
    text-transform : uppercase;
}
```

L’exemple ci-dessus met la première ligne de chaque paragraphe en majuscule. 

Il existe de nombreuses autres pseudos-éléments qui sont détaillées dans le cours dédié à ce sujet.