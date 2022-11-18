## Introduction

La gestion des événements est l'une des caractéristiques importantes d'une application web. Elle permet à l'utilisateur d'interagir avec l'application. React supporte tous les événements disponibles dans une application web. La gestion des événements React est très similaire aux événements DOM avec peu de changements. Apprenons comment gérer les événements dans une application React dans ce chapitre.

Voyons le processus de traitement d'un événement dans un composant React, étape par étape.

- Définir une méthode de gestion d'événement pour traiter l'événement donné.

```js
log() { 
    console.log("Event is fired"); 
}
```

React fournit une syntaxe alternative utilisant la fonction lambda pour définir le gestionnaire d'événements. La syntaxe lambda est -

```js
log = () =;> { 
    console.log("Event is fired"); 
}
```

Si vous voulez connaître la cible de l'événement, alors ajoutez un argument e dans la méthode handler. React enverra les détails de la cible de l'événement à la méthode handler.

```js
log(e) { 
    console.log("Event is fired"); 
    console.log(e.target); 
}
```

La syntaxe lambda alternative est -

```js
log = (e) => { 
    console.log("Event is fired"); 
    console.log(e.target); 
}
```

Si vous voulez envoyer des détails supplémentaires pendant un événement, ajoutez les détails supplémentaires comme argument initial, puis ajoutez l'argument (e) pour la cible de l'événement.

```js
log(extra, e) { 
    console.log("Event is fired"); 
    console.log(e.target); 
    console.log(extra); 
    console.log(this); 
}
```

La syntaxe lambda alternative est la suivante -

```js
log = (extra, e) => { 
    console.log("Event is fired"); 
    console.log(e.target); 
    console.log(extra); 
    console.log(this); 
}
```

Liez la méthode du gestionnaire d'événements dans le constructeur du composant. Cela garantira la disponibilité de cette méthode dans le gestionnaire d'événements.

```js
constructor(props) { 
    super(props); 
    this.logContent = this.logContent.bind(this); 
}
```

Si le gestionnaire d'événements est défini dans une syntaxe lambda alternative, la liaison n'est pas nécessaire. Ce mot-clé sera automatiquement lié à la méthode du gestionnaire d'événements.

Définissez la méthode de gestion de l'événement pour l'événement spécifique, comme indiqué ci-dessous.

```html
<div onClick={this.log}> ... </div>
```

Pour définir des arguments supplémentaires, liez la méthode du gestionnaire d'événements, puis passez les informations supplémentaires comme deuxième argument.

```html
<div onClick={this.log.bind(this, extra)}> ... </div>
```

La syntaxe alternative de lambda est la suivante -

```html
<div onClick={this.log(extra, e)}> ... </div>
```

Ici,

- Créer un composant sensible aux événements
- Introduire des événements dans l'application Expense manager