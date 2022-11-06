De manière générale, il y a deux types de barres de navigation (communément appelées “menu”) sur un site web. Une barre de navigation verticale et/ou une barre de navigation horizontale. 

Un menu facile à utiliser et attrayant est un important pour un site web. Le langage CSS permet de transformer un menu HTML “brut” en une barre de navigation.

Ce chapitre montre pas à pas comment créer une barre de navigation horizontale et une barre de navigation horizontale. 

## Code de base pour une barre de navigation

Un menu est avant tout une liste de liens menant vers les différentes pages d’un site web. Pour commencer, il faut donc créer une liste de liens en HTML :

```html
<nav>
    <ul>
        <li><a href="page1.html" title="Lien 1">Lien 1</a></li>
        <li><a href="page2.html" title="Lien 2">Lien 2</a></li>
        <li><a href="page3.html" title="Lien 3">Lien 3</a></li>
        <li><a href="page4.html" title="Lien 4">Lien 4</a></li>
        <li><a href="page5.html" title="Lien 5">Lien 5</a></li>
    </ul>
</nav>
```

Voici, ensuite, le code CSS de base pour la création d’une barre de navigation :

```css
nav ul {
	list-style-type: none; /* Les puces sont enlevées */
	padding: 0;
	margin: 0; /* padding et margin sont définis à 0 afin de retirer les réglages par défaut du navigateur */
}
```

## Barre de navigation verticale

### Styliser les liens

Pour commencer la création d’un menu vertical, il faut commencer par styliser les ```<a>``` de la barre de navigation. Pour ce faire, en plus du code précédent, il faut ajouter le code CSS suivant :

```css
li a {
	display: block; /* Disposition en block afin que les liens soient les uns en-dessous des autres */
	width: 60px; /* Largeur définie à 60 pixels */
}

li a:visited {
    color: red;
    display: block; /* Disposition en block afin que les liens soient les uns en-dessous des autres */
	width: 60px; /* Largeur définie à 60 pixels */
}
```

__Remarque__ : Afin d’avoir une cohérence dans le design, pour s’assurer que le style ne change pas une fois que l’utilisateur a cliqué sur le lien, il faut rajouter ```li a:visited```.

### Changer l’arrière-plan au survol de la souris

Pour changer la couleur d'arrière-plan d’un lien lorsque celui-ci est survolé par la souris, la pseudo-classe ```:hover``` doit être utilisée.

__Remarque__ : Pour que le style reste le même lorsqu’il est survolé, que l’internaute utilise sa souris ou son clavier pour naviguer, ```a:hover``` est toujours accompagné de ```a:focus```.

Exemple :

```css
ul {
	list-style-type: none;
	padding: 0;
	margin: 0;
	width: 200px;
	background-color: #F5F5F5; /* Couleur blanc cassé */
}

li a {
	display: block; /* Disposition en block afin que les liens soient les uns en-dessous des autres */
	width: 60px; /* Largeur définie à 60 pixels */
	color: black;
	padding: 8px 16px;
	text-decoration: none; /* Le soulignage des liens est retiré */
}

li a:hover, li a:focus {
	background-color: grey; /* Au survol des liens, leur arrière-plan devient gris */
}
```

### Active pour le lien courant 

Dans la création d’un menu, la pseudo-classe :active, appliquée sur un lien, permet d’indiquer à l’utilisateur sur quelle page il se trouve. 

Pour ce faire, il faut ajouter le code suivant au code ci-dessus :

```css
li a:active {
	background-color: green; /* Le lien de la page consultée a un arrière-plan vert */
}
```

### Centrer les liens et ajouter des bordures

Pour centrer les liens, il faut utiliser le code ```text-align: center;``` sur les éléments de type ```<a>``` ou ```<li>```.

Pour ajouter une bordure autour du menu, il faut utiliser la propriété ```border``` sur le ```<ul>```. Ensuite, pour ajouter des bordures sous chaque lien, il faut utiliser ```border-bottom``` sur chaque ```<li>```. 

__Remarque__ : Pour éviter que le dernier lien de la barre de navigation ait 2 bordures (celle du ```<ul>``` et celle du ```<li>```), le pseudo-élément ```::last-child``` est utilisé afin d’indiquer que le dernier ```<li>``` n’a pas de bordure inférieure. 

Exemple :

```css
ul {
	border: 1px solid black; /* Une bordure est appliquée au pourtour de la barre de navigation */
}

ul a {
	text-align: center; /* Le texte des liens est centré */
}

ul li {
	border-bottom: 1px solid black; /* Une bordure inférieure est ajoutée sous chaque <li> */
}

ul li::last-child {
	border-bottom: none; /* Pour le dernier <li>, aucune bordure inférieure n'est appliquée */
}
```

## Barre de navigation horizontale

En CSS, il existe 2 moyens de créer une barre de navigation horizontale : soit en utilisant la propriété ```display: inline```, soit en utilisant ```float```.

### Utilisation de inline

Un des deux moyens courants de créer un menu horizontal, est de définir les ```<li>``` en ```inline```.

Pour ce faire, il faut ajouter le code suivant à celui utilisé en début de cours :

```css
ul li {
	display: inline;
}
```

### Utilisation de float

L’autre moyen de rendre un menu horizontal est d’utiliser la propriété ```float``` sur les éléments ```<li>```. Ensuite, il suffit de spécifier une mise en page pour les liens ```<a>``` du menu.

Exemple :

```css
ul li {
	float: left;
}

ul a {
	/* Disposer les liens en block permet de définir les marges, etc. */
	display: block;
	padding: 8px;
	color: grey;
}
```

__Remarques__ :

- Pour avoir une barre de navigation avec un arrière-plan défini, utiliser background-color sur le ```<ul>``` et non pas sur les ```<a>```, sinon ce sera seulement l’arrière-plan de liens qui sera coloré.
- Les pseudo-classes et pseudo-éléments évoqués pour la création du menu vertical sont également utilisables pour styliser la barre de navigation horizontale.

Il est également possible d’utiliser la propriété flex afin de réaliser un menu horizontal. Cette propriété est entièrement détaillée dans un cours spécifique.

## Ou encore...

Une autre possibilité est aujourd'hui très largement utilisée dans le positionnement des menus : le Flexbox. Référrez-vous au cours le concernant pour vous mettre à jour !