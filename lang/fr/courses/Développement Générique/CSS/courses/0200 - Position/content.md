La position des éléments est essentielle dans la mise en page d’une page web. C’est ce qui définit tout le design d’un site internet. 

## La propriété position

Afin de gérer le positionnement des éléments, le langage CSS met à disposition la propriété ```position```. 

Cette propriété doit d’abord recevoir une des valeurs suivantes :

- ```static```
- ```relative```
- ```fixed```
- ```absolute```
- ```sticky```

Ensuite, les éléments sont positionnés en utilisant les propriétés CSS suivantes : ```top```, ```left```, ```right```, ```bottom```. Néanmoins, la propriété ```position``` doit d’abord être définie avec une des valeurs listées ci-dessus ; si tel n’est pas le cas, ```top```, ```left```, ```right```, ```bottom``` ne fonctionnent pas.

## La position statique

Les éléments HTML sont, par défaut, placés en position statique (*static*, en anglais). La position de ces éléments **n’est pas modifiable** en utilisant les propriétés haut, bas, gauche, droite. 

Les éléments utilisant ```position: static;``` ne sont pas positionnés de manière particulière. Ils suivent simplement le flux de la page. 

## La position relative

Un élément placé en position relative, en utilisant la propriété ```position : relative;```, est positionné de façon relative par rapport à sa position initiale. 

Utiliser les propriétés haut, bas, gauche, droite sur un élément placé de manière relative ajuste la position de cet élément plus loin que sa position normale. Le vide laissé par un élément placé de manière relative n’est pas comblé par les autres éléments de la page. 

## La position fixe

Un élément HTML placé de façon fixe, en utilisant ```position: fixed;```, ne bougera pas. Cela signifie que même si l’utilisateur fait défiler la page vers le bas, l’élément continuera d’être toujours affiché. L’élément est ensuite positionné en utilisant les propriétés top, bottom, left, right. 

Lorsque la position d’un élément est définie sur ```fixed```, celui-ci reste affiché à l’écran, peu importe la position de l’utilisateur sur la page. De plus, les éléments se situant en dessous sont remontés, comme si l’élément ```fixed``` n’existait pas sur la page. 

## La position absolue

Un élément HTML positionné avec la valeur ```position: absolute;``` sera positionné en fonction de l’élément contenant “positionné” le plus proche. Cependant, si un élément positionné de manière absolu n’a pas de contenant, il sera positionné en fonction de son plus proche élément parent "positionné", ou, à défaut, en fonction de l’élément ```<html>```.

__Remarque__ : Un contenant “positionné” est un élément dont la position est différente de ```static```.

Exemple :

HTML:

```html
<body>

	<div class="contenu">
		<p>
			Je suis un paragraphe contenu dans une div en <code>position: relative;</code>
		</p>
		<div class="premier">
			<p> Je suis un paragraphe dans une div dont la position est <code> position:absolute; </code> . Je suis contenu dans une div de classe contenu dont la position est fixed.</p>
		</div>
	</div>

</body>
```

CSS :

```css
.contenu
{
	position: relative;
	width: 600px;
	height: 200px;
	border: 5px solid red;
}

.premier
{
	position: absolute;
	width: 300px;
	height: 100px;
	right: 0px;
	border: 3px solid red;
}
```

## La position sticky

Un élément HTML dont la position est collée (*sticky*, en anglais) est positionné en fonction de la position de l’utilisateur sur la page. 

En fait, ```position : sticky;``` varie entre ```relative``` et ```fixed```. Tant que l’utilisateur fait défiler la page, l’élément sera en position relative et suivra le défilement de la page jusqu’à ce que l’élément retrouve sa position initiale, auquel cas, il reviendra en position fixe.

Remarque : Internet Explorer ne prend pas en charge la position ```sticky```. En ce qui concerne Safari, il faut rajouter le préfixe ```-webkit-``` pour que la position ```sticky``` fonctionne. Enfin, il faut absolument spécifier une position ```top```, ```bottom```, ```right``` ou ```left``` pour que la position ```sticky``` fonctionne. 

Exemple :

```css
div.exemple {
	position: -webkit-sticky; /* Pour Safari */
	position: sticky; /* L'élément est en position sticky, donc défilera en même temps que la page */
	top: 0; /* L'élément sera en position fixe lorsque l'utilisateur reviendra en haut de la page */
}
```

## Superposition d’éléments

Lorsque les éléments sont positionnés, ils peuvent ensuite être superposés les uns sur les autres. 

La propriété CSS ```z-index``` définit l’ordre d’empilement des éléments, c'est-à-dire, quel élément doit être placé en premier plan, lequel doit être placé derrière le premier élément, etc. 

Un élément peut avoir un ordre d’empilement positif ou négatif. Un élément avec un ordre d’empilement plus élevé sera placé devant un élément avec un ordre d’empilement plus faible. 

Exemple :

```css
.logo {
	position: absolute;
	left: 20px;
	top: 0px;
	z-index: -1; /* Avec un ordre d'empilement définit à -1, le logo sera placé derrière le texte */
}
```