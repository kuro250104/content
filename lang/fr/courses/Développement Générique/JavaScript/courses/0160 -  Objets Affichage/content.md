Lorsqu’un développeur cherche à afficher un objet, le résultat retourné est le suivant : ```[object Object]```.

Le problème est qu’en général, il y a plutôt besoin d’afficher les variables et méthodes d’un objet. 

Pour ce faire, plusieurs solutions existent :

- Afficher les propriétés de l’objet par nom
- Afficher les propriétés d’un objet dans une boucle
- Afficher l’objet en utilisant ```Object.value()```
- Afficher l’objet en utilisant ```JSON.stringify()```

## Afficher les propriétés d’un objet

Les propriétés d’un objet peuvent être affichées sous forme de chaînes de caractères.

Exemple :

```js
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

document.getElementById("demo").innerHTML =
person.name + "," + person.age + "," + person.city;
```

Cet exemple retourne les valeurs des propriétés : “**John, 30, New York**”.

## Afficher l’objet dans une boucle

Pour afficher le contenu des différentes propriétés de l’objet, la boucle **for in** peut être utilisée afin de parcourir les différentes propriétés :

Exemple :

```js
const person = {
    name: "John",
    age: 30,
    city: "New York"
};

let txt = "";
for (x in person){
    txt += person[x] + " ";
}

document.getElementById("demo").innerHTML = txt;
```

Cet exemple affiche bien le contenu des propriétés de l’objet ```person```.

## Utiliser Object.value()

Un objet Javascript peut être converti en array grâce à la méthode ```Object.value()```.

Exemple :

```js
const person = {
    name: "John",
    age: 30,
    city: "New York"
};

const myArray = Object.values(person);
```

**myArray** est désormais un tableau prêt à être affiché.

## Utiliser JSON.stringify()

N’importe quel objet JavaScript peut-être converti en chaîne de caractères grâce à la méthode ```JSON.stringify()```.

Exemple :

```js
const person = {
    name: "John",
    age: 30,
    city: "New York"
};

let myString = JSON.stringify(person);
```

```myString``` est désormais une chaîne de caractères prête à être affichée. Le résultat retourné est affiché au format JSON : 

```json
{"name":"John","age":50,"city":"New York"}
```

__Remarque__ : JSON est inclus avec JavaScript et supporté par tous les navigateurs “connus”.

## Convertir les dates en string (stringify)

La méthode ```JSON.stringify()``` peut également convertir les dates en chaînes de caractères, affichées au format JSON.

Exemple :

```js
const person = {
    name: "John",
    today: new Date()
};

let myString = JSON.stringify(person);
document.getElementById("demo").innerHTML = myString;
```

## Convertir les fonctions en string (stringify)

La méthode ```JSON.stringify``` en elle-même ne peut pas convertir une fonction en chaîne de caractères pour l’afficher. Ce problème peut être réglé en convertissant la fonction en chaîne de caractères avant de la stringifier. 

Exemple :

```js
const person = {
    name: "John",
    age: function () {return 30;}
};
person.age = person.age.toString();

let myString = JSON.stringify(person);
document.getElementById("demo").innerHTML = myString;
```

## Convertir les arrays en chaîne de caractères

```JSON.stringify``` permet également de retourner les entrées d’un tableau sous forme de chaîne de caractères. 

__Remarque__ : Lorsque cette méthode est utilisée, le tableau est retourné avec la notation suivante : ```[“entrée 1”, “entrée2”]```.

Exemple :

```js
const arr = ["John", "Peter", "Sally", "Jane"];

let myString = JSON.stringify(arr);
document.getElementById("demo").innerHTML = myString;
```