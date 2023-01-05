Le langage CSS permet d’ajouter des animations sans avoir besoin d’utiliser Adobe Flash ni JavaScript.

Une animation permet à un élément de passer graduellement d’un style à un autre. En CSS, pour créer une animation, il est possible de changer des propriétés autant de fois qu’il est jugé nécessaire. 

Pour utiliser les animations en CSS, il faut commencer par déclarer des “images clés” (keyframes, en anglais). Ces keyframes “retiennent” quel style aura un élément à un moment donné. 

## La règle @keyframes

Lorsque du style CSS est déclaré dans un ```@keyframes```, l’élément va graduellement changer d’un style à l’autre à un moment donné. 

Pour qu’une animation fonctionne, il faut lier cette dernière à un élément.

Exemple :

```css
/* Code pour l'animation, qui passera d'un arrière-plan rouge à un arrière-plan jaune */
@keyframes exemple {
	from { background-color: red; }
	to { background-color: yellow; }
}

div {
	width: 100px;
	height: 100px;
	background-color: red;
	animation-name: exemple; /* Ici, l'animation "exemple" déclarée dans le @keyframe est lié à la div */
	animation-duration: 4s; /* L'animation dure 4 secondes */
}
```

__Remarque__ : Pour que l’animation fonctionne, il faut **obligatoirement qu’une durée soit définie** dans la propriété ```animation-duration```. Si tel n’est pas le cas, **l’animation ne se lancera pas**, car la durée par défaut est de 0 seconde.

## Retarder une animation

La propriété CSS ```animation-delay``` permet de retarder le lancement d’une animation. 

Exemple :

```css
div {
	width: 100px;
	height: 100px;
	background-color: red;
	animation-name: exemple;
	animation-duration: 4s; 
	animation-delay: 2s; /* Le navigateur attend 2 secondes avant de lancer l'animation */
}
```

__Remarque__ : Les valeurs négatives sont également prises en compte. Dans un tel cas, l’animation démarrera comme si elle avait déjà été jouée pendant *N* secondes avant le chargement d’une page par exemple. 

## Définir combien de fois une animation doit se lancer

Pour définir le nombre de fois où une animation doit se lancer, il faut utiliser la propriété ```animation-iteration-count```. Cette propriété prend en valeur le nombre de fois que l’animation doit se jouer ; elle peut également prendre la valeur ```infinite```, si l’animation doit se jouer à l’infini.

Exemple :

```css
div {
	width: 100px;
	height: 100px;
	background-color: red;
	animation-name: exemple;
	animation-duration: 4s; 
	animation-delay: 2s;
	animation-iteration-count: 3; /* L'animation se jouera 3 fois */
}
```

## Lancer l’animation dans une direction alternée ou en cycle alterné

La propriété ```animation-direction``` définit si l’animation doit se jouer vers l’avant, vers l’arrière ou en cycles alternés. 

Cette propriété prend une des 4 valeurs suivantes :

- ```normal``` : l’animation se joue normalement, dans l’ordre défini dans le ```@keyframes```. C’est la valeur par défaut. 
- ```reverse``` : L’animation est jouée dans la direction opposée, c'est-à-dire dans l’ordre inverse que celui défini dans la règle ```@keyframes```.
- ```alternate``` : L’animation est jouée dans l’ordre, d’abord, puis dans l’ordre inverse, ensuite. 
- ```alternate-reverse``` : L’animation est d’abord jouée dans l’ordre inverse, puis dans l’ordre correct. 

Exemple :

```css
div {
	width: 100px;
	height: 100px;
	background-color: red;
	animation-name: exemple;
	animation-duration: 4s; 
	animation-direction: reverse; /* L'animation est jouée dans l'ordre inverse */
}
```

## Définir la courbe de vitesse pour une animation 

La propriété ```animation-timing-function``` permet de définir la courbe de vitesse d’une animation. 

Elle reçoit une des 6 valeurs suivantes :

- ```ease``` : Valeur par défaut. L’animation commence lentement, puis continue rapidement puis finit à nouveau lentement. 
- ```linear``` : L’animation a la même vitesse du début à la fin. 
- ```ease-in``` : L’animation a un début lent.
- ```ease-out``` : L’animation a une fin lente.
- ```ease-in-out``` : L’animation a un début et une fin lents.
- ```cubic-bezier(n,n,n)``` : Permet au développeur de définir lui-même la vitesse d’animation au sein de cette fonction.

Exemple :

```css
div {
	width: 100px;
	height: 100px;
	background-color: red;
	animation-name: exemple;
	animation-duration: 4s; 
	animation-direction: reverse;
	animation-timing-function: ease; /* Ici, l'animation a un début lent, puis continue plus rapidement, puis termine lentement */
}
```

## Définir le mode de remplissage pour une animation

En CSS, les animations n’affectent pas le comportement d’un élément HTML avant que le premier **keyframe** soit joué ou après que le dernier **keyframe** soit joué. Cependant, la propriété ```animation-fill-mode``` permet de passer outre cette spécificité.

Cette propriété permet donc de définir un style pour l’élément ciblé par l’animation, lorsque cette dernière n’est pas jouée (avant que l’animation ne commence, avant qu’elle ne se termine, ou les deux).

La propriété ```animation-fill-mode``` peut recevoir une des 4 valeurs suivantes :

- ```none``` : Valeur par défaut. L’animation n’appliquera aucun style à l’élément avant et/ou après que l’animation soit exécutée.
- ```forwards``` : L’élément se verra appliquer le style retenu par la dernière keyframe. Ce style dépend des valeurs données aux propriétés animation-direction et animation-iteration-count. 
- ```backwards``` : L’élément se verra appliquer le style retenu par la première keyframe et ce style est retenu pendant toute la durée de l’animation. Le style défini dépend ainsi de la valeur donnée à animation-direction.
- ```both``` : L’élément se verra appliquer le style à la fois de forwards et backwards et étend les propriétés de l’animation dans les deux directions.

Exemple avec la valeur forwards : 

```css
@keyframes exemple {
	from { top: 20px; background-color: red; }
	to { top: 400px; background-color: yellow; }
}

div {
	width: 100px;
	height: 100px;
	position: relative;
	animation-name: exemple;
	animation-duration: 4s; 
	animation-fill-mode: forwards; /* Ici, la div garde le style appliqué à la dernière keyframe : top 200 pixels et couleur de fond :
	jaune */
}
```

Exemple avec la valeur backwards :

```css
@keyframes exemple {
	from { top: 20px; background-color: red; }
	to { top: 400px; background-color: yellow; }
}

div {
	width: 100px;
	height: 100px;
	position: relative;
	animation-name: exemple;
	animation-duration: 4s; 
	animation-delay: 2s;
	animation-fill-mode: backwards; /* Ici, la div garde le style appliqué à la première keyframe, avant que l'animation ne commence
	(définit par animation-delay: 2s) */
}
```

Exemple avec both :

```css
div {
	width: 100px;
	height: 100px;
	position: relative;
	animation-name: exemple;
	animation-duration: 4s; 
	animation-delay: 2s;
	animation-fill-mode: both; /* Ici, la div garde le style appliqué à la première keyframe, avant que l'animation ne commence
	(définit par animation-delay: 2s), et ensuite, prend le style appliqué à la dernière keyframe, quand l'animation se termine */
}
```

## Propriété raccourcie

Comme pour beaucoup d’autres propriétés, le langage CSS met à disposition une propriété raccourcie pour les animations : ```animation```.

Cette propriété permet de rassembler les 6 propriétés d’animations étudiées dans les points précédents en une seule. 

Elle prend les valeurs des 6 propriétés dans l’ordre suivant :

- ```animation-name```
- ```animation-duration```
- ```animation-timing-function```
- ```animation-delay```
- ```animation-iteration-count```
- ```animation-direction```

Exemple :

```css
div {
	animation: exemple 4s ease 2s 3 reverse;
}
```
