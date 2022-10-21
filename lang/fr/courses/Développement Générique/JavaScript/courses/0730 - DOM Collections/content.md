Ce cours traite du type d’objet ```HTMLCollection```.

## L’objet HTMLCollection

Lorsque la méthode ```getElementsByTagName()``` est invoquée, celle-ci retourne en fait un objet de type ```HTMLCollection```. Il s’agit d’une liste - ou collection -, similaire à un array, des éléments HTML retournés.

Exemple :

```js
const myCollection = document.getElementsByTagName("p");
```

Dans cet exemple, ce sont tous les paragraphes du document qui sont sélectionnés. Cependant, grâce à l’index - qui, pour rappel, commence toujours à 0 -, il est possible de sélectionner un paragraphe en particulier.

Exemple :

```js
myCollection[1];
```

Dans cet exemple, le deuxième paragraphe du document est sélectionné.

## Longueur de HTMLCollection

La propriété ```length``` retourne le nombre d’entrées contenues dans le ```HTMLCollection```. ```length``` est utile lorsqu’il y a besoin de “boucler” sur les éléments d’une collection. 

Exemple :

```js
const myCollection = document.getElementsByTagName("p");
for (let i = 0; i < myCollection.length; i++) {
    myCollection[i].style.color = "red";
}
```

__Remarque__ : ```HTMLCollection``` n’est pas un array. Cela y ressemble, mais ce n’en est pas un.