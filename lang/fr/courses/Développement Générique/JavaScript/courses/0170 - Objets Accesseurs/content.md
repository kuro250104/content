Les accesseurs - également appelés getters et setters - ont été rendus disponibles en 2009, avec la version 5 du langage. Ils permettent de créer des accesseurs pour les propriétés d’un objet.

## Les getters - le mot-clé get

Ce mot-clé est utilisé pour créer une méthode permettant d’obtenir la valeur d’une propriété. 

Exemple :

```js
// Création de l'objet
const person = {
    firstName: "John",
    lastName: "Doe",
    language: "en",
    get lang() {
        return this.language;
    }
};

// Affichage de la donnée 
document.getElementById("demo").innerHTML = person.lang;
```

Dans cet exemple, la première partie du code crée l’objet ```person```. Au sein de cet objet, une méthode de type getter est créée grâce au mot-clé ```get```.

Ensuite, dans la seconde partie du code, la langue de la personne est affichée grâce à l’accesseur créé dans l’objet.

## Les setters - le mot-clé set

Dans certains langages de programmation, les valeurs des propriétés d’un objet ne sont, pour des raisons de sécurité du code, jamais modifiées directement par le développeur.

Ainsi, pour pouvoir modifier les valeurs des propriétés, il est donc nécessaire d’utiliser un accesseur de type setter afin de modifier cette valeur, après que la méthode ait fait quelques vérifications afin de s’assurer que la nouvelle valeur transmise est fiable. 

C’est là que le mot-clé ```set``` entre en jeu.

Exemple :

```js
const person = {
    firstName: "John",
    lastName: "Doe",
    language: "",
    set lang(lang) {
        this.language = lang;
    }
};

// Modifie la valeur de la propriété via le setter
person.lang = "en";

// Affichage de la nouvelle valeur
document.getElementById("demo").innerHTML = person.language;
```

## Qualité des données

JavaScript peut assurer une meilleure sécurité, intégrité et qualité des données grâce aux accesseurs, car les données transmises pour modifier une propriété sont d’abord vérifiées par le setter avant d’être envoyées à la propriété.

## Pourquoi utiliser les getters et les setters

Voici les principales raisons pour lesquelles utiliser les getters et les setters :

- Cela permet une meilleure syntaxe, plus simple et plus lisible.
- Cela permet une syntaxe similaire pour les propriétés et les méthodes.
- Cela permet d’assurer une meilleure qualité, intégrité et sécurité des données transmises.

## Object.defineProperty()

Cette méthode peut également être utilisée pour créer des accesseurs.

Exemple :

```js
// Définit l'objet
const obj = {counter : 0};

// Définit les setters
Object.defineProperty(obj, "reset", {
    get : function () {this.counter = 0;}
});
Object.defineProperty(obj, "increment", {
    get : function () {this.counter++;}
});
Object.defineProperty(obj, "decrement", {
    get : function () {this.counter--;}
});
Object.defineProperty(obj, "add", {
    set : function (value) {this.counter += value;}
});
Object.defineProperty(obj, "subtract", {
    set : function (value) {this.counter -= value;}
});
```