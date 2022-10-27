Ajouter des icônes dans une page HTML est on ne peut plus simple, en CSS. Il suffit simplement d’utiliser une bibliothèque d’icônes.

## Ajouter des icônes

Font Awesome fait partie des bibliothèques d’icônes les plus utilisées par les développeurs web. Pour l’utiliser, il suffit juste d’ajouter le nom de l’icône dans l’attribut class de n’importe quel élément HTML de type inline, tel qu’un ```<i>``` ou un ```<span>```. L’élément HTML ```<i>``` est également souvent utilisé pour ajouter des icônes depuis une bibliothèque. À la base, cet élément HTML est utilisé pour mettre du contenu en italique, mais l’usage à fait que l’élément ```<i>``` est fréquemment interprété comme l’acronyme de “icône” ou du moins est utilisé à cette fin. Même s’il n’est donc pas rare de voir l’utilisation de cette balise afin d’afficher des icônes, gardez en mémoire que ce n’est pas une bonne pratique et ne correspond pas à la sémantique prodiguée par le HTML. Préférez l’utilisation de ```<span>``` lorsque c’est possible.

__Remarque__ : Il est courant de trouver dans les documentations des librairies d'icônes des exemples d’utilisation avec la balise ```<i>```. Leur utilisation avec la balise ```<span>``` (et ainsi conforme à la sémantique HTML) n’entraîne normalement aucun désagrément.

## Utiliser les icônes Font Awesome

Pour utiliser les icônes mises à disposition par Font Awesome, il suffit de se rendre sur le site web de Font Awesome, de créer un compte, puis d’obtenir un code qu’il faudra ajouter dans la section ```<head>``` de la page HTML.

L’avantage d’utiliser cette librairie est qu’il n’y a ni téléchargement, ni installation à effectuer. 

Le code fournit par Font Awesome ressemble à cela : 

```html
<script src="https://kit.fontawesome.com/1561b8564b.js" crossorigin="anonymous"></script>
```

__Remarque__ : le code se trouvant juste avant l’extension ‘.js’ est personnel et généré lors de la création du compte sur le site. 

Exemple d’utilisation des icônes Font Awesome :

```html
<!DOCTYPE html>
<html>
<head>
	<!-- Ligne de code fournie par le site. À placer absolument dans la section <head> -->
	<script src="https://kit.fontawesome.com/1561b8564b.js" crossorigin="anonymous"></script>
	<meta charset="utf-8" />
	<title>Mon site</title>
</head>
<body>
	<!-- Utilisation des icônes -->
	<span class="fas fa-bolt"></span>
	<span class="fas fa-bell"></span>
</body>
</html>
```

## Icônes Bootstrap

Il est également possible d’utiliser la librairie d’icônes mis à disposition par Bootstrap. Pour ce faire, placer la ligne de code ci-dessous dans la section ```<head>``` du code HTML :

```html
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
```

L’avantage de cette solution est qu’elle ne nécessite pas non plus de téléchargement ni d’installation. 

Exemple :

```html
<!DOCTYPE html>
<html>
<head>
	<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
	<meta charset="utf-8" />
	<title>Mon site</title>
</head>
<body>
	<!-- Utilisation des icônes -->
	<span class="glyphicon glyphicon-home"></span>
	<span class="glyphicon glyphicon-refresh"></span>
</body>
</html>
```

## Icônes Google

Cette méthode ne nécessite pas de téléchargement ni d’installation. Pour ajouter des icônes Google à une page HTML, il suffit d’ajouter le lien ci-dessous dans la section ```<head>``` du code HTML :

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
```

Exemple :

```html
<!DOCTYPE html>
<html>
<head>
	<link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
	<meta charset="utf-8" />
	<title>Mon site</title>
</head>
<body>
	<!-- Utilisation des icônes -->
	<span class="material-icon">article</span>
	<span class="material-icon">announcement</span>
</body>
</html>
```