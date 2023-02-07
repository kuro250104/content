Le langage HTML permet de définir des paragraphes et d’indiquer au navigateur comment les afficher.

## Les paragraphes

En HTML, un paragraphe est délimité par les balises ```<p></p>```. À chaque fois que la balise ```</p>``` ferme un paragraphe, le navigateur effectue un saut de lignes. 

Exemple :

```html
<body>
	<p>Ceci est un paragraphe</p>
	<p>Ceci est un autre paragraphe</p>
</body>
```

## Affichage HTML

Il n’est pas de règles précises quant à l’affichage des paragraphes par les navigateurs. Tout dépend de leurs paramètres, de leurs versions, etc. 

Néanmoins, il est important de noter qu’un paragraphe écrit sur plusieurs lignes en HTML apparaît sur une seule ligne lorsque le navigateur l’affiche. En effet, ce dernier supprime les sauts de lignes et espaces inutiles. 

Pour faire des retours à la ligne au sein d’un paragraphe, le langage HTML met à disposition la balise ```<br />```.

```html
<p>
Un paragraphe
Qui contient plusieurs lignes
Dans le code source 
Mais le navigateur
Les ignores
</p>

<p>
Un paragraphe
Qui contient         plusieurs lignes et espaces
Dans le code         source
Mais le        navigateur
Les ignores
</p>
<p> Ceci est un paragraphe écrit <br />
Sur plusieurs lignes et qui est affiché sur plusieurs <br />
Lignes grâce à la balise <br /></p>
```

## Bordure horizontale

Lorsque plusieurs idées sont évoquées sur une même page web, il est parfois intéressant de pouvoir séparer visuellement les différentes sections à l’aide d’une bordure horizontale. 

Le langage HTML permet cela grâce à la balise unique ```<hr>```.

*Remarque* : ```<hr>``` est une balise unique qui n’est pas auto-fermante et qui ne dispose pas de balise fermante non plus. Ainsi, si le développeur écrit ```<hr />```, la bordure horizontale ne s’affiche pas.

## Texte préformaté

Dans le troisième point de ce cours, il est expliqué qu’au sein des balises ```<p></p>```, les retours à la ligne n’étaient pas pris en compte par le navigateur. Ainsi, si un paragraphe doit revenir à la ligne, la balise ```<br />``` est utilisée. 

Cependant, lorsqu’un long paragraphe est composé de nombreux retours à la ligne, il est assez fastidieux de mettre des balises ```<br />``` à chaque retour à la ligne. 

Le langage HTML règle ce problème grâce aux balises ```<pre></pre>```. Grâce à cela, il est précisé au navigateur qu’il s’agit d’un texte préformaté. Le navigateur affichera donc le paragraphe dans une police de largeur fixe, tout en préservant les espaces et les retours à la ligne.

Exemple :

```html
<pre>
Un paragraphe

Qui contient plusieurs lignes

Dans le code source 

Mais le navigateur

Les ignore
</pre>
```
