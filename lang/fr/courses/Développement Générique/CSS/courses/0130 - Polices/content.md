Choisir la bonne police est important. Cela joue énormément sur l’expérience utilisateur. Il faut choisir une police facile à lire, ainsi que la taille et la couleur correctes pour cette police. 

Ce cours donne quelques explications sur les différents types de polices existantes, puis détaille les différentes propriétés permettant de gérer une police. 

## Généralités

En CSS, les types de polices peuvent être regroupés en 5 familles :

- **Serif** : Ce type de police a de petites barres sur les extrémités de chaque lettre (par exemple : Times New Roman, Georgia, Garamond)

- **Sans-serif** : Ce type de police est “lisse”. Il n’y a pas de barres sur les extrémités de chaque lettre (par exemple : Arial, Verdana, Helvetica)

- Polices **monospaces** : Les lettres de ces polices ont une largeur fixe. Cela donne un style de rendu mécanique (par exemple : Courier New, Lucida Console, Monaco)

- Polices **cursives** : Ces polices imitent les écritures manuscrites (par exemple : Brush Script MT, Lucida Handwriting)

- Les polices **fantasy** : Ces polices sont plutôt décoratives (par exemple : Papyrus, Comic Sans MS)

## La propriété font-family

Pour définir une police, en CSS, il faut utiliser la propriété ```font-family```.

Cette propriété doit contenir **plusieurs noms** de polices, afin que les navigateurs internets plus anciens puissent choisir une police qui convient et qui, malgré tout, reste en cohérence avec le design du site. 

Les polices contenant plusieurs noms (Times New Roman, par exemple), doivent être déclarées dans des guillemets.

Exemple :

```css
p {
	font-family: "Times New Roman", Helvetica, serif; /* Ici, Times new Roman est entre guillemets et plusieurs noms de polices sont déclarées afin qu'un navigateur plus ancien puisse en choisir une compatible */
}
```

## Les polices “web safe”

Les polices dites “web safe” sont des polices universelles, censées être installées sur tous les navigateurs et tous les ordinateurs en général. Il n’existe néanmoins pas de polices 100% “web safe” car il y a toujours une possibilité qu’une police ne soit pas trouvée ou ne soit pas correctement installée. 

C’est pourquoi il est important de constamment déclarer des polices de remplacement dans la propriété ```font-family```, comme indiqué dans le point précédent. En procédant ainsi, le navigateur va vérifier si la première police déclarée est installée ; si ce n’est pas le cas, il va chercher la deuxième police de la liste, et ainsi de suite. 

Remarque : Avant de mettre un site internet en ligne, il est recommandé de le tester sur plusieurs navigateurs et plusieurs appareils afin de voir si les polices déclarées fonctionnent. 

Voici une liste des polices considérées comme “web safe” :

- Arial
- Verdana
- Helvetica
- Tahoma
- Trebuchet MS
- Times New Roman
- Georgia
- Garamond
- Courier New
- Brush Script MT

## La propriété font-style

En CSS, la propriété ```font-style``` est principalement utilisée afin de mettre une police en italique.

Cette propriété reçoit une des valeurs suivantes : 

- ```normal``` : le texte n’est pas mis en italique
- ```italic``` : le texte est mis en italique
- ```oblique``` : le texte est “penché”. En fait, la valeur oblique rend un résultat très similaire à italique, mais la valeur oblique est moins supportée par les navigateurs.

Exemple :

```css
body {
	font-style: oblique; /* Le texte est penché (très similaire à italic mais moins supporté par les navigateurs) */
}
p {
	font-style: italic; /* Le texte est mis en italique */
}
h1 {
	font-style: normal; /* Le texte ne sera pas mis en italique */
}
```

## La propriété font-weight

La propriété ```font-weight``` est principalement utilisée pour mettre du texte en gras. Cette propriété peut recevoir une des valeurs suivantes :

- ```normal``` : le texte n’est pas mis en gras
- ```bold``` : le texte est mis en gras

Exemple :

```css
body {
	font-weight: normal; /* Le texte n'est pas mis en gras */
}
p {
	font-weight: bold; /* Le texte est mis en gras */
}
```

## La propriété font-variant

La propriété ```font-variant``` permet de spécifier si un texte apparaît ou non dans une police contenant des lettres minuscules. 

Dans les polices avec des lettres minuscules, les minuscules sont converties en majuscules. Néanmoins, les majuscules converties en lettres minuscules apparaissent plus petites que leurs tailles normales.

La propriété ```font-variant``` reçoit une des propriétés suivantes :

- ```normal``` : le texte n’est pas mis en minuscule
- ```small-caps``` : le texte est mis en minuscule

Exemple : 

```css
body {
	font-variant: normal; /* Le texte apparaît normalement */
}
p {
	font-variant: small-caps; /* Le texte est mis en minuscules */
}
```

## Définir la taille de la police

Avec la propriété ```font-siz```, le langage CSS permet de définir une taille pour un texte. 

Cette propriété reçoit en valeur un nombre définissant la taille du texte en **px**, **em** ou **%**. La taille du texte peut-être absolue ou relative.

Une taille absolue :

- Défini une taille spécifique pour le texte
- Ne permet à l’utilisateur d’adapter la taille du texte à celle du navigateur
- La taille absolue est principalement utilisée lorsque la taille de l’appareil utilisé pour afficher la page est connue

Une taille relative :

- Adapte la taille en fonction des éléments autour
- Adapte la taille du texte en fonction de la taille de la fenêtre du navigateur

__Remarque__ : Si aucune taille n’est spécifiée, le navigateur affichera par défaut le texte avec une taille de 16 pixels.

Exemple :

```css
body {
	font-size: 12px; /* La taille du texte est définie à 12 pixels */
}
h1 {
	font-size : 1%; /* La taille de l'élément h1 est défini à 1 pourcent */
}
p {
	font-size: 1.3em; /* La taille du texte des paragraphes est définie à 1.3em */
}
```

La taille définie en **em** permet d’adapter la taille du texte à tous les navigateurs, à l’exception des anciennes versions d’Internet Explorer qui présentent le texte trop grand quand la fenêtre est agrandie, et trop petit quand la fenêtre est réduite. 

### Taille du texte adaptable

Il est possible d’utiliser une valeur “universelle” permettant au navigateur d’adapter la taille du texte en fonction du type d’appareil sur lequel la page web est visionnée.

Pour ce faire, il suffit d’attribuer à la propriété ```font-size``` la taille de texte souhaitée, suivie des 2 lettres ```vw``` (pour *viewport width*, largeur du port sur lequel la page est visionnée).

Exemple :

```css
h1 {
	font-size : 10vw; /* La taille de l'élément h1 est définie à 10 en fonction de la taille de l'appareil utilisé pour visionner
	la page web  */
}
```

Viewport est la taille de la fenêtre du navigateur. **1vw = 1% de la largeur du viewport**.

## Les polices Google

Si les polices basiques disponibles en HTML/CSS ne correspondent pas aux design d’un site internet, il est possible d’utiliser les polices mises à disposition par l’entreprise Google. Ces polices sont gratuites, libres de droits et il y en a plus de 1000 disponibles. 

La liste complète des polices mises à disposition par Google est disponible <a href="https://fonts.google.com/" title="liste complète des polices mises à disposition par Google" target="_blank">ici</a>.

### Utiliser les polices Google

Pour utiliser les polices mises à disposition par Google, il suffit de mettre un lien ```stylesheet``` dans le ```<head>``` du code HTML, puis de se référer à cette police dans le code CSS.

L’exemple ci-dessous démontre comment utiliser les polices Google, en utilisant le lien dans le code HTML puis en se référant à cette police dans le code CSS :

```html
<!DOCTYPE html>
<html>
<head>
	<!-- Définition de la police Google (ici, "Lato") -->
	<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Lato">
	<meta charset="utf-8" />
	<style type="text/css">
		body {
			font-family: "Lato", serif; /* La police Google Lato est appelée par la propriété font-family.
			De plus, une police standard est également utilisée au cas où la police google ne peut être utilisée */
		}
	</style>
	<title>Mon site</title>
</head>
<body>

	<p>
		Ceci est un paragraphe utilisant la police Google du nom de Lato
	</p>
</body>
</html>
```

__Remarque__ : Dans le code CSS, le nom de la police Google est mise entre guillemets.

### Utiliser plusieurs polices Google

Il est possible de définir plusieurs polices Google. Pour ce faire, il suffit de séparer le nom des polices par une barre verticale |.

Exemple : 

```html
<!DOCTYPE html>
<html>
<head>
	<!-- Définition de la police Google (ici, "Lato" et "Oswald") -->
	<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Lato|Oswald">
	<meta charset="utf-8" />
	<style type="text/css">
		body {
			font-family: "Lato", serif; /* La police Google Lato est appelée par la propriété font-family.
			De plus, une police standard est également utilisée au cas où la police google ne peut être utilisée */
		}
		h1
		{
			font-family: "Oswald", serif; /* La police Google Oswald est utilisée pour les titres h1, ou la police serif par défaut */
		}
	</style>
	<title>Mon site</title>
</head>
<body>
	<h1>Bienvenue sur mon site internet !</h1>

	<p>
		Ceci est un paragraphe utilisant la police Google du nom de Lato
	</p>
</body>
</html>
```

__Remarque__ : Utiliser de multiples polices Google peut ralentir le chargement de la page web. 

### Styliser les Google Fonts

Styliser une police Google se fait de la même manière qu’une police normale. 

Exemple :

```html
<!DOCTYPE html>
<html>
<head>
	<!-- Définition de la police Google (ici, "Lato" et "Oswald") -->
	<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Lato">
	<meta charset="utf-8" />
	<style type="text/css">
		body {
			font-family: "Lato", serif; /* La police Google Lato est appelée par la propriété font-family.
			De plus, une police standard est également utilisée au cas où la police google ne peut être utilisée */
			font-size: 12px; /* La police Lato a une taille de 12 pixels */
		}
	</style>
</head>
```

## Appairage des polices

### Règles de l’appairage

Afin d’avoir un design cohérent, il est important de définir des polices cohérentes. Voici les règles pour bien combiner des polices entre elles :

1. Les polices doivent être complémentaires. Il est toujours plus sûr de trouver des polices qui se complètent entre elles. Une bonne combinaison devrait donner un résultat harmonieux, sans que les polices soient ni trop similaires, ni trop différentes. 
2. Utiliser les “superfamilles” de polices. Il existe des polices qui ont été déclinées en plusieurs “styles” afin de pouvoir l’utiliser de manière harmonieuse sans prendre trop de risque d’un point de vue design (exemple : la superfamille Lucida : Lucid Sans, Lucida Serif, etc.
3. Le contraste fonctionne bien. Mettre deux polices du même type peut parfois créer des conflits. Un contraste très connu est donc d’associer une police de type **sans-serif** avec une police de type **serif**.
4. Ne choisir qu’une police principale. Cela établira une hiérarchie sur la page. 

## Propriété raccourcie

Comme pour beaucoup d’autres propriétés, afin de rendre le code plus lisible et de gagner du temps, le langage CSS permet d’utiliser une propriété raccourcie pour gérer les polices.

Cette propriété est ```font``` et prend comme valeur un ou plusieurs, voire l’ensemble, des items ci-dessous :

- ```font-style```
- ```font-variant```
- ```font-weight```
- ```font-size```
- ```font-family```

__Remarque__ : Les valeurs de font-value et font-family doivent obligatoirement être déclarées. Si ce n’est pas le cas, le navigateur leur attribuera leurs valeurs par défaut. 

Exemple :

```css
body {
	font: italic bold 20px "Times New Roman", Times, serif;
}
```