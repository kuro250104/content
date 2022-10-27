Avec le langage CSS, les liens peuvent être stylisés de différentes manières.

## Styliser les liens

Les liens peuvent être stylisés avec n’importe quelle propriété CSS.

Exemple :

```css
a {
	color : blue;
	text-align: center;
	font-style: italic;
}
```

En plus des différentes propriétés utilisables, les liens peuvent être stylisés en fonction de “l’état” dans lequel ils se trouvent. Ci-dessous, la liste des cinq états dans lesquels se trouve un lien :

- ```a:link``` : un lien vierge, pas encore visité 
- ```a:visited``` : un lien que l’internaute a visité
- ```a:hover``` : un lien survolé par la souris
- ```a:active``` : un lien au moment où l’internaute clique dessus
- ```a:focus``` : un lien sélectionné par l’utilisateur à l’aide de son clavier.

__Remarque__ : De façon générale, les éléments ```a``` et les sélecteurs ```a:pseudo-classe``` fonctionnent par paires et sont donc stylisés avec les mêmes règles. Ainsi, ```a``` et ```a:visited``` fonctionnent-ils ensemble et sont ainsi stylisés pareils. Il en va de même avec ```a:hover``` et ```a:focus```.

Lorsque plusieurs “états” de liens sont stylisés, il y a un ordre à respecter :

- ```a:hover``` doit être stylisé après ```a:link``` et ```a:visited```
- ```a:active``` doit être stylisé après ```a:hover```

Exemple :

```css
a:link {
	font-weight : bold; /* Les liens actifs seront mis en gras */	          color : blue; /* Le texte des liens actifs sera de couleur bleu */
}

a:visited {
	font-style: italic; /* Les liens visités seront mis en italique */
}

a:hover {
	background-color: red; /* Au survol de la souris, l'arrière plan des liens sera rouge */
}

a:active {
	color : white; /* Lorsque l'internaute clique sur les liens, ceux-ci seront blancs */
}
```

## Propriété text-decoration

Le langage CSS permet d’enlever le soulignage des liens. Pour ce faire, il faut utiliser la propriété ```text-decoration```.

Cette propriété reçoit une des deux valeurs suivantes :

- ```underline``` : les liens seront soulignés
- ```none``` : les liens ne seront pas soulignés

Exemple :

```css
a:link {
	text-decoration: underline; /* Les liens seront soulignés */
}

a:visited {
	text-decoration: none; /* Les liens visités ne seront pas soulignés */
}
```

## Propriété background-color

La propriété ```background-color``` est utilisée pour changer la couleur d’arrière-plan des liens.

Exemple :

```css
a:link {
	text-decoration : underline; /* Les liens seront soulignés */
	background-color : green;  /* Par défaut, les liens ont un arrière-plan vert */
}

a:visited {
	text-decoration: none; /* Les liens visités ne seront pas soulignés */
	background-color: red; /* Les liens visités ont un arrière-plan rouge */
}
```