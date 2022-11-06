L’objectif de ce cours est de comprendre plus précisément le rôle du HTML dans la création d’une page web.

## Le HTML et les balises

HTML est l’acronyme de “HyperText Markup Language”, signifiant littéralement : “langage de balisage hypertexte”, hypertexte faisant référence à tout ce qui est autour du texte. 

Par conséquent, le HTML est un langage de balises, celles-ci permettent à la fois de structurer la page web, mais également d’indiquer au navigateur comment afficher un élément.

Le langage HTML permet également de créer des liens hypertextes, des images, des vidéos, etc. Tous ces aspects du langage seront traités dans les différents cours. 

## Les titres

Les titres, en HTML, sont structurés avec des balises ```<hn>```, “n” représentant un chiffre de 1 à 6. Ceci pour la simple raison que les titres respectent une hiérarchie, ```<h1>``` représentant un titre principal ou important, et ```<h6>```, en étant le plus bas niveau de titre dans la hiérarchie, représente un titre beaucoup, beaucoup moins important.

Exemple :

```html
<h1>Titre de niveau 1 (important)</h1>
<h6> Titre de niveau 6 (beaucoup, beaucoup moins important)</h6>
```

## Les paragraphes

En HTML, les paragraphes sont définis avec la balise ```<p>```. Lorsque cette balise est fermée avec ```</p>```, un saut de ligne est automatiquement ajouté entre le paragraphe actuel et celui en dessous.

Exemple :

```html
<p>Ceci est un paragraphe</p>
```

## Liens HTML

Il existe deux types de liens, en HTML :

- Les liens “externe”, redirigeant l’utilisateur vers un autre site web, en fournissant l’URL de l’autre site web
- Les liens “internes’, permettant à l’utilisateur de naviguer entre les différentes pages du site, en fournissant le chemin d’accès au fichier HTML concerné.

Pour définir un lien en langage HTML, il faut utiliser la balise ```<a></a>```. Pour spécifier l’URL d’un autre site ou le chemin d’accès à un autre fichier HTML, l’attribut href doit être utilisé. Enfin, le texte du lien cliquable est placé entre les balises ```<a></a>```.

Exemple avec un lien menant vers un autre site web :

```html
<a href="www.google.com">Google</a>
```

Exemple avec lien menant vers une autre page du site :

```html
<a href="index.html">Accueil</a>
```

## Images

En HTML, les images sont définies avec la balise ```<img>```. Le chemin d’accès à l’image est spécifié dans l’attribut ```src```.

__Remarque__ : La balise ```<img>``` fait partie des exceptions, car elle **n’a pas de balise fermante**. Ainsi n’est-il pas possible d’écrire ```<img></img>```. De manière générale, un slash est ajouté à la fin de la balise.

Exemple :

```html
<img src="dossier/image.jpg" />
```

Par soucis d’accessibilité pour les personnes non-voyantes et pour les cas où l’image de s’afficherait pas correctement, il est courant d’utiliser l’attribut ```alt```. Cet attribut fournit un texte alternatif (très court, en général, un mot ou deux suffisent pour décrire l’image) qui s’affiche en cas de défaut d’affichage de l’image, ou qui sera lu par le navigateur des personnes non voyantes. 

Exemple :

```html
<img src="image.jpg" alt="logo" />
```

## Inspecteur d’élément

Il arrive à tout développeur de devoir un jour "déboguer" son code. En effet, lorsque ce dernier ne permet pas d’obtenir le rendu voulu, le développeur doit chercher l’erreur commise afin de la résoudre pour que tout rentre dans l’ordre.

Pour faciliter le travail des développeurs, les concepteurs de navigateurs internets (notamment Mozilla Firefox et Google Chrome) ont développé un outil très utile : l’inspecteur d’élément. Cet outil permet de consulter le code HTML et CSS d’une page web et de le modifier temporairement (au prochain rechargement de la page, le code sera revenu “à la normale”).

Pour accéder à l’inspecteur d’élément, il suffit de faire un clic droit sur une page web et de cliquer sur “inspecter”.

Sur Google Chrome, voici à quoi ressemble l’inspecteur d’éléments :

![Inspecteur d'éléments](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/HTML/courses/0020%20-%20Bases/images/image2.png)

L'inspecteur donne des informations détaillées sur l'élément actuellement sélectionné. Le bouton “Sélectionner un élément” permet de sélectionner un élément à inspecter :

![Inspecteur d'éléments](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/HTML/courses/0020%20-%20Bases/images/image3.png)

Le volet style permet de consulter le code CSS appliqué à un élément. Le CSS est le langage permettant d’appliquer du style à une page web. Ce langage est abordé dans un autre cours. 

![Onglet Style](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/HTML/courses/0020%20-%20Bases/images/image1.png)