Pour insérer la valeur d’une variable, en CSS, la fonction ```var()``` est utilisée. 

Les variables CSS ont accès au DOM (Document Object Model - le modèle Objet d’un document). Cela signifie que les variables peuvent être modifiées en JavaScript et ou bien encore basées sur les media queries. Cela donne également la possibilité de définir si une variable est locale (cela signifie qu’elle ne peut être modifiée que dans le programme actuel) ou si elle est globale (permettant de modifier la variable dans d’autres programmes).

Généralement, les variables CSS sont utilisées pour les couleurs. Quand il s’agit de définir une couleur, plutôt que de l’écrire encore et encore dans la feuille de style, cette couleur est stockée dans une variable et est utilisée encore et encore. D’autres utilisations sont bien évidemment possibles : gestion des polices d’écritures, de tailles, de marges, etc.

## Manière traditionnelle 

Habituellement, les couleurs sont définies comme suit :

```css
body {
	background-color : rgb(255, 9, 155);
}

h1 {
	background-color: orange;
	color: rgb(255, 9, 155);
}

div p {
	background-color: rgb(255, 9, 155);
}
```

## Syntaxe

La syntaxe de la fonction ```var()``` est la suivante :

```css
var(nom, valeur);
```

Le **nom** de la variable est **obligatoire**. La **valeur** est **optionnelle**. 

__Remarque__ : Le nom d’une variable CSS doit obligatoirement commencer par deux tirets (--) et est sensible à la casse, ce qui veut dire que si le nom d’une variable est en majuscule, il faudra, par la suite, toujours l’écrire en majuscule lorsqu’elle sera réutilisée. 

## Fonctionnement de var()

Comme dit dans l’introduction, une variable CSS peut avoir une portée locale globale. 

Une variable avec une **portée locale** ne peut être (ré)utilisée que dans le **sélecteur dans lequel elle est déclarée** ; tandis qu’une variable avec une **portée globale** est (ré)utilisable dans **tout le document CSS**.

Pour créer une variable globale, il faut la déclarer au sein du sélecteur ```:root```. Ce sélecteur désigne l’élément racine du document. 

Pour créer une variable locale, il suffit de la déclarer dans le sélecteur au sein duquel elle sera utilisée.

Exemple :

```css
:root {
	--color: rgb(255, 9, 155); /* Création de la variable color à portée globale */
}

body {
	background-color : var(--color);/* Utilisation de la variable globale --color) */
}

h1 {
--second-color : orange; /* Création de la variable à portée locale --second-color */
	background-color: var(--second-color); /* Utilisation de la variable locale --second-color */
	color: var(--color);
border-top: 1px solid var(--second-color);
}

div p {
	background-color: var(color);
}
```

Il y a deux avantages à utiliser les variables :

- Cela rend le code plus lisible
- Cela permet de simplement changer une couleur, par exemple. En effet, si la couleur doit changer, il suffit de changer sa valeur dans la déclaration de la variable, et elle sera changée automatiquement partout où la variable n’a pas été utilisée

## Outrepasser les variables

Dans le point précédent, il est expliqué que les variables globales sont utilisables dans tout le document CSS, tandis que les variables locales ne sont utilisables que dans le sélecteur dans lequel elles ont été déclarées. 

Cependant, il est parfois nécessaire, pour un sélecteur particulier, de devoir changer la valeur de la variable globale. Ceci est faisable en déclarant à nouveau la variable dans le sélecteur en question et de l’utiliser au sein de ce sélecteur. 

Exemple :

```css
:root {
	--color: blue;
}

body {
	background-color: var(--color); /* Ici, la variable --color vaut "blue" */
}

button {
	--color: orange; /* Déclaration de la variable --color afin de l'utiliser seulement dans ce sélecteur */
	background-color: var(--color); /* Ici, la variable --color vaut "orange" */
	border: 3px solid var(--color);
}

h1 {
	background-color: var(--color); /* Ici, la variable --color vaut de nouveau "blue" */
}
```