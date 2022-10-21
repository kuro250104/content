Le **DOM** (*Document Object Model*) est une arborescence générée par le navigateur afin d’afficher ou d'interagir avec le contenu HTML d’un site web, ou bien avec son apparence (CSS).

## Le DOM

Le DOM est une interface de programmation pour des documents HTML, XML ou SVG qui représente informatiquement un document de manière structurée et normée. Il est généralement créé par le navigateur lors du chargement d’un document et nous permet par la suite d’interagir avec.

Le DOM est souvent représenté sous la forme d’un arbre qui permet de comprendre plus simplement son fonctionnement et son organisation : 

- Un arbre dispose d’un tronc, qui constitue une base à partir de laquelle plusieurs branches peuvent se rattacher. De même, chacune de ces branches peuvent avoir d’autres branches rattachées, et ainsi de suite.
- Le DOM fonctionne de la même manière. Les branches et le tronc sont nommés des “**nœuds**”. Le tronc étant le nœud principal. Chaque nœud présent dans le DOM peut donc être la base de zéro, un ou plusieurs autres nœuds de la même manière qu’une branche.

Lorsqu’un navigateur génère un DOM, il parcourt donc votre document en créant une suite de nœuds pour chaque élément, de telle sorte à les répertorier et pouvoir interagir avec. Chacun de ces nœuds dispose de propriétés et de méthodes. Certains peuvent également disposer de gestionnaires d’événements qui nous permettent d’interagir avec le DOM en déclenchant des actions en fonction des actions de l’utilisateur.

Le DOM contient également un ensemble d’API que nous développerons sur un autre cours.

## structure du dom 

Lorsque l’on demande à un navigateur d’afficher une page Web, celui-ci va automatiquement créer le DOM à partir du document. Celui-ci correspond donc à une représentation de la page sous forme d’arborescence contenant des objets de type ```Node``` (les fameux "nœuds").

Prenons un exemple à partir d’un code HTML simple :

```js
<!DOCTYPE html>
<html>
<head>
    <title>My title</title>
</head>
<body>
    <h1>A heading</h1>
    <a href="">Link text</a>
</body>
</html>
```

Lorsque l’on charge ce code via le navigateur, celui-ci génère un DOM qui ressemble à ceci :

![Résultat du DOM généré par le navigateur](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/D%C3%A9veloppement%20G%C3%A9n%C3%A9rique/JavaScript/courses/0620%20-%20DOM%20-%20Introduction/images/image1.png)
*source de l’image : wikipédia*

## Les interfaces

DOM est en fait un ensemble d’interfaces qui vont pouvoir fonctionner ensemble et nous permettre notamment d’accéder et de manipuler divers éléments de nos documents en JavaScript.

Parmi les interfaces du DOM, quelques-unes vont particulièrement nous intéresser :

- L’interface ```Window``` permet d’interagir avec la fenêtre courante de l’utilisateur
- L’interface ```Event``` permet de générer des événements
- L’interface ```EventTarget``` permet de définir quels éléments pourront être soumis à des événements
- L’interface ```Node``` est donc l’interface de base pour une grande partie des objets du DOM
- L’interface ```Document``` représente le document courant
- L’interface ```Element``` qui est l’interface de base pour tous les objets d’un document
