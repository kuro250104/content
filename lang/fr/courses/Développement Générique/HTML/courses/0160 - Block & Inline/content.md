Chaque élément HTML a un niveau d’affichage qui lui est attribué par défaut. Ces niveaux influencent l’affichage des éléments par le navigateur et sont très importants lorsque le développeur commence à faire le design d’un site web.

## Block-level

Les éléments dits **block level**, comme leur nom l’indique, sont affichés comme des blocs par le navigateur. Cela signifie que chaque élément de type **block** s’affiche l’un en dessous de l’autre, prenant toute la largeur disponible - à moins qu’une largeur spécifique soit définie, grâce à l’attribut ```style```.

Voici une liste non exhaustive des éléments nativement traités comme des **blocks** par les navigateurs :

- ```<div>```
- ```<h1>``` à ```<h6>```
- ```<form>```
- ```<header>```
- ```<footer>```
- ```<section>```

Exemple :

```html
<body>
    <!-- Definit un block -->
    <div>Hello World</div>
</body>
```

## Inline

Les éléments de type **inline** continuent sur la ligne en cours et ne prennent que la largeur nécessaire à leur affichage. 

Ci-dessous, une liste non exhaustive des éléments **inline** en HTML :

- ```<span>```
- ```<a>```
- ```<img>```

Exemple :

```html
<body>
 <!-- Hello World ne commence pas sur une nouvelle ligne, car <span> étant un élément inline, il continue sur la ligne en cours -->
    <p>Je suis un paragraphe alors je vous dis <span> Hello World</span></p>
</body>
```

## L'élément ```<div>```

```<div></div>``` est utilisé comme conteneur pour d'autres éléments HTML. Cela signifie que ces balises entourent d’autres éléments HTML. Ainsi, toute la ```<div>``` sera affichée en **bloc**. 

L’élément ```<div>``` n’a pas d’attribut particulier. Néanmoins, il est commun que l’attribut ```id``` soit utilisé afin d’attribuer un **identifiant unique** à l’élément, permettant, par exemple de créer des liens d’ancres ou encore, plus tard, de pouvoir styliser l’ensemble de la ```<div>```.

Exemple :

```html
<!-- Div de fond noir et texte en blanc -->
<div id="contenant">
    <!-- Titre de niveau 2 -->
    <h2>Toulouse</h2>
    <!-- Paragraphe -->
    <p>Toulouse est une belle ville proche des Pyrénées dans le sud de la France.</p>
</div>
```

## L'élément ```<span>```

L'élément ```<span></span>``` est un élément utilisé, en général, pour marquer un mot ou un bout de phrase au milieu d’un paragraphe. C’est un élément de type **inline**, permettant donc de faire continuer la partie marquée sur la ligne en cours. 

Cet élément est principalement utilisé pour pouvoir, plus tard, styliser une partie d’un texte à mettre en valeur, par exemple, sans que cette partie ne soit affichée comme un élément de type **block**.

Exemple :

```html
<p>J'ai des skis <span class="couleur">jaune</span></p>
```