Le JavaScript s’est vu implémenté la possibilité d’utiliser des classes. Cette fonctionnalité est sortie en 2015.

## Syntaxe des classes

Pour créer une classe en JavaScript, il suffit d’utiliser le mot-clé ```class```, puis d’ouvrir une paire d’accolades. C’est entre ces accolades que se placeront les différentes propriétés et méthodes de la classe.

Exemple :

```js
classe nomDeLaClasse {
	// Propriétés et méthodes
}
```

### Constructeur

La première méthode à déclarer dans une classe est le constructeur. C’est lui qui est appelé chaque fois que la classe est instanciée (appelée).

Pour déclarer un constructeur, rien de plus simple. Une fonction ```constructor()``` existe et prend en paramètres les propriétés que le constructeur recevra. 

Exemple :

```js
classe user {
	constructor(name, age) {
        let name = name;
	    let age = age;
    }
}
```

__Remarque__ : En JavaScript, une classe **n’est pas** un objet. C’est simplement, en quelque sorte, un modèle d’objet.

Pour résumer, un constructeur est une méthode spéciale qui :

- Doit avoir le nom exact suivant : ```constructor()```
- Est exécuté automatique quand un nouvel objet est créé
- Est utilisé pour initialiser les propriétés de l’objet

Si aucun constructeur n’est déclaré au moment de la création de la classe, JavaScript ajoutera automatiquement un constructeur vide. 

## Utiliser les classes

Lorsqu’une classe est créée, elle peut être utilisée pour créer un nouvel objet. 

Exemple :

```js
let utilisateur1 = new user("Joe", 25);
```

Dans cet exemple, un nouvel utilisateur est créé. Pour ce faire, la classe ```user``` est appelée grâce au mot-clé ```new```, et les propriétés ```name``` et ```age``` sont initialisées grâce au constructeur de la classe. 

__Remarque__ : Le constructeur est appelé automatiquement lorsqu’un nouvel objet est créé.

## Classes et méthodes

Pour les classes, les méthodes sont créées et s’utilisent exactement de la même manière que celle d’un objet. 

Exemple :

```js
class Car {
    constructor(name, year) {
        this.name = name;
        this.year = year;
    }
    age() {
        let date = new Date();
        return date.getFullYear() - this.year;
    }
}

let myCar = new Car("Ford", 2014);
document.getElementById("demo").innerHTML =
"My car is " + myCar.age() + " years old.";
```