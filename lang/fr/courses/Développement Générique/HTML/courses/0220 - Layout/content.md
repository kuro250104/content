La mise en page d’une page web - communément appelée “layout” - est importante pour un site internet.

Tel qu’il a été expliqué dans les cours précédents, le HTML est un langage de balises, chaque balise permettant d’indiquer au navigateur à quoi correspond un élément. Ainsi, pour améliorer la sémantique du langage HTML - sémantique signifiant “qui concerne le sens, la signification” - et savoir à quoi correspond chaque section d’une page HTML lors du travail de mise en page, le langage met à disposition un certain nombre de balises.

## Eléments de mise en page

Le langage HTML dispose de plusieurs balises permettant de “structurer” un site afin d’améliorer sa sémantique. 

**Remarque** : Tous ces éléments de structure se trouvent entre les balises ```<body></body>``` du fichier HTML.

Ci-dessous, la liste des éléments sémantiques mis à disposition pour l’amélioration de la structure d’un document HTML :

- ```<header>``` : Définit un en-tête pour un document ou une section. À ne pas confondre avec l’élément ```<head></head>```. Dans une page HTML, le header contient généralement le logo.
- ```<nav>``` : Cet élément entoure une barre de navigation (menu).
- ```<section>``` : Définit une section dans un fichier HTML
- ```<article>``` : Définit un contenu indépendant et autonome, généralement le contenu de la page web ou de la section en cours.
- ```<aside>``` : Définit un contenu qui sera mis “sur le côté”. En d’autre termes, cet élément est utilisé afin de définir un contenu qui ne peut être mis dans un ```<article>``` (des informations supplémentaires, par exemple).
- ```<footer>``` : Définit un pied de page pour un document ou une section
- ```<details>``` : Définit des détails supplémentaires que l'utilisateur peut ouvrir et fermer à la demande

Exemple d’une structure HTML reprenant les éléments ci-dessus :

``` html
<!DOCTYPE html>
<html lang="fr">
<head>
	<meta charset="utf-8" />
	<title>Titre de la page web</title>
</head>
<body>
	 <header>
	 	Logo
	 </header>

	 <nav>
	 	<ul>
	 		<li><a href="#">Lien 1</a></li>
	 		<li><a href="#">Lien 2</a></li>
	 		<li><a href="#">Lien 3</a></li>
	 </nav>

	 <section>
	 	<article>
	 		<p>Je suis un paragraphe contenu dans la balise article</p>
	 	</article>
	 	<aside>
	 		<p>Je contiens des informations supplémentaires</p>
	 	</aside>
	 </section>

	 <footer>
	 	Ici se trouvent généralement un lien pour contacter le propriétaire du site et les droits d'auteur
	 </footer>

</body>
</html>
```

## Éléments de mise en page

### Element section

L’élément ```<section></section>``` permet de regrouper des contenus ayant le même thème. Une section commence généralement avec un titre. 

En fonction du type de site développé, il est courant qu’une page web soit divisée en plusieurs sections, toutes avec une thématique différente.

Exemple :

``` html
<!-- Définit une section -->
<section>
      <h1>Première section</h1>
    	<p>Pellentesque feugiat, mauris nec ornare commodo, nisi leo pellentesque neque, et mollis dui ante mattis felis.
        Nullam quis lacinia libero, non malesuada tellus. Integer nec augue finibus, tempus magna eget, placerat leo.
        Nulla hendrerit arcu ipsum, ac pharetra massa sodales id.</p>
</section>

<!-- Définit une autre section -->
<section>
    <h1>Deuxième section</h1>
    <p>Pellentesque feugiat, mauris nec ornare commodo, nisi leo pellentesque neque, et mollis dui ante mattis felis.
        Nullam quis lacinia libero, non malesuada tellus. Integer nec augue finibus, tempus magna eget, placerat leo.
        Nulla hendrerit arcu ipsum, ac pharetra massa sodales id.</p>
</section>
```

### Élement article

L’élément ```<article></article>``` entoure le contenu d’une page web ; cependant, le contenu d’un ```<article>``` doit être autonome et indépendant. En d’autre termes, il ne doit être raccroché à aucune autre thématique sur la page. 

Concrètement, un contenu de type ```<article></article>``` peut très bien être un message sur un forum, un billet de blog ou un article sur le site d’un journal, par exemple.

Cependant, bien que par définition un article doit représenter un contenu autonome et indépendant, il est courant de voir des sites web incluant des éléments ```<article>``` au sein de  ```<section>```.

Exemple :

``` html
<!-- Définit un article -->
<article>
    <h2>Microlead</h2>
    <p>Microlead vous accompagne dans l’apprentissage du développement et dans l’amélioration permanente de vos compétences.</p>
</article>
```

### Élément header

Dans sa fonction première, l’élément ```<header></header>``` est utilisé pour définir un en-tête. Généralement il est utilisé pour définir l’en-tête d’une page web, mais rien n’interdit de l’utiliser également pour définir l’en-tête d’une section ou d’un article.

Exemple :

``` html
<!-- Définit un article -->
<article>
    <!-- Définit l'en-tête de l'article -->
    <header>
        <h1>Microlead</h1>
        <p>Notre mission :</p>
      </header>
    <!-- Paragraphe -->
    <p>Microlead vous accompagne dans l’apprentissage du développement et dans l’amélioration permanente de vos compétences.</p>
</article>
```

### Element footer

L’élément ```<footer></footer>``` définit un “pied” (une fin) pour une section ou une page HTML. Cet élément contient généralement des informations sur l’auteur, sur les droits d’auteur, un lien menant vers un formulaire de contact, etc.

Exemple :

``` html
<!-- Définit un pied de page -->
<footer class="sub-footer">
    <div class="footer-content">
        <p><a class="link" href="legals.php">Mentions légales</a> | Microlead </p>
    </div>
</footer>
```

### Élément nav

L'élément ```<nav></nav>``` définit un ensemble de liens de navigation. De manière générale, cet élément est utilisé lors de la création d’un menu de navigation pour un site web. C’est d’ailleurs son rôle. En effet, ```<nav>``` n’est utilisé que pour les “blocs” de liens.

Exemple :

``` html
<!-- Dans cet exemple, <nav> entoure le menu de navigation -->
<nav class="main-nav">
    <a title="Accueil" class="link" href="#">Accueil</a>
    <a title="Titre 1" class="link" href="#">Titre 1</a>
    <a title="Titre 2" class="link" href="#">Titre 2</a>
    <a title="Titre 3" class="link" href="#">Titre 3</a>
    <a title="Titre 4" class="link" href="#">Titre 4</a>
    <a title="Titre 5" class="link" href="#">Titre 5</a>
    <a title="Titre 6" class="link" href="#">Titre 6</a>
</nav>
```

### Element aside

L’élément ```<aside></aside>``` définit un contenu indirectement lié au contenu actuel. C’est généralement un élément qui sera placé sur le côté lors de la phase de design. Cet élément peut, par exemple, contenir des informations supplémentaires sur le contenu, une liste de liens menant à des ressources externes, etc.

Exemple :

``` html
<aside>
    <h1>Microlead</h1>
    <p>Microlead vous accompagne dans l’apprentissage du développement et dans l’amélioration permanente de vos compétences.</p>
</aside>
```