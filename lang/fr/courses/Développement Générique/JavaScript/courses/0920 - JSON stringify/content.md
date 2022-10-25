Lorsque des données sont envoyées à un serveur, celles-ci doivent être au format texte. JavaScript a une fonction intégrée permettant de convertir des données au format texte - JSON - afin de pouvoir les envoyer au serveur. 

## Convertir un objet JavaScript

L’objet JavaScript suivant doit être converti au format texte :

```js
const obj = {name: "John", age: 30, city: "New York"};
```

La fonction JavaScript ```JSON.stringify()``` doit alors être utilisée pour convertir cet objet en format JSON.

Exemple :

```js
const myJSON = JSON.stringify(obj);
```

Une chaîne de caractères suivant la notation JSON est retournée grâce à cette fonction.

## Convertir un array JavaScript

Il est également possible de convertir un array JavaScript en chaîne de caractères respectant la notation JSON.

L’array suivant est utilisé comme exemple :

```js
const arr = ["John", "Peter", "Sally", "Jane"];
```

La fonction ```JSON.stringify()``` est également utilisée pour le convertir en chaîne de caractères.

Exemple :

```js
const myJSON = JSON.stringify(arr);
```

## Stocker des données

JSON rend également possible de stocker des objets JavaScript comme texte.

Exemple :

```js
// Stockage des données :
const myObj = {name: "John", age: 31, city: "New York"};
const myJSON = JSON.stringify(myObj);
localStorage.setItem("testJSON", myJSON);

// Récupération des données :
let text = localStorage.getItem("testJSON");
let obj = JSON.parse(text);
document.getElementById("demo").innerHTML = obj.name;
```

## Exceptions

### Convertir les dates

Au format JSON, les dates ne sont pas autorisées. En revanche, la fonction ```JSON.stringify()``` va convertir une date en chaîne de caractères.

Exemple :

```js
const obj = {name: "John", today: new Date(), city : "New York"};
const myJSON = JSON.stringify(obj);
```

Par la suite, lorsque le fichier est récupéré, il est possible de convertir à nouveau la date afin de pouvoir l’utiliser comme un objet JavaScript.

## Convertir les fonctions

En JSON, les fonctions ne sont pas autorisées comme valeurs d’objet. Par conséquent, la fonction ```JSON.stringify()``` supprimera toute fonction présente ; à la fois la clé et la valeur. 

Exemple :

```js
const obj = {name: "John", age: function () {return 30;}, city: "New York"};
const myJSON = JSON.stringify(obj);
```

Ce problème peut être évité si la fonction est convertie en chaîne de caractères avant que ```JSON.stringify()``` soit utilisée. 

Exemple :

```js
const obj = {name: "John", age: function () {return 30;}, city: "New York"};
obj.age = obj.age.toString();
const myJSON = JSON.stringify(obj);
```