## Introduction

Dans ce nouveau cours, nous allons apprendre la syntaxe de base de jQuery et écrire les premières instructions jQuery. Nous verrons également où écrire du code jQuery.

## Où écrire le code jQuery

Lors du développement, il est généralement considéré comme une bonne pratique de séparer les différents modules du projet en les mettant dans des fichiers différents, d'autant plus que cela simplifie la maintenance du code et rend l'ensemble de celui-ci plus lisible pour les développeurs.

Notre code jQuery ne fait pas exception, nous écrivons donc ce code dans des fichiers séparés. Ensuite, nous utiliserons l'élément script et son attribut src pour inclure les fichiers requis dans le fichier HTML.

Pour la suite de ce cours, nous allons créer deux fichiers : un fichier appelé index.html et un fichier appelé script.js, où nous placerons le code jQuery.

## La syntaxe du jQuery

JQuery a une syntaxe de base relativement simple, logique et intuitive, adaptée aux personnes qui ont des notions débutantes à intermédiaires en HTML, CSS et JavaScript.

Nous pourrons utiliser ```jQuery()``` ou ```$()``` pour accéder aux différents attributs et méthodes de la bibliothèque jQuery.

jQuery est le langage de "queries" JavaScript, c'est-à-dire le langage de requête JavaScript. Nous utiliserons jQuery pour effectuer des opérations sur des éléments HTML.

Par conséquent, pour sélectionner tous les paragraphes de la page, nous écrirons ```$("p")```, et pour sélectionner uniquement l'élément avec l'attribut ```id = "p1"```, nous écrirons ```$("# p1")```.

Nous pourrons utiliser n'importe quel sélecteur CSS pour localiser des éléments HTML dans jQuery, y compris des sélecteurs CSS complexes ou composés. Cela nous permettra de localiser tout type de contenu HTML de manière très précise et simple.

Lors de l'utilisation de la syntaxe ```$(selecteur)```, jQuery renvoie en fait un objet jQuery. Ensuite, nous pourrons appliquer des méthodes ou des propriétés à l'objet retourné pour effectuer des opérations ou obtenir des informations à son sujet.

Plus précisément, notre code jQuery ressemblera à ceci : ```$(selecteur).action()```. Ici, la partie ```$(selecteur)``` retourne un objet auquel nous appliquerons la méthode ```action()```.

```js
$('#p1').hide();
```

## Attendre le chargement de la page pour exécuter le jQuery

La plupart des opérations que nous effectuerons dans jQuery sont des opérations sur la structure HTML de la page. Cependant, pour manipuler cette structure HTML, elle doit exister.

Par conséquent, avant d'effectuer des opérations avec jQuery, vous devez vous assurer que le navigateur ait fini de charger la structure HTML de la page pour pouvoir interagir avec.

En effet, lorsque vous demandez au navigateur d'afficher une page Web, il crée automatiquement un modèle objet de la page ou du document. Ce modèle objet est appelé “DOM” (Document Object Model) et nous vous invitons à consulter le cours Javascript concernant ce sujet si nécessaire.

Il existe différentes méthodes afin d’imposer à jQuery d’attendre le chargement d’une page avant d’exécuter le script, cependant une seule est aujourd’hui considérée comme sûre (les autres ayant été dépréciées) : $(document).ready()

Cette commande ne s’exécutera que lorsque le DOM sera entièrement disponible, c’est-à-dire que tous les éléments du HTML auront été analysés par votre navigateur. Voici un exemple d’utilisation :

```js
$(document).ready(function(){
    $('#p1').hide();
});
```

Dans l’exemple ci-dessus, l'événement ready est déclenché, puis le code contenu dans la fonction anonyme est exécuté.

L’utilisation de cette méthode est soumise à un détail important : cette technique permet de n’exécuter du code que lorsque le DOM est généré. Or il est important de rappeler que le DOM peut être complet alors que toutes les ressources externes n’auront peut-être pas été chargées. Ainsi si l’on prend l’exemple d’une modification à réaliser sur une image, il est possible que votre DOM soit prêt, mais que l’image n’ait pas encore été téléchargée et intégrée par votre navigateur. Ainsi la modification sur l’image n’aura pas forcément lieu, et le résultat du traitement sera assez aléatoire en fonction des utilisateurs qui consultent votre site.

Si toutefois vous éprouvez la nécessité absolue que tous les éléments d’une page soient chargés AVANT d’exécuter un script, vous devez savoir qu’il existe la méthode ```$(window).load()``` qui permet de répondre à ce besoin. Cependant, vous devez également savoir que cette méthode est de moins en moins utilisée et devenue obsolète à partir de la version 1.8 de jQuery, et complètement supprimée à partir de la version 3.0. Aussi nous vous déconseillons de vous en servir, dans la limite du possible.