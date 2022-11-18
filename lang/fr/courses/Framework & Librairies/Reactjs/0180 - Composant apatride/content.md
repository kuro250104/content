## Introduction

Un composant React avec un état interne est appelé composant Stateful et un composant React sans aucune gestion d'état interne est appelé composant Stateless. React recommande de créer et d'utiliser autant de composants sans état que possible et de ne créer des composants avec état que lorsque c'est absolument nécessaire. De plus, React ne partage pas l'état avec les composants enfants. Les données doivent être transmises au composant enfant par le biais des propriétés de ce dernier.

Voici un exemple de transmission d'une date au composant FormattedDate.

```js
<FormattedDate value={this.state.item.spend_date} />
```

L'idée générale est de ne pas compliquer à l'excès la logique de l'application et de n'utiliser les fonctions avancées que lorsque cela est nécessaire.

## Créer un composant à état

Créons une application React pour afficher la date et l'heure actuelles.

Tout d'abord, créez une nouvelle application React, react-clock-app en utilisant le bundler Create React App ou Rollup en suivant les instructions du chapitre Créer une application React.

Ensuite, ouvrez l'application dans votre éditeur préféré.

Ensuite, créez le dossier src sous le répertoire racine de l'application.

Ensuite, créez un dossier de composants sous le dossier src.

Ensuite, créez un fichier Clock.js dans le dossier src/components et commencez à le modifier.

Ensuite, importez la bibliothèque React.

```js
import React from 'react';
```

Ensuite, créez le composant Clock.

```js
class Clock extends React.Component { 
    constructor(props) { 
        super(props); 
    } 
}
```

Ensuite, initialiser l'état avec la date et l'heure actuelles.

```js
constructor(props) { 
    super(props); 
    this.state = { 
        date: new Date() 
    } 
}
```

Ensuite, ajoutez une méthode, setTime() pour mettre à jour l'heure actuelle -

```js
setTime() { 
    console.log(this.state.date); 
    this.setState((state, props) => (
        {
            date: new Date() 
        } 
    )) 
}
```

Ensuite, utilisez la méthode JavaScript, setInterval et appelez la méthode ```setTime()``` toutes les secondes pour vous assurer que l'état du composant est mis à jour toutes les secondes.

```js
constructor(props) { 
    super(props); 
    this.state = { 
        date: new Date() 
    } 
    setInterval( () => this.setTime(), 1000); 
}
```

Ensuite, créez une fonction de rendu.

```js
render() {
}
```

Ensuite, mettez à jour la méthode ```render()`` pour afficher l'heure actuelle.

```js
render() {
    return (
        <div><p>The current time is {this.state.date.toString()}</p></div>
    );
}
```

Enfin, exportez le composant.

```js
export default Clock;
```

Le code source complet du composant Clock est le suivant -

```js
import React from 'react';

class Clock extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            date: new Date()
        }      
        setInterval( () => this.setTime(), 1000);
    }
    setTime() {
        console.log(this.state.date);
        this.setState((state, props) => (
            {
                date: new Date()
            }
        ))
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

Ensuite, créez un fichier, index.js, dans le dossier src et utilisez le composant Clock.

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
```

Enfin, créez un dossier public sous le dossier racine et créez le fichier index.html.

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>Clock</title>
    </head>
    <body>
        <div id="root"></div>
        <script type="text/JavaScript" src="./index.js"></script>
    </body>
</html>
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée. L'application affichera l'heure et la mettra à jour toutes les secondes.

```bash
The current time is Wed Nov 11 2020 10:10:18 GMT+0530(Indian Standard Time)
```

L'application ci-dessus fonctionne bien mais affiche une erreur dans la console.

```bash
Can't call setState on a component that is not yet mounted.
```

Le message d'erreur indique que le setState ne doit être appelé qu'après le montage du composant.

### Qu'est-ce que le montage ?

Le composant React a un cycle de vie et le montage est l'une des étapes de ce cycle de vie. Nous en apprendrons plus sur le cycle de vie dans les prochains cours.

## Introduire l'état dans l'application de gestion des dépenses

Introduisons la gestion d'état dans l'application de gestion des dépenses en ajoutant une fonction simple pour supprimer un élément de dépenses.

Ouvrez l'application de gestion des dépenses dans votre éditeur préféré.

Ensuite, ouvrez le fichier ExpenseEntryItemList.js.

Ensuite, il faut initialiser l'état du composant avec les éléments de dépense transmis aux composants par le biais des propriétés.

```js
this.state = { 
    items: this.props.items 
}
```

Ensuite, ajoutez l'étiquette de suppression dans la méthode render().

```html
<thead>
    <tr>
        <th>Item</th>
        <th>Amount</th>
        <th>Date</th>
        <th>Category</th>
        <th>Remove</th>
    </tr>
</thead>
```

Ensuite, mettez à jour les listes dans la méthode ```render()``` pour inclure le lien de suppression. De plus, utilisez les éléments de l'état (this.state.items) au lieu des éléments des propriétés (this.props.items).

```js
const lists = this.state.items.map((item) =>
    <tr key={item.id} onMouseEnter={this.handleMouseEnter} onMouseLeave={this.handleMouseLeave}>
        <td>{item.name}</td>
        <td>{item.amount}</td>
        <td>{new Date(item.spendDate).toDateString()}</td>
        <td>{item.category}</td>
        <td><a href="#" onClick={(e) =>  this.handleDelete(item.id, e)}>Remove</a></td>
    </tr>
);
```

Ensuite, mettez en œuvre la méthode handleDelete, qui supprimera le poste de dépense concerné de l'état.

```js
handleDelete = (id, e) => {
    e.preventDefault();
    console.log(id);

    this.setState((state, props) => {
        let items = [];

        state.items.forEach((item, idx) => {
            if(item.id != id)
                items.push(item)
        })
        let newState = {
            items: items
        }
        return newState;
    })
}
```

Ici,

Les postes de dépenses sont récupérés à partir de l'état actuel du composant. Les postes de dépenses actuels sont parcourus en boucle pour trouver le poste référencé par l'utilisateur en utilisant l'identifiant du poste. Créer une nouvelle liste de postes avec tous les postes de dépenses sauf celui référencé par l'utilisateur.

Ensuite, ajoutez une nouvelle ligne pour afficher le montant total des dépenses.

```html
<tr>
    <td colSpan="1" style={{ textAlign: "right" }}>Total Amount</td>
    <td colSpan="4" style={{ textAlign: "left" }}>
        {this.getTotal()}
    </td>
</tr>
```

Ensuite, implémentez la méthode getTotal() pour calculer le montant total des dépenses.

```js
getTotal() {
    let total = 0;
    for(var i = 0; i < this.state.items.length; i++) {
        total += this.state.items[i].amount
    }
    return total;
}
```

Le code complet de la méthode ```render()``` est le suivant -

```js
render() {
    const lists = this.state.items.map((item) =>
        <tr key={item.id} onMouseEnter={this.handleMouseEnter} onMouseLeave={this.handleMouseLeave}>
            <td>{item.name}</td>
            <td>{item.amount}</td>
            <td>{new Date(item.spendDate).toDateString()}</td>
            <td>{item.category}</td>
            <td><a href="#" 
                onClick={(e) =>  this.handleDelete(item.id, e)}>Remove</a></td>
        </tr>
    );
    return (
        <table onMouseOver={this.handleMouseOver}>
            <thead>
                <tr>
                <th>Item</th>
                <th>Amount</th>
                <th>Date</th>
                <th>Category</th>
                <th>Remove</th>
                </tr>
            </thead>
            <tbody>
                {lists}
                <tr>
                <td colSpan="1" style={{ textAlign: "right" }}>Total Amount</td>
                <td colSpan="4" style={{ textAlign: "left" }}>
                    {this.getTotal()}
                </td> 
                </tr>
            </tbody>
        </table>
    );
}
```

Enfin, le code mis à jour de l'ExpenseEntryItemList est le suivant -

```js
import React from 'react';
import './ExpenseEntryItemList.css';

class ExpenseEntryItemList extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            items: this.props.items
        }
        this.handleMouseEnter = this.handleMouseEnter.bind();
        this.handleMouseLeave = this.handleMouseLeave.bind();
        this.handleMouseOver = this.handleMouseOver.bind();
    }
    handleMouseEnter(e) {
        e.target.parentNode.classList.add("highlight");
    }
    handleMouseLeave(e) {
        e.target.parentNode.classList.remove("highlight");
    }
    handleMouseOver(e) {
        console.log("The mouse is at (" + e.clientX + ", " + e.clientY + ")");
    }
    handleDelete = (id, e) => {
        e.preventDefault();
        console.log(id);
        this.setState((state, props) => {
            let items = [];
            state.items.forEach((item, idx) => {
                if(item.id != id)
                items.push(item)
            })
            let newState = {
                items: items
            }
            return newState;
        })
    }
    getTotal() {
        let total = 0;
        for(var i = 0; i < this.state.items.length; i++) {
            total += this.state.items[i].amount
        }
        return total;
    }
    render() {
        const lists = this.state.items.map((item) =>
            <tr key={item.id} onMouseEnter={this.handleMouseEnter} onMouseLeave={this.handleMouseLeave}>
                <td>{item.name}</td>
                <td>{item.amount}</td>
                <td>{new Date(item.spendDate).toDateString()}</td>
                <td>{item.category}</td>
                <td><a href="#" 
                onClick={(e) =>  this.handleDelete(item.id, e)}>Remove</a></td>
            </tr>
        );
        return (
            <table onMouseOver={this.handleMouseOver}>
                <thead>
                <tr>
                    <th>Item</th>
                    <th>Amount</th>
                    <th>Date</th>
                    <th>Category</th>
                    <th>Remove</th>
                </tr>
                </thead>
                <tbody>
                {lists}
                <tr>
                    <td colSpan="1" style={{ textAlign: "right" }}>Total Amount</td>
                    <td colSpan="4" style={{ textAlign: "left" }}>
                        {this.getTotal()}
                    </td> 
                </tr>
                </tbody>
            </table>
        );
    }
}
export default ExpenseEntryItemList;
```

Ensuite, mettez à jour le fichier index.js et incluez le composant ExpenseEntyItemList.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import ExpenseEntryItemList from './components/ExpenseEntryItemList'

const items = [
    { id: 1, name: "Pizza", amount: 80, spendDate: "2020-10-10", category: "Food" },
    { id: 2, name: "Grape Juice", amount: 30, spendDate: "2020-10-12", category: "Food" },
    { id: 3, name: "Cinema", amount: 210, spendDate: "2020-10-16", category: "Entertainment" },
    { id: 4, name: "Java Programming book", amount: 242, spendDate: "2020-10-15", category: "Academic" },
    { id: 5, name: "Mango Juice", amount: 35, spendDate: "2020-10-16", category: "Food" },
    { id: 6, name: "Dress", amount: 2000, spendDate: "2020-10-25", category: "Cloth" },
    { id: 7, name: "Tour", amount: 2555, spendDate: "2020-10-29", category: "Entertainment" },
    { id: 8, name: "Meals", amount: 300, spendDate: "2020-10-30", category: "Food" },
    { id: 9, name: "Mobile", amount: 3500, spendDate: "2020-11-02", category: "Gadgets" },
    { id: 10, name: "Exam Fees", amount: 1245, spendDate: "2020-11-04", category: "Academic" }
]
ReactDOM.render(
    <React.StrictMode>
        <ExpenseEntryItemList items={items} />
    </React.StrictMode>,
    document.getElementById('root')
);
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

Enfin, pour supprimer un poste de dépense, cliquez sur le lien de suppression correspondant. Cela supprimera l'élément correspondant et rafraîchira l'interface utilisateur.