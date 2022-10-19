Comme beaucoup de langages de programmation, le JavaScript permet de créer des objets et de les utiliser. 

La notion d’objet est très importante en JavaScript, et si elle est bien comprise, alors le JavaScript en lui-même sera bien compris.

## Les objets

Tout, absolument tout en JavaScript peut être considéré comme un objet. Toutes les valeurs, sauf les valeurs primitives, sont considérées comme des objets. 

## Les valeurs primitives

Une valeur primitive est une valeur qui n’a ni propriété, ni méthode. 

Un type de donnée primitif est une donnée qui a une valeur primitive. En JavaScript, il y a 5 types de données primitifs :

- **string**
- **number**
- **boolean**
- **null**
- **undefined**

Ces valeurs primitives sont immuables. Elles ne peuvent pas être modifiées.

## Les objets sont des variables.

Les variables en JavaScript peuvent contenir une seule valeur. 

Exemple :

``` js
let x = 3.14;
```

Cependant, les variables JavaScript peuvent également contenir plusieurs variables. En fait, les objets sont également des variables, et ce sont les objets qui contiennent plusieurs valeurs.

Les valeurs d’objet sont écrites en pair clé valeur, les deux séparés par les deux points : **cle:valeur**.

Exemple :

``` js
let person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
```

__Remarque__ : Il est d’usage d’utiliser le mot-clé ```const``` pour déclarer un objet.

## Les propriétés d’objet

Les clés sont en fait des propriétés d’objet. 

Exemple :

``` js
const person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
```

Dans cet exemple, **firstName**, **lasName**, **age** et **eyeColor** sont les propriétés de l’objet **person**.

## Les méthodes d’objet

Les méthodes sont des actions pouvant être effectuées sur les objets. Il s’agit de fonctions. 

Les propriétés d’objet peuvent être des valeurs primitives, d’autres objets et des fonctions. 

Donc, une **méthode d’objet** est une propriété définie comme fonction. 

## Créer un objet JavaScript

Le JavaScript permet aux développeurs de définir et créer leurs propres objets. 

Il existe plusieurs moyens de créer des objets en JavaScript :

- Créer un seul objet en utilisant une expression littérale
- Créer un seul objet en utilisant le mot-clé ```new```
- Définir un constructeur d’objet et ensuite créer un objet du type de celui construit
- Créer un objet en utilisant ```Object.create()```

### Utiliser une expression littérale pour créer un objet

C’est le moyen le plus facile pour créer un objet en JavaScript. En utilisant cette manière de faire, cet objet est à la fois défini et créé en une seule déclaration.

Une expression littérale pour créer un objet est un ensemble de paire clé :valeurs placées entre accolades.

Exemple :

``` js
const person = {firstName:"John", lastName:"Doe  ", age:50, eyeColor:"blue"};
```

Les espaces et les retours à la ligne ne sont pas pris en compte. Ainsi, pour des raisons de lisibilité du code, il est courant de voir une expression littérale d’objet écrite comme suite :

``` js
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};
```

### Utiliser le mot-clé new

Pour créer un nouvel objet en JavaScript, il est également possible d’utiliser ```new Object()```.

Exemple :

``` js
const person = new Object();
person.firstName = "John";
person.lastName = "Doe";
person.age = 50;
person.eyeColor = "blue";
```

Ce code, en fait, fait exactement la même chose que l’expression littérale objet du point précédent. L’objet est déclaré à la première ligne avec ```const person = new Object()```.

Ensuite, chaque propriété est déclarée et initialisée en utilisant cette syntaxe : ```objet.nomDeLaPropriété = valeur```.

__Remarque__ : Pour des raisons de lisibilité, de simplicité et de vitesse d'exécution, il est plutôt recommandé d’utiliser la méthode littérale pour créer un objet.

## Les objets JavaScript sont muables

Les objets sont muables, car ils sont accessibles par référence et non par valeur. 

L’exemple ci-dessous copie l’objet person dans une nouvelle variable :

``` js
const x = person;
```

Ici, la variable **x n’est pas une copie de l’objet person**. La variable **x** est l’objet **person**. Par conséquent, tout changement apporté à **x** change l’objet **person**, parce que **x** et **person** sont le même objet.

Exemple :

``` js
const person = {
    firstName:"John",
    lastName:"Doe",
    age:50, eyeColor:"blue"
}
const x = person;
x.age = 10;
```

Dans ce dernier exemple, la dernière ligne change à la fois la valeur de ```x.age``` et celle de ```person.age```.