Afin que chaque développeur puisse s’y retrouver dans le code source des autres, les langages informatiques ont tous une convention de codage. Cela signifie qu’il y a des règles de base d’écriture du code qui sont définies afin que tout le monde code de la même manière.

Bien entendu, rien n’oblige les développeurs à suivre ces règles, mais la plupart s’y plient tout de même afin d’assurer une certaine standardisation du code.

## Toujours déclarer le type de document

Lors de la création du document HTML, le type de document doit toujours être déclaré avec la balise ```<!DOCTYPE html>```. Cela indique au navigateur qu’il s’agit d’un document HTML et pas simplement d’un document texte.

## Utiliser des noms d'éléments et d'attributs en minuscules

Le langage HTML n’est pas sensible à la casse. Cela signifie qu’il ne fait pas la distinction entre un élément écrit en minuscule ou en majuscule.

Néanmoins, par convention, les éléments et attributs sont écrits en minuscule, pour les raisons suivantes :

- Les développeurs utilisent les minuscules
- Les minuscules semblent plus propre dans le code
- Les minuscules sont plus rapides à écrire

Exemple respectant la convention concernant les éléments et attributs :

```html
<body>
    <h1>Cours HTML</h1>
    <p>Voici un cours sur le HTML</p>
</body>

<a href="www.google.com">Google</a>
```

Exemple ne respectant pas la convention concernant les éléments et attributs:

```html
<BODY>
    <H1>Cours HTML</H1>
    <P>Voici un cours sur le HTML</P>
    <A href="www.google.com">Google</A>
</BODY>
```

__Remarque__ : Il est également formellement déconseillé d'utiliser des accents ou des caractères spéciaux à l'exception du tiret ```-``` et de l'underscore ```_```.

## Fermer tous les éléments HTML

HTML permet de ne pas fermer les éléments présents dans le code. Cependant, pour éviter la confusion et rendre le code plus clair, la convention veut qu’il faille fermer tous les éléments. Aussi il est largement recommandé pour toutes les balises non “auto fermantes” de bien spécifier les balises fermantes systématiquement.

Exemple respectant la convention : 

```html
<body>
    <h1>Cours HTML</h1>
    <p>Voici un cours sur le HTML</p>
</body>
```

Exemple ne respectant pas cette convention :

```html
<body>
    <h1>Cours HTML
    <p>Voici un cours sur le HTML
</body>
```

## Mettre les valeurs d’attributs entre guillemets

Le langage HTML permet également de ne pas mettre les valeurs d’attributs entre guillemets.

Cependant, pour les raisons citées ci-dessous, il est recommandé de mettre des guillemets autour des valeurs d’attributs :

- Les valeurs entre guillemets sont plus faciles à distinguer dans le code
- Le langage HTML exige de toute manière que les guillemets soient utilisés en si la valeur contient des espaces.

Exemple respectant la convention :

```html
<p class="container red">Voici un cours sur le HTML</p>
```

Exemple ne respectant pas la convention :

```html
<p class=container red>Voici un cours sur le HTML</p>
```

## Toujours spécifier l'attribut alt, la largeur et la hauteur des images

Comme évoqué dans le cours sur les images, l’attribut ```alt```, bien que non obligatoire, est recommandé. Il permet d’afficher un texte alternatif en cas de problème d’affichage de l’image et rend également le site accessible aux personnes malvoyantes ou non-voyantes.

De plus, la convention exige de spécifier la hauteur et la largeur des images afin de réduire le scintillement. En effet, en spécifiant la hauteur et la largeur de l’image, le navigateur peut allouer l’espace nécessaire à l’affichage de l’image avant le chargement de la page ou du moins avant l’affichage de l’image. 

Exemple respectant la convention :

```html
<img src="chat.png" alt="chat" style="width:500px; height:500px" />
```

Exemple ne respectant pas la convention :

```html
<img src="chat.png" />
```

## Espaces et signe égal

Le langage HTML permet d’ajouter un espace entre l’attribut, le signe égale et la valeur de l’attribut. 

Cependant, pour des raison de lisibilité du code, la convention veut que le développeur ne rajoute pas d’espace entre ces éléments.

Exemple sans espace :

```html
<p class="container">Voici un cours sur le HTML</p>
```

Exemple avec espaces :

```html
<p class     =     "container">Voici un cours sur le HTML</p>
```

## Évitez les longues lignes de code

Pour des raisons de gain de temps et de lecture du code, les longues lignes de code ne sont pas recommandées. En effet, faire défiler l’éditeur de code de gauche à droite pour lire une longue ligne de code fait perdre un temps précieux. 

Il est ainsi recommandé de revenir à la ligne lorsque le code commence à “dépasser” de la fenêtre de l’éditeur. Ainsi, sera-t-il plus facile à lire.

## Lignes vides et indentation

L’indentation est le fait de créer un décalage du contenu sur la droite, et ainsi laisser une marge plus grande sur la gauche. La plupart des éditeurs de code ajoutent automatiquement une indentation lorsque cela est nécessaire. Cela rend le code plus lisible et plus clair lorsqu’il y a des éléments à corriger.

Néanmoins, il ne faut pas rajouter des indentations là où ce n’est pas nécessaire. Cela rend, au contraire, le code moins lisible et moins clair.

Il est de coutume d’ajouter un niveau d’indentation en fonction de l’imbrication des éléments HTML. Ainsi si une balise en contient une autre, il est de convention d’indenter la seconde, de telle sorte à distinguer visuellement l’appartenance de cette dernière.

Exemple respectant la convention :

```html
<table>
    <tr>
        <td>Nom</td>
        <td>Prénom</td>
    </tr>
    <tr>
        <td>Doe</td>
        <td>John</td>
    </tr>
</table>
```

Exemple ne respectant pas la convention :

```html
<table>
    <tr>

<td>Nom</td>
<td>Prénom</td>
    </tr>

    <tr>

        <td>Doe</td>
        <td>John</td>
    </tr>
</table>
```

## Ne jamais sauter l'élément ```<title>```

Dans le document HTML, l’élément ```<title></title>``` doit toujours être renseigné. En effet, en plus de définir un titre dans l’onglet ou la fenêtre du navigateur, en plus de fournir un titre à la page lorsqu’elle est ajoutée en favoris, cela permet aussi un meilleur référencement par les moteurs de recherche.

Il est donc recommandé d’écrire un titre qui soit le plus précis possible - sans être trop long, cependant.

Exemple :

```html
<title>Guide de style HTML et conventions de codage</title>
```

## Omettre les éléments ```<html>``` et ```<body>```

Un document HTML est valide, même sans les éléments ```<html></html>``` et ```<body></body>```. Cependant, par soucis de compatibilité du site web avec les anciens navigateurs, il est tout de même recommandé de mettre ces balises. En effet, l’omission de ces balises peut créer des bugs sur les anciens navigateurs.

Exemple respectant cette convention :

```html
<!DOCTYPE html>
<html>
<head>
    <title>Conventions de codage</title>
</head> 

<body>
    <h1>Cours HTML</h1>
    <p>Voici un cours sur le HTML</p>    
</body>
</html>
```

Exemple ne respectant pas cette convention :

```html
<!DOCTYPE html>
<head>
    <title>Conventions de codage</title>
</head>

<h1>Cours HTML</h1>
<p>Voici un cours sur le HTML</p>
```

## Omettre l’élément ```<head>```

Un fichier HTML est également viable sans les balises ```<head></head>```. Si tel est le cas, les navigateurs ajouteront des éléments par défaut contenus dans le ```<head>```.

Malgré tout, il est recommandé d’ajouter l’élément ```<head>```. Cela permet au développeur d’ajouter les informations précises contenues dans cet élément.

Exemple avec le ```<head>``` :

```html
<!DOCTYPE html>
<html>
<head>
    <title>Conventions de codage</title>
</head> 

<body>
    <h1>Cours HTML</h1>
    <p>Voici un cours sur le HTML</p>    
</body>
</html>
```

Exemple sans le ```<head>``` :

```html
<!DOCTYPE html>
<html>
<title>Conventions de codage</title>

<body>
    <h1>Cours HTML</h1>
    <p>Voici un cours sur le HTML</p>    
</body>
</html>
```

## Fermer les éléments HTML vides

Le langage HTML permet au développeur de ne pas ajouter un slash (/) à la fin d’une balise auto-fermante, et aucune règle précise n’existe sur le fait d’ajouter ce slash. Ceci est à la discrétion du développeur.

Ainsi, l’exemple ci-dessous est-il accepté :

```html
<meta charset="utf-8">
```

Et cet exemple est aussi accepté :

```html
<meta charset="utf-8" />
```

## Ajouter l'attribut lang

En HTML, la convention exige de toujours ajouter et renseigner l’attribut ```lang``` dans la balise ```<html>```, car cela aide les moteurs de recherche pour le référencement du site web.

Exemple :

```html
<!DOCTYPE html>
<html lang="fr-FR">
<head>
    <title>Conventions de codage</title>
</head> 

<body>
	...
</body>
</html>
```

## Extensions des fichiers HTML

Il existe deux extensions pour un fichier HTML :

- L’extension .html
- L’extension .htm

Aucune différence n’existe entre ces deux extensions. Les deux seront traitées, par le navigateur, comme des fichiers HTML.