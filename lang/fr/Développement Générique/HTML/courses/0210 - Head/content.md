L’élément ```<head></head>```, bien qu’il ne soit pas interprété ni affiché par le navigateur, contient des informations importantes pour que le navigateur puisse, par exemple, savoir quel encodage utiliser afin de pouvoir afficher correctement les accents.

## Element <head>

Les éléments contenus dans le ```<head>``` (*en-tête*, en anglais), ne sont pas affichés par le navigateur. Ils permettent par exemple d’afficher le texte et les accents correctement, de lier le fichier contenant le design du site web, ou encore de donner un titre à la page web.

## Element <title>

Cet élément permet de définir un titre pour la page en cours. Il est affiché dans la fenêtre ou dans l’onglet du navigateur - c’est d’ailleurs le seul élément contenu dans le ```<head></head>``` qui est affiché par le navigateur. 

Le texte contenu entre les balises ```<title></title>``` est également affiché dans les favoris et dans les résultats des moteurs de recherches.

**Remarque** : Le titre doit être uniquement composé de texte. 

L’élément ```<title></title>``` est nécessaire dans un document HTML, car cela favorise, par la suite, le référencement du site par les moteurs de recherche.

Exemple :

``` html
<!DOCTYPE html>
<html lang="fr">
<head>
    <!-- Titre de du document -->
    <title>Titre de page important</title>
</head>
<body>
    
</body>
</html>
```

## Element <style>

Cet élément est utilisé pour écrire du code CSS (permettant de créer le design du site) directement au sein du document HTML.

Exemple :

``` html
<style>
    /* Les paragraphes seront écrits en rouge et le texte sera centré */
    p {
        color: red;
        text-align: center;
    }
</style>
```

## Element <link>

Cet élément est utilisé pour lier une ressource externe au document actuel. De nos jours, il est généralement utilisé pour lier une feuille de style contenant le design, au document HTML actuel.

**Remarque** : ```<link>``` est une balise auto-fermante, il n’est donc pas rare de voir un slash avant le chevron de fin.

Cet élément est **toujours** accompagné des deux attributs suivants :

- **rel** : indique le type de document que représente le source externe. Dans le cas d’une feuille de style, cet attribut recevra la valeur “stylesheet”.
- **href** : reçoit en valeur le chemin absolu ou relatif menant vers la ressource à lier au document.

Exemple :

``` html
<!-- Lie un fichier css interne au document -->
<link rel="stylesheet" href="style.css" />
```

## Element <meta>

Meta, par son étymologie, signifie “après” ou “au-delà de”. Cet élément HTML permet donc d’apporter aux navigateurs et aux moteurs de recherches des informations sur le document HTML et sur le site. Ces données ne sont pas affichées par le navigateur.

**Remarque** : ```<meta>``` est également une balise autofermante. 

Exemples d’utilisations de ```<meta>``` :

``` html
<!-- Définir l’encodage utilisé afin que les navigateurs affichent correctement les accents -->
<meta charset="UTF-8">
<!-- Définir des mots-clés pour les moteurs de recherche -->
<meta name="keywords" content="Cours, Programmation, Informatique, HTML">
<!-- Définir la description de votre page web -->
<meta name="description" content="Cours de programmation informatique -  HTML">
<!-- Définir l'auteur de la page -->
<meta name="author" content="NK Informatique">
```

## Définition de la taille de la fenêtre du navigateur

La fenêtre d’affichage est l’endroit où le site web s’affiche. Elle ne prend pas en compte la barre d’outil du navigateur. 

De nos jours, avec les smartphones, les tailles de fenêtres d’affichage varient en fonction de l’appareil utilisé pour consulter un site web. Ainsi la fenêtre d’affichage sera-t-elle plus petite sur un smartphone et une tablette, que sur un ordinateur, par exemple. Le principal problème avec les différentes tailles de fenêtres, c’est que le design d’un site web doit rester cohérent et le contenu lisible, quelle que soit la taille de la fenêtre sur lequel le site est consulté.

Pour palier à ce problème, le langage HTML met à disposition 2 attributs utilisables avec l’élément ```<meta>``` :

- **name** : qui contient généralement le mot “viewport” (*fenêtre d’affichage*, en anglais), permet d’indiquer à la balise ```<meta>``` qu’elle va recevoir des informations concernant la fenêtre d’affichage
- **content** : reçoit des informations concernant la largeur de l’appareil utilisé pour consulter le site, et le niveau de zoom à utiliser lors du premier chargement de la page.

Exemple d’utilisation de meta pour les fenêtres d’affichage :

``` html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

```width=device-width``` définit la largeur de la fenêtre d’affichage de l’appareil utilisé, afin que le navigateur puisse afficher le site web de manière lisible, quelle que soit la taille de la fenêtre d’affichage.

La partie ```initial-scale=1.0``` définit le niveau de zoom à utiliser lors du premier chargement de la page

Ci-dessous, un exemple de ce que donne une page HTML chargée sans que l’élément **meta viewport** soit renseigné (à gauche), et un autre exemple avec la balise **meta viewport** renseignée (à droite).

Dans l’exemple ci-dessous, la page HTML chargée sans que **meta viewport** soit renseigné (image de gauche) “déborde” de la fenêtre d’affichage du téléphone, ce qui rend le contenu moins lisible, et le design moins agréable.

En revanche, dans l’image de droite, la balise **meta viewport** est renseignée, permettant au navigateur d’adapter l’affichage du contenu afin que celui-ci ne déborde pas de la fenêtre d’affichage. Cela permet également à l’utilisateur de zoomer à sa convenance afin de pouvoir lire le texte.

![Illustration ci-dessus](https://github.com/Microleadoff/content/blob/master/lang/fr/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/HTML/courses/0210%20-%20Head/images/image1.jpg)