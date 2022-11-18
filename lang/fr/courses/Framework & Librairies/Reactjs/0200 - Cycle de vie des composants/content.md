## Introduction

Dans React, le cycle de vie d'un composant représente les différentes étapes du composant au cours de son existence. React fournit des fonctions de callback pour attacher des fonctionnalités à chacune des étapes du cycle de vie de React. Dans ce chapitre, nous allons apprendre le cycle de vie (et l'API associée) d'un composant React.

### API du cycle de vie

Chaque composant React comporte trois étapes distinctes.

- **Mounting** − Le montage représente le rendu du composant React dans le nœud DOM donné.
- **Updating** − La mise à jour représente le nouveau rendu du composant React dans le nœud DOM donné pendant les changements d'état / mises à jour.
- **Unmounting** − Le démontage représente la suppression du composant React.

React fournit une collection d'événements du cycle de vie (ou API de rappel) pour attacher des fonctionnalités, qui seront exécutées au cours des différentes étapes du composant. La visualisation du cycle de vie et la séquence dans laquelle les événements du cycle de vie (APIs) sont invoqués comme indiqué ci-dessous.

![Cycle de vie React](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Reactjs/0200%20-%20Cycle%20de%20vie%20des%20composants/images/life_cycle_react.jpeg)

- ```constructor()``` − Appelé pendant la phase de construction initiale du composant React. Utilisé pour définir l'état initial et les propriétés du composant.
- ```render()``` − Appelé après que la construction du composant soit terminée. Il rend le composant dans l'instance virtuelle du DOM. Celle-ci est spécifiée comme le montage du composant dans l'arbre DOM.
- ```componentDidMount()``` − Appelé après le montage initial du composant dans l'arbre DOM. C'est le bon endroit pour appeler les points de terminaison de l'API et pour effectuer des requêtes réseau. Dans notre composant horloge, la fonction setInterval peut être définie ici pour mettre à jour l'état (date et heure actuelles) toutes les secondes.

```js
componentDidMount() { 
    this.timeFn = setInterval( () => this.setTime(), 1000); 
}
```

- ```componentDidUpdate()``` − Similaire à ```ComponentDidMount()``` mais invoqué pendant la phase de mise à jour. La demande de réseau peut être faite pendant cette phase, mais seulement lorsqu'il y a une différence entre les propriétés actuelles et précédentes du composant.

La signature de l'API est la suivante -

```js
componentDidUpdate(prevProps, prevState, snapshot)
```

- **prevProps** − Propriétés précédentes du composant.
- **prevState** − État précédent du composant.
- **snapshot** − Contenu actuel rendu.

- ```componentWillUnmount()``` − Appelé après que le composant soit démonté du DOM. C'est le bon endroit pour nettoyer l'objet. Dans notre exemple d'horloge, nous pouvons arrêter de mettre à jour la date et l'heure dans cette phase.

```js
componentDidMount() { 
    this.timeFn = setInterval( () => this.setTime(), 1000);
}
```

- ```shouldComponentUpdate()``` − Appelé pendant la phase de mise à jour. Utilisé pour spécifier si le composant doit être mis à jour ou non. Si elle renvoie false, la mise à jour n'aura pas lieu.

La signature est la suivante -

```js
shouldComponentUpdate(nextProps, nextState)
```

- **nextProps** − Propriétés à venir du composant
- **nextState** − État à venir du composant

- ```getDerivedStateFromProps``` − Appelé pendant la phase initiale et la phase de mise à jour et juste avant la méthode render(). Elle renvoie le nouvel objet d'état. Elle est rarement utilisée lorsque les modifications des propriétés entraînent un changement d'état. Elle est surtout utilisée dans un contexte d'animation où les différents états du composant sont nécessaires pour réaliser une animation fluide.

La signature de l'API est la suivante -

```js
static getDerivedStateFromProps(props, state)
```

- **props** − propriétés actuelles du composant
- **state** − État actuel du composant

Il s'agit d'une méthode statique qui n'a pas accès à cet objet.

```getSnapshotBeforeUpdate``` − Appelé juste avant que le contenu rendu ne soit transmis à l'arbre DOM. Elle est principalement utilisée pour obtenir des informations sur le nouveau contenu. Les données renvoyées par cette méthode seront transmises à la méthode ```ComponentDidUpdate()```. Par exemple, elle est utilisée pour maintenir la position de défilement de l'utilisateur dans le nouveau contenu généré. Elle renvoie la position de défilement de l'utilisateur. Cette position de défilement est utilisée par ```ComponentDidUpdate()``` pour définir la position de défilement de la sortie dans le DOM actuel.

La signature de l'API est la suivante -

```js
getSnapshotBeforeUpdate(prevProps, prevState)
```

- **prevProps** − Propriétés précédentes du composant.
- **prevState** − État précédent du composant.

## Exemple de travail de l'API du cycle de vie

Utilisons l'API du cycle de vie dans notre application react-clock-app.

Ouvrez react-clock-hook-app dans votre éditeur préféré.

Ensuite, ouvrez le fichier ```src/components/Clock.js``` et commencez à le modifier.

Ensuite, supprimez la méthode ```setInterval()``` du constructeur.

```js
constructor(props) { 
    super(props); 
    this.state = { 
        date: new Date() 
    } 
}
```

Ensuite, ajoutez la méthode ```componentDidMount()``` et appelez ```setInterval()``` pour mettre à jour la date et l'heure toutes les secondes. Stockez également la référence pour arrêter la mise à jour de la date et de l'heure plus tard.

```js
componentDidMount() { 
    this.setTimeRef = setInterval(() => this.setTime(), 1000); 
}
```

Ensuite, ajoutez la méthode ```componentWillUnmount()``` et appelez ```clearInterval()``` pour arrêter les appels de mise à jour de la date et de l'heure.

```js
componentWillUnmount() { 
    clearInterval(this.setTimeRef) 
}
```

Maintenant, nous avons mis à jour le composant Horloge et le code source complet du composant est donné ci-dessous -.

```js
import React from 'react';

class Clock extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            date: new Date()
        }      
    }
    componentDidMount() {
        this.setTimeRef = setInterval(() => this.setTime(), 1000); 
    }
    componentWillUnmount() {
        clearInterval(this.setTimeRef)
    }
    setTime() {
        this.setState((state, props) => {
            console.log(state.date);
            return {
                date: new Date()
            }
        })
    }
    render() {
        return (
            <div>
                <p>The current time is {this.state.date.toString()}</p>
            </div>
        );
    }
}
export default Clock;
```

Ensuite, ouvrez index.js et utilisez setTimeout pour supprimer l'horloge du DOM après 5 secondes.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import Clock from './components/Clock';

ReactDOM.render(
    <React.StrictMode>
        <Clock />
    </React.StrictMode>,
    document.getElementById('root')
);
setTimeout(() => {
    ReactDOM.render(
        <React.StrictMode>
            <div><p>Clock is removed from the DOM.</p></div>
        </React.StrictMode>,
        document.getElementById('root')
    );
}, 5000);
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

L'horloge sera affichée pendant 5 secondes et ensuite, elle sera retirée du DOM. En vérifiant le journal de la console, nous pouvons constater que le code de nettoyage est correctement exécuté.

## Api du cycle de vie dans l'application de gestion des dépenses

Ajoutons l'api du cycle de vie dans le gestionnaire de dépenses et enregistrons chaque fois que l'api est appelée. Cela donnera un aperçu du cycle de vie du composant.

Ouvrez l'application de gestion des dépenses dans votre éditeur préféré.

Ensuite, mettez à jour le composant ExpenseEntryItemList avec les méthodes ci-dessous.

```js
componentDidMount() {
    console.log("ExpenseEntryItemList :: Initialize :: componentDidMount :: Component mounted");
}
shouldComponentUpdate(nextProps, nextState) {
    console.log("ExpenseEntryItemList :: Update :: shouldComponentUpdate invoked :: Before update");
    return true;
}
static getDerivedStateFromProps(props, state) {
    console.log("ExpenseEntryItemList :: Initialize / Update :: getDerivedStateFromProps :: Before update");
    return null;
}
getSnapshotBeforeUpdate(prevProps, prevState) {
    console.log("ExpenseEntryItemList :: Update :: getSnapshotBeforeUpdate :: Before update");
    return null;
}
componentDidUpdate(prevProps, prevState, snapshot) {
    console.log("ExpenseEntryItemList :: Update :: componentDidUpdate :: Component updated");
}
componentWillUnmount() {
    console.log("ExpenseEntryItemList :: Remove :: componentWillUnmount :: Component unmounted");
}
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

Ensuite, vérifiez le journal de la console. Il montrera le cycle de vie de l'api pendant la phase d'initialisation comme indiqué ci-dessous.

```bash
ExpenseEntryItemList :: Initialize / Update :: getDerivedStateFromProps :: Before update 
ExpenseEntryItemList :: Initialize :: componentDidMount :: Component mounted
```

Ensuite, supprimez un élément, puis vérifiez le journal de la console. Il montrera le cycle de vie de l'api pendant la phase de mise à jour comme indiqué ci-dessous.

```bash
ExpenseEntryItemList :: Initialize / Update :: getDerivedStateFromProps :: Before update 
ExpenseEntryItemList.js:109 ExpenseEntryItemList :: Update :: shouldComponentUpdate invoked :: Before update 
ExpenseEntryItemList.js:121 ExpenseEntryItemList :: Update :: getSnapshotBeforeUpdate :: Before update 
ExpenseEntryItemList.js:127 ExpenseEntryItemList :: Update :: componentDidUpdate :: Component updated
```

Enfin, supprimez toutes les api du cycle de vie car elles peuvent nuire aux performances de l'application. L'api cycle de vie ne doit être utilisée que si la situation l'exige.