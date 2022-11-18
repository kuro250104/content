## Introduction

Comme nous l'avons appris précédemment, le composant React maintient et expose son état à travers this.state du composant. React fournit une seule API pour maintenir l'état du composant. Cette API est this.setState(). Elle accepte soit un objet JavaScript, soit une fonction qui renvoie un objet JavaScript.

La signature de l'API setState est la suivante -

```js
this.setState( { ... object ...} );
```

Un exemple simple pour définir / mettre à jour le nom est le suivant -

```js
this.setState( { name: 'John' } )
```

La signature de la fonction setState with est la suivante -

```js
this.setState( (state, props) => 
    ... function returning JavaScript object ... );
```

Ici,

- state désigne l'état actuel du composant React
- props fait référence aux propriétés actuelles du composant React.

React recommande d'utiliser l'API setState avec une fonction car elle fonctionne correctement dans un environnement asynchrone. Au lieu de la fonction lambda, une fonction JavaScript normale peut également être utilisée.

```js
this.setState( function(state, props) { 
    return ... JavaScript object ... 
}
```

Un exemple simple de mise à jour du montant à l'aide de la fonction est le suivant -

```js
this.setState( (state, props) => ({ 
    amount: this.state.amount + this.props.additionaAmount 
})
```

L'état de React ne doit pas être modifié directement par la variable membre this.state et la mise à jour de l'état par la variable membre n'entraîne pas un nouveau rendu du composant.

Une caractéristique particulière de l'API d'état React est qu'elle sera fusionnée avec l'état existant au lieu de remplacer l'état. Par exemple, nous pouvons mettre à jour un seul des champs d'état à la fois au lieu de mettre à jour l'objet entier. Cette fonctionnalité donne au développeur la flexibilité nécessaire pour manipuler facilement les données d'état.

Une caractéristique particulière de l'API d'état React est qu'elle sera fusionnée avec l'état existant au lieu de remplacer l'état. Par exemple, nous pouvons mettre à jour un seul des champs d'état à la fois au lieu de mettre à jour l'objet entier. Cette fonctionnalité donne au développeur la flexibilité nécessaire pour manipuler facilement les données d'état.

Par exemple, considérons que l'état interne contient un enregistrement d'étudiant.

```js
{ 
    name: 'John', age: 16 
}
```

Nous pouvons mettre à jour uniquement l'âge en utilisant l'API setState, qui fusionnera automatiquement le nouvel objet avec l'objet existant du dossier de l'étudiant.

```js
this.setState( (state, props) => ({ 
    age: 18 
});
```