Le rôle d’un langage de programmation est d’être compréhensible à la fois pour le développeur et pour la machine qui va devoir interpréter le code pour afficher les résultats attendus. 

Pour cela, les créateurs de langages informatiques se doivent d’adopter une sémantique claire et précise afin que le langage remplisse les deux objectifs ci-dessus.

## Les éléments sémantiques

Un élément sémantique décrit clairement sa fonction, le rôle qu’il remplit, tant pour le développeur qui utilise cet élément, que pour le navigateur qui affiche le résultat ou le contenu de l’élément.

Par exemple, les éléments ```<div>``` et ```<span>``` ne sont pas des éléments sémantiques car ils ne décrivent pas clairement le “rôle” du contenu qu’ils entourent. Le navigateur ne sait pas quel type de contenu il va afficher lorsqu’il rencontre ces éléments.

En revanche, les éléments ```<h1>```, ```<article>```, ```<form>```, ```<nav>```, etc. sont des éléments sémantiques car ils indiquent clairement ce qu’ils entourent, et donnent des informations au navigateur et au développeur sur ce qui va être affiché.

## Éléments sémantiques en HTML

De nombreux développeurs utilisent encore des ```<div id=”id”>``` pour structurer leurs pages webs. Cette technique n’est pas incorrecte, en soit. Mais si le code doit, plus tard, être repris par un autre développeur, ce dernier mettra plus de temps à comprendre le contenu de la ```<div>``` que si des éléments HTML sémantiques avaient été utilisés.

Comme évoqué dans le cours sur la mise en page en HTML, il existe des éléments sémantiques permettant de structurer clairement une page web :

- ```<article>```
- ```<aside>```
- ```<details>```
- ```<figcaption>```
- ```<figure>```
- ```<footer>```
- ```<header>```
- ```<main>```
- ```<mark>```
- ```<nav>```
- ```<section>```
- ```<summary>```
- ```<time>```

## Éléments figure et figcaption

Il existe deux autres éléments sémantiques, en HTML : les éléments ```<figure></figure>``` et ```<figcaption></figcaption>```.

L’élément ```<figure>``` entoure généralement du contenu d’illustration, tel que des photos, des dessins, des graphiques, etc.

L’élément ```<figcaption>```, quant à lui, définit une légende pour le contenu de ```<figure>```. ```<figcaption>``` peut-être placé avant ou après l’élément ```<figure>```.

Exemple :

```html
<figure>
    <img src="chat.jpg" alt="chat">
    <!-- Définit une légende -->
    <figcaption>Image1. - Un chat.</figcaption>
</figure>
```