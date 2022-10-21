Les écouteurs d’événements permettent de vérifier si un événement se produit sur un élément, afin d’exécuter ou non un bout de code particulier. 

## La méthode addEventListener()

Cette méthode permet d’attribuer un écouteur d’événement à un élément, sans pour autant écraser les écouteurs déjà existants. Il est possible d’ajouter autant d’écouteurs d’événement que souhaité sur un même élément. Il est également possible d’ajouter plusieurs fois le même type d’événement sur un même élément.

De plus, il est possible d’ajouter un écouteur d’événement à n’importe quel élément du DOM, et pas seulement à un élément HTML. Par exemple, il est possible d’ajouter un écouteur d’événement sur l’objet global ```window```.

### Syntaxe

Voici la syntaxe permettant d’ajouter un écouteur d’événement à un élément :

```js
element.addEventListener(event, function, useCapture);
```

Le premier argument est le type d’événement que JavaScript doit écouter. Le deuxième paramètre est la fonction à exécuter lorsque l’événement se produit. Le troisième argument est optionnel. 

Exemple :

```js
document.getElementById("myBtn").addEventListener("click", displayDate);
```

Dans cet exemple, la fonction ```displayDate()``` est exécutée lorsque l’utilisateur clique sur le bouton ```myBtn```.

__Remarque__ : Lorsque les événements sont traités directement en JavaScript, il n’y a pas de préfixe “on” avant le nom de l’événement.

## Ajouter un écouteur d’événement à un élément

Il est possible d’attribuer un écouteur d’événement à un élément HTML.

Exemple :

```js
element.addEventListener("click", function(){ alert("Hello World!"); });
```

Ici, l’alerte ```Hello World``` s’affiche lorsque l’utilisateur clique sur l’élément. Dans cet exemple, une fonction anonyme est utilisée, mais il est également possible d’appeler une fonction externe. 

Exemple :

```js
element.addEventListener("click", myFunction);

function myFunction() {
    alert ("Hello World!");
}
```

Cet exemple fait exactement la même chose que le précédent, à la différence près que cette fois, c’est une fonction externe qui est invoquée. 

## Ajouter plusieurs écouteurs à un même élément

La méthode ```addEventListener()``` permet d’ajouter plusieurs écouteurs d’événements sans écraser ceux déjà existants. 

Exemple :

```js
element.addEventListener("change", myFunction);
element.addEventListener("click", mySecondFunction);
```

__Remarque__ : Il est possible d’ajouter le même événement ou un événement différent à un élément.

## Ajouter un écouteur à l’objet window

La méthode ```addEventListener()``` permet d’ajouter un écouteur d’événement sur n’importe quel élément du DOM, comme, par exemple, l’objet global ```window```, ou tout autre objet supportant les événements.

Exemple :

```js
window.addEventListener("resize", function(){
    document.getElementById("demo").innerHTML = sometext;
});
```

## Passer des paramètres

Lorsque des paramètres sont passés, il est recommandé d’utiliser une fonction anonyme qui appelle la fonction spécifique, avec les paramètres. 

Exemple :

```js
element.addEventListener("click", function(){ myFunction(p1, p2); });
```

## Capture de l’événement ou événement "bouillonnant" ?

Il y a deux moyens de propagation d’un événement dans le DOM : la capture ou le "bouillonnement".

La propagation d’un événement est une manière de définir dans quel ordre les événements vont se produire sur un élément. Par exemple, un élément ```<p>``` est contenu dans une ```<div>```. L’utilisateur clique sur le paragraphe. Quel événement de type ```click``` doit être déclenché en premier ?

En "*bouillonnement*", l'événement de l’élément se trouvant le plus à l’intérieur est déclenché en premier, puis celui de l’élément le plus à l’extérieur. En reprenant l’exemple ci-dessus, c’est donc l’événement sur l’élément ```<p>``` qui est déclenché en premier, puis, après seulement, l’événement de l’élément ```<div>```.

En *capture*, en revanche, c’est l’inverse. C’est l’événement de l’élément le plus à l’extérieur qui est déclenché en premier. Donc, dans le cas de l’exemple, c’est d’abord l’événement de la ```<div>``` qui est déclenché, puis celui du ```<p>```.

La méthode ```addEventListener``` permet de spécifier si l’événement doit être capturé ou si un “bouillonnement” doit être effectué. C’est le troisième paramètre optionnel de la méthode :

```js
addEventListener(event, function, useCapture);
```

Par défaut, ce paramètre est initialisé à **false**, donc un “bouillonnement” est exercé. Si l’événement doit plutôt être capturé, il suffit de passer **true** comme troisième paramètre de la méthode.

Exemple :

```js
document.getElementById("myP").addEventListener("click", myFunction, true);
document.getElementById("myDiv").addEventListener("click", myFunction, true);
```

Dans cet exemple, les deux événements sont capturés, car **true** est passé comme troisième paramètre de la méthode ```addEventListener()```.

## La méthode removeEventListener()

Cette méthode permet de supprimer un écouteur d'événement attribué à un élément avec ```addEventListener()```. ```removeEventListener()``` prend en paramètre le nom de l’événement a supprimé, ainsi qu’une éventuelle fonction à exécuter.

Exemple :

```js
element.removeEventListener("mousemove", myFunction);
```

Dans cet exemple, l’événement **mousemove**, attribué à un élément, est supprimé.