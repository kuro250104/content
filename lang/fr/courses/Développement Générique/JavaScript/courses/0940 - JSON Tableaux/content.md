JSON permet de stocker des tableaux. Il existe ensuite des expressions JavaScript permettant de convertir ces tableaux JSON en array JavaScript.

## Les expressions JSON en array

Ceci est une chaîne de caractères :

```js
'["Ford", "BMW", "Fiat"]'
```

À l’intérieur de cette chaîne de caractères, il y a un array.

Les arrays en JSON sont quasiment similaires à ceux en JavaScript. Cependant, en JSON les valeurs d’array doivent être de type string, nombre, objet, array, booléen ou null.

## Les arrays JavaScript

Il est possible de créer un array JavaScript depuis une expression de ce type :

```js
myArray = ["Ford", "BMW", "Fiat"];
```

Il est possible de créer un array Javascript en parsant un string JSON :

```js
myJSON = '["Ford", "BMW", "Fiat"]';
myArray = JSON.Parse(myJSON);
```

## Accéder aux valeurs d’array

Il est possible d’accéder aux valeurs de l’array grâce aux index :

```js
myArray[0];
```

## Les arrays dans les objets

Les objets peuvent contenir des arrays :

```js
{
    "name":"John",
    "age":30,
    "cars":["Ford", "BMW", "Fiat"]
}
```

Il est possible d’accéder aux valeurs grâce aux index :

```js
myObj.cars[0];
```

## Boucler sur un array

Il est possible de boucler sur un array JavaScript en utilisant la boucle ```for in``` :

```js
for (let i in myObj.cars) {
    x += myObj.cars[i];
}
```

Il est également possible de boucler sur un array en utilisant la boucle ```for``` :

```js
for (let i = 0; i < myObj.cars.length; i++) {
    x += myObj.cars[i];
}
```