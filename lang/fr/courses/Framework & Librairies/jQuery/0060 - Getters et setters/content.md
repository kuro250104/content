## Introduction

JQuery dispose de différentes méthodes pour récupérer des informations sur les éléments HTML de notre page, notamment leur contenu, ainsi qu’effectuer diverses opérations sur ceux-ci : modifier le contenu, le style et la taille, supprimer les éléments et en utiliser d'autres, en ajouter avant ou après un autre...

## Fonctionnement des méthodes getters et setters jQuery

La fonction du getter est d’obtenir des informations, d’en récupérer. Le rôle du setter est d’en définir ou d’en mettre à jour. Ils existent dans de nombreux langages de programmation et sont respectivement traduits en français par des accesseurs et des mutateurs.

Par convention, les fonctions de type getter commencent par le préfixe "get", et les fonctions de type setter commencent par le préfixe "set", ce qui permet de les identifier rapidement.

JQuery fonctionne différemment de ce modèle classique, et dans la plupart des cas, il est impossible de faire la distinction entre un getter et un setter. En effet, dans jQuery, les méthodes qui permettent d'obtenir des informations permettent généralement également de définir et de mettre à jour ces informations, afin qu'elles puissent être utilisées à la fois comme getter et comme setter.

Ainsi, l’utilisation d’une seule méthode en jQuery permet soit de servir de getter, soit de setter. La distinction s’opère souvent dans la manière d’appeler cette méthode. Une méthode appelée sans argument sera ainsi considérée comme un “getter”, alors que la même méthode, utilisée avec au moins un argument sera considérée comme un “setter”.

Voici une liste de différentes méthodes concernées :

- ```html()``` : Permet d'obtenir le contenu HTML d’un élément ou de définir son contenu.

```js
// récupération du contenu HTML
$( "div.demo-container" ).html();
// modification du contenu HTML
$( "div.demo-container" ).html("<p>microlead</p>");
```

- ```text()``` : Permet d’obtenir ou de définir les contenus textuels de tous les éléments d’une sélection

```js
// récupération du contenu textuel
$( "p" ).text();
// modification du contenu textuel
$( "p" ).text("microlead");
```

- ```attr()``` : Permet d’obtenir la valeur d’un attribut du premier élément d’une sélection ou de définir un ou plusieurs attributs pour tous les éléments de la sélection

```js
// récupération de l'attribut "checked" du premier élément
$(".element").attr("checked");
// définition de tous les attributs "alt" des balises images
// avec le contenu "microlead"
$("img").attr("alt", "microlead");
```

- ```prop()``` : Permet d’obtenir la valeur d’une propriété du premier élément d’une sélection ou de définir une ou plusieurs propriétés pour tous les éléments de la sélection

```js
// récupération de la propriété "checked" du premier élément de
// la sélection
$(".element").prop("checked");
// définition de la propriété "checked" à "true" pour
// tous les éléments de la sélection
$(".element").prop("checked", true);
```

- ```val()``` : Permet d’obtenir la valeur (le contenu de l’attribut value) du premier élément d’une sélection ou de définir une valeur pour tous les éléments de la sélection

```js
// récupère la valeur de l'attribut "value" du premier élément
// de la sélection
$("select#foo option:checked").val();
// définit l'attribut "value" de tous les éléments de la
// sélection
$("select#foo option:checked").val(true);
```

- ```css()``` : Permet d’obtenir la valeur d’une propriété CSS pour le premier élément d’une sélection ou de définir les valeurs d’une ou de plusieurs propriétés CSS pour tous les éléments de la sélection

```js
// récupération de la propriété CSS du premier élément de la 
// sélection
$(".element").css("color");
// définition de la couleur "red" en CSS pour tous les éléments
// de la sélection
$(".element").css("color", "red");
```

- ```height()``` : Permet d’obtenir la hauteur de la boite élément du premier élément d’une sélection ou de définir cette hauteur pour tous les éléments de la sélection

```js
// récupère la hauteur du premier élément de la sélection
$(".element").height();
// modifie la hauteur de tous les éléments de la sélection
$(".element").height(50);
```

- ```innerHeight()``` : Identique à ```height()```, mais inclut les marges intérieures dans le calcul

```js
// récupère la hauteur du premier élément de la sélection en incluant
// les marges intérieures
$(".element").innerHeight();
// modifie la hauteur de tous les éléments de la sélection en incluant
// les marges intérieures
$(".element").innerHeight(50);
```

- ```outerHeight()``` : Identique à ```height()```, mais inclut les marges intérieures, les bordures et de manière optionnelle les marges extérieures dans le calcul

```js
// récupère la hauteur du premier élément de la sélection en incluant
// les marges intérieures et les bordures
$(".element").outerHeight();
// récupère la hauteur du premier élément de la sélection en incluant
// les marges intérieures, les bordures et les marges extérieures
$(".element").outerHeight(true);
// modifie la hauteur de tous les éléments de la sélection en incluant
// les marges intérieurs et les bordures
$(".element").outerHeight(50);
// modifie la hauteur de tous les éléments de la sélection en incluant
// les marges intérieurs, les bordures et les marges extérieurs
$(".element").outerHeight(50, true);
```

- ```width()``` : Permet d’obtenir la largeur de la boite élément du premier élément d’une sélection ou de définir cette largeur pour tous les éléments de la sélection

```js
// récupère la largeur du premier élément de la sélection
$(".element").width();
// définit la largeur de tous les éléments de la sélection
$(".element").width(50);
```

- ```innerWidth()``` : Identique à ```width()```, mais inclut les marges intérieures dans le calcul

```js
// récupère la largeur du premier élément de la sélection en incluant
// les marges intérieures
$(".element").innerWidth();
// définit la largeur de tous les éléments de la sélection en incluant
// les marges intérieures
$(".element").innerWidth(50);
```

- ```outerWidth()``` : Identique à ```width()```, mais inclut les marges intérieures, les bordures et de manière optionnelle les marges extérieures dans le calcul

```js
// récupère la largeur du premier élément de la sélection en incluant
// les marges intérieures et les bordures
$(".element").outerWidth();
// récupère la largeur du premier élément de la sélection en incluant
// les marges intérieures, les bordures et les marges extérieures
$(".element").outerWidth(true);
// définit la largeur de tous les éléments de la sélection en incluant
// les marges intérieures et les bordures
$(".element").outerWidth(50);
// définit la largeur de tous les éléments de la sélection en incluant
// les marges intérieures, les bordures et les marges extérieures
$(".element").outerWidth(50, true);
```

- ```offset()``` : Permet d’obtenir les coordonnées actuelles du premier élément d’une sélection ou de définir les coordonnées de tous les éléments de la sélection relativement au document. Cette méthode utilise le pixel comme unité de valeur.

```js
// récupère les coordonnées en pixel, à partir de la gauche et de la 
// droite, du premier élément de la sélection
$(".element").offset();
// définit les coordonnées en pixel, à partir de la gauche et de la 
// droite, de tous les éléments de la sélection
$(".element").offset( {top: 50, left: 100} );
```

- ```scrollLeft()``` : Permet d’obtenir la position actuelle de la barre de défilement horizontale du premier élément d’une sélection ou de définir cette position tous les éléments de la sélection. Cette méthode utilise le pixel comme unité de valeur.

```js
// récupère la position de la barre de défilement horizontale du
// premier élément de la sélection, à partir de la gauche (0)
$("div.demo").scrollLeft();
// définit la position de la barre de défilement horizontale de tous
// les éléments de la sélection à la valeur indiquée
$("div.demo").scrollLeft(100);
```

- ```scrollTop()``` : Permet d’obtenir la position actuelle de la barre de défilement verticale du premier élément d’une sélection ou de définir cette position tous les éléments de la sélection. Cette méthode utilise le pixel comme unité de valeur.

```js
// récupère la position de la barre de défilement verticale du
// premier élément de la sélection, à partir du haut (0)
$("div.demo").scrollTop();
// définit la position de la barre de défilement verticale de tous
// les éléments de la sélection à la valeur indiquée
$("div.demo").scrollTop(300);
```