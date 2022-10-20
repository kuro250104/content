Ce cours traite du type d’objet ```NodeList```.

## L’objet NodeList

Ce type d’objet retourne la liste - ou collection - des nœuds extraits d’un document. Ce type d’objet est **quasiment** similaire à ```HTMLCollection```.

Exemple :

```js
const myNodeList = document.querySelectorAll("p");
```

Tous les paragraphes ```<p>``` du document sont recherchés. Ensuite, celui désiré est sélectionné avec l’index.

Exemple :

```js
myNodeList[1]
```

## Longueur de la liste de nœuds

La propriété ```length``` retourne le nombre de nœuds contenus dans une liste de nœuds.

Exemple :

```js
myNodelist.length
```

Utiliser cette propriété devient particulièrement utile lorsqu’il y a besoin de boucler sur les nœuds dans une liste de nœuds.

Exemple :

```js
const myNodelist = document.querySelectorAll("p");
for (let i = 0; i < myNodelist.length; i++) {
    myNodelist[i].style.color = "red";
}
```

Cet exemple permet de changer la couleur des paragraphes contenus dans la liste de nœuds.

## Différence en HTMLCollection et NodeList

```HTMLCollection``` est une collection d’éléments HTML ; tandis que ```NodeList``` est une liste de nœuds contenus dans un document. En fait, ils sont tous les deux similaires.

Ces deux types d’objets retournent tous les deux une liste d’objets ressemblant à un array. Ils ont également tous les deux accès à la propriété ```length``` permettant de retourner le nombre d’éléments qu’ils contiennent. Tous fournissent des index - commençant à 0 - permettant, comme pour un array, d’accéder à un élément de la liste. 

Cependant, voici la différence entre ces deux types d’objets : ```HTMLCollection``` permet un accès aux items contenus grâce au nom de l’item, de l’id ou de l’index. ```NodeList```, quant à lui, ne permet l’accès aux items contenus que grâce à l’index.

De plus, il n’y a que ```NodeList``` qui contient les nœuds d’attributs et les nœuds textes.

__Remarque__ : Bien que cela y ressemble, ```NodeList``` n’est pas un array. Bien sûr, les entrées contenues dans la liste sont accessibles par l’index, mais les méthodes utilisables avec un array - telle que ```push()```, ```valueOf()```, ```pop()``` ou ```join()``` ne le sont pas avec ```NodeList```.