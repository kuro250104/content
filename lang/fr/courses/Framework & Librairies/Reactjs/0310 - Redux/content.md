## Introduction

React redux est une bibliothèque de gestion d'état avancée pour React. Comme nous l'avons appris précédemment, React ne supporte que la gestion d'état au niveau des composants. Dans une application importante et complexe, un grand nombre de composants sont utilisés. React recommande de déplacer l'état vers le composant de niveau supérieur et de passer l'état au composant imbriqué en utilisant des propriétés. Cela aide dans une certaine mesure, mais cela devient complexe lorsque le nombre de composants augmente.

React redux intervient et aide à maintenir l'état au niveau de l'application. React redux permet à tout composant d'accéder à l'état à tout moment. De même, il permet à tout composant de modifier l'état de l'application à tout moment.

Dans ce chapitre, nous allons voir comment écrire une application React en utilisant React redux.

## Concepts

React redux maintient l'état de l'application dans un endroit unique appelé Redux store. Le composant React peut obtenir l'état le plus récent à partir du magasin ainsi que changer l'état à tout moment. Redux fournit un processus simple pour obtenir et définir l'état actuel de l'application et implique les concepts suivants.

- **Store** − L'endroit central pour stocker l'état de l'application.
- **Actions** − L'action est un objet simple avec le type de l'action à effectuer et l'entrée (appelée payload) nécessaire pour effectuer l'action. Par exemple, une action pour ajouter un article dans le magasin contient ADD_ITEM comme type et un objet avec les détails de l'article comme charge utile. L'action peut être représentée comme -

```js
{ 
    type: 'ADD_ITEM', 
    payload: { name: '..', ... }
}
```

- **Reducers** − Les réducteurs sont des fonctions pures utilisées pour créer un nouvel état basé sur l'état existant et l'action en cours. Il renvoie l'état nouvellement créé. Par exemple, dans le scénario d'ajout d'un élément, il crée une nouvelle liste d'éléments et fusionne les éléments de l'état et du nouvel élément et renvoie la liste nouvellement créée.
- **Action creators** − Le créateur d'action crée une action avec le type d'action approprié et les données nécessaires pour l'action et renvoie l'action. Par exemple, le créateur de l'action addItem renvoie l'objet ci-dessous -

```js
{ 
    type: 'ADD_ITEM', 
    payload: { name: '..', ... }
}
```

- **Component** − Le composant peut se connecter au magasin pour obtenir l'état actuel et envoyer une action au magasin afin que ce dernier exécute l'action et mette à jour son état actuel.

Le flux de travail d'un magasin redux typique peut être représenté comme suit.

![flux de travail d'un magasmin redux](https://raw.githubusercontent.com/Microleadoff/content/master/lang/fr/courses/Framework%20%26%20Librairies/Reactjs/0310%20-%20Redux/images/image1.png)

- Le composant React s'abonne au magasin et obtient le dernier état pendant l'initialisation de l'application.
- Pour changer l'état, le composant React crée l'action nécessaire et la distribue.
- Le réducteur crée un nouvel état basé sur l'action et le renvoie. Le magasin se met à jour avec le nouvel état.
- Une fois l'état modifié, le magasin envoie l'état mis à jour à tous ses composants abonnés.

## Redux API

Redux fournit une seule api, connect qui connectera un composant au magasin et permettra au composant d'obtenir et de définir l'état du magasin.

La signature de l'API de connexion est -

```js
function connect(mapStateToProps?, mapDispatchToProps?, mergeProps?, options?)
```

Tous les paramètres sont facultatifs et la fonction renvoie un HOC (higher order component). Un composant d'ordre supérieur est une fonction qui enveloppe un composant et renvoie un nouveau composant.

```js
let hoc = connect(mapStateToProps, mapDispatchToProps) 
let connectedComponent = hoc(component)
```

Voyons les deux premiers paramètres qui seront suffisants pour la plupart des cas.

- **mapStateToProps** − Accepte une fonction avec la signature ci-dessous.

```js
(state, ownProps?) => Object
```

Ici, state désigne l'état actuel du magasin et Object désigne les nouveaux props du composant. Il est appelé chaque fois que l'état du magasin est mis à jour.

```js
(state) => { prop1: this.state.anyvalue }
```

- **mapDispatchToProps** − Accepte une fonction avec la signature ci-dessous.

```js
Object | (dispatch, ownProps?) => Object
```

Ici, dispatch fait référence à l'objet de distribution utilisé pour distribuer l'action dans le magasin redux et Object fait référence à une ou plusieurs fonctions de distribution en tant que props du composant.

```js
(dispatch) => {
    addDispatcher: (dispatch) => dispatch({ type: 'ADD_ITEM', payload: { } }),
    removeispatcher: (dispatch) => dispatch({ type: 'REMOVE_ITEM', payload: { } }),
}
```

## Composant du fournisseur

React Redux fournit un composant Provider et son seul but est de rendre le magasin Redux disponible à tous ses composants imbriqués connectés au magasin en utilisant l'API connect. L'exemple de code est donné ci-dessous -

```js
import React from 'react'
import ReactDOM from 'react-dom'
import { Provider } from 'react-redux'
import { App } from './App'
import createStore from './createReduxStore'

const store = createStore()

ReactDOM.render(
    <Provider store={store}>
        <App />
    </Provider>,
    document.getElementById('root')
)
```

Maintenant, tous les composants à l'intérieur du composant App peuvent avoir accès au magasin Redux en utilisant l'API de connexion.

### Exemple de travail

Recréons notre application de gestion des dépenses et utilisons le concept React redux pour maintenir l'état de l'application.

Tout d'abord, créez une nouvelle application React, react-message-app en utilisant le bundler Create React App ou Rollup en suivant les instructions du chapitre Création d'une application React.

Ensuite, installez Redux et la bibliothèque React redux.

```bash
npm install redux react-redux --save
```

Ensuite, installez la bibliothèque uuid pour générer un identifiant unique pour les nouvelles dépenses.

```bash
npm install uuid --save
```

Ensuite, ouvrez l'application dans votre éditeur préféré.

Ensuite, créez le dossier src sous le répertoire racine de l'application.

Ensuite, créez un dossier actions sous le dossier src.

Ensuite, créez un fichier, types.js, dans le dossier src/actions et commencez à le modifier.

Ensuite, ajoutez deux types d'action, une pour ajouter une dépense et une pour supprimer une dépense.

```js
export const ADD_EXPENSE = 'ADD_EXPENSE'; 
export const DELETE_EXPENSE = 'DELETE_EXPENSE';
```

Ensuite, créez un fichier, index.js, sous le dossier src/actions pour ajouter une action et commencer à éditer.

Ensuite, importez uuid pour créer un identifiant unique.

```js
import { v4 as uuidv4 } from 'uuid';
```

Ensuite, importez les types d'action.

```js
import { ADD_EXPENSE, DELETE_EXPENSE } from './types';
```

Ensuite, ajoutez une nouvelle fonction pour retourner le type d'action pour ajouter une dépense et exportez-la.

```js
export const addExpense = ({ name, amount, spendDate, category }) => ({
    type: ADD_EXPENSE,
    payload: {
        id: uuidv4(),
        name,
        amount,
        spendDate,
        category
    }
});
```

Ici, la fonction attend un objet de dépenses et renvoie le type d'action ADD_EXPENSE ainsi que des informations sur les dépenses.

Ensuite, ajoutez une nouvelle fonction pour retourner le type d'action pour la suppression d'une dépense et exportez-la.

```js
export const deleteExpense = id => ({
    type: DELETE_EXPENSE,
    payload: {
        id
    }
});
```

Ici, la fonction attend l'identifiant de l'élément de dépense à supprimer et renvoie le type d'action 'DELETE_EXPENSE' ainsi que l'identifiant de la dépense.

Le code source complet de l'action est donné ci-dessous -

```js
import { v4 as uuidv4 } from 'uuid';
import { ADD_EXPENSE, DELETE_EXPENSE } from './types';

export const addExpense = ({ name, amount, spendDate, category }) => ({
    type: ADD_EXPENSE,
    payload: {
        id: uuidv4(),
        name,
        amount,
        spendDate,
        category
    }
});
export const deleteExpense = id => ({
    type: DELETE_EXPENSE,
    payload: {
        id
    }
});
```

Ensuite, créez un nouveau dossier, reducers, sous le dossier src.

Ensuite, créez un fichier, index.js sous src/reducers pour écrire la fonction de réduction et commencez à l'éditer.

Ensuite, importez les types d'action.

```js
import { ADD_EXPENSE, DELETE_EXPENSE } from '../actions/types';
```

Ensuite, ajoutez une fonction, expensesReducer pour faire la fonction réelle d'ajout et de mise à jour des dépenses dans le magasin redux.

```js
export default function expensesReducer(state = [], action) {
    switch (action.type) {
        case ADD_EXPENSE:
            return [...state, action.payload];
        case DELETE_EXPENSE:
            return state.filter(expense => expense.id !== action.payload.id);
        default:
            return state;
    }
}
```

Le code source complet du réducteur est donné ci-dessous -

```js
import { ADD_EXPENSE, DELETE_EXPENSE } from '../actions/types';

export default function expensesReducer(state = [], action) {
    switch (action.type) {
        case ADD_EXPENSE:
            return [...state, action.payload];
        case DELETE_EXPENSE:
            return state.filter(expense => expense.id !== action.payload.id);
        default:
            return state;
    }
}
```

Ici, le réducteur vérifie le type d'action et exécute le code correspondant.

Ensuite, créez un dossier de composants sous le dossier src.

Ensuite, créez un fichier, ExpenseEntryItemList.css, dans le dossier src/components et ajoutez un style générique pour les tableaux html.

```css
html {
    font-family: sans-serif;
}
table {
    border-collapse: collapse;
    border: 2px solid rgb(200,200,200);
    letter-spacing: 1px;
    font-size: 0.8rem;
}
td, th {
    border: 1px solid rgb(190,190,190);
    padding: 10px 20px;
}
th {
    background-color: rgb(235,235,235);
}
td, th {
    text-align: left;
}
tr:nth-child(even) td {
    background-color: rgb(250,250,250);
}
tr:nth-child(odd) td {
    background-color: rgb(245,245,245);
}
caption {
    padding: 10px;
}
tr.highlight td { 
    background-color: #a6a8bd;
}
```

Ensuite, créez un fichier, ExpenseEntryItemList.js, dans le dossier src/components et commencez à le modifier.

Ensuite, importez React et la bibliothèque React redux.

```js
import React from 'react'; 
import { connect } from 'react-redux';
```

Ensuite, importez le fichier ExpenseEntryItemList.css.

```js
import './ExpenseEntryItemList.css';
```

Ensuite, importez les créateurs d'actions.

```js
import { deleteExpense } from '../actions'; 
import { addExpense } from '../actions';
```

Ensuite, créez une classe, ExpenseEntryItemList et appelez le constructeur avec les props.

```js
class ExpenseEntryItemList extends React.Component {
    constructor(props) {
        super(props);
    }
}
```

Ensuite, créez la fonction mapStateToProps.

```js
const mapStateToProps = state => {
    return {
        expenses: state
    };
};
```

Ici, nous avons copié l'état d'entrée aux dépenses props du composant.

Ensuite, créez la fonction mapDispatchToProps.

```js
const mapDispatchToProps = dispatch => {
    return {
        onAddExpense: expense => {
            dispatch(addExpense(expense));
        },
        onDelete: id => {
            dispatch(deleteExpense(id));
        }
    };
};
```

Ici, nous avons créé deux fonctions, l'une pour envoyer la fonction d'ajout de dépense (addExpense) et l'autre pour envoyer la fonction de suppression de dépense (deleteExpense) et nous avons mappé ces fonctions aux props du composant.

Ensuite, exportez le composant en utilisant l'api connect.

```js
export default connect(
    mapStateToProps,
    mapDispatchToProps
)(ExpenseEntryItemList);
```

Maintenant, le composant obtient trois nouvelles propriétés données ci-dessous -

- **expenses** − liste des dépenses
- **onAddExpense** − pour envoyer la fonction addExpense
- **onDelete** − fonction pour envoyer la fonction deleteExpense

Ensuite, ajoutez quelques dépenses dans le magasin redux dans le constructeur en utilisant la propriété onAddExpense.

```js
if (this.props.expenses.length == 0)
{
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
    items.forEach((item) => {
        this.props.onAddExpense(
            { 
                name: item.name, 
                amount: item.amount, 
                spendDate: item.spendDate, 
                category: item.category 
            }
        );
    })
}
```

Ensuite, ajoutez un gestionnaire d'événement pour supprimer le poste de dépense en utilisant l'identifiant de la dépense.

```js
handleDelete = (id,e) => {
    e.preventDefault();
    this.props.onDelete(id);
}
```

Ici, le gestionnaire d'événements appelle le répartiteur onDelete, qui appelle deleteExpense avec l'identifiant de la dépense.

Ensuite, ajoutez une méthode pour calculer le montant total de toutes les dépenses.

```js
getTotal() {
    let total = 0;
    for (var i = 0; i < this.props.expenses.length; i++) {
        total += this.props.expenses[i].amount
    }
    return total;
}
```

Ensuite, ajoutez la méthode ```render()``` et listez les postes de dépenses sous forme de tableau.

```js
render() {
    const lists = this.props.expenses.map(
        (item) =>
        <tr key={item.id}>
            <td>{item.name}</td>
            <td>{item.amount}</td>
            <td>{new Date(item.spendDate).toDateString()}</td>
            <td>{item.category}</td>
            <td><a href="#"
                onClick={(e) => this.handleDelete(item.id, e)}>Remove</a></td>
        </tr>
    );
    return (
        <div>
            <table>
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
        </div>
    );
}
```

Ici, nous définissons le gestionnaire d'événement handleDelete pour supprimer la dépense du magasin.

Le code source complet du composant ExpenseEntryItemList est donné ci-dessous -

```js
import React from 'react';
import { connect } from 'react-redux';
import './ExpenseEntryItemList.css';
import { deleteExpense } from '../actions';
import { addExpense } from '../actions';

class ExpenseEntryItemList extends React.Component {
    constructor(props) {
        super(props);

        if (this.props.expenses.length == 0){
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
            items.forEach((item) => {
                this.props.onAddExpense(
                { 
                    name: item.name, 
                    amount: item.amount, 
                    spendDate: item.spendDate, 
                    category: item.category 
                }
                );
            })
        }
    }
    handleDelete = (id,e) => {
        e.preventDefault();
        this.props.onDelete(id);
    }
    getTotal() {
        let total = 0;
        for (var i = 0; i < this.props.expenses.length; i++) {
            total += this.props.expenses[i].amount
        }
        return total;
    }
    render() {
        const lists = this.props.expenses.map((item) =>
            <tr key={item.id}>
                <td>{item.name}</td>
                <td>{item.amount}</td>
                <td>{new Date(item.spendDate).toDateString()}</td>
                <td>{item.category}</td>
                <td><a href="#"
                onClick={(e) => this.handleDelete(item.id, e)}>Remove</a></td>
            </tr>
        );
        return (
            <div>
                <table>
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
            </div>
        );
    }
}
const mapStateToProps = state => {
    return {
        expenses: state
    };
};
const mapDispatchToProps = dispatch => {
    return {
        onAddExpense: expense => {
            dispatch(addExpense(expense));
        },
        onDelete: id => {
            dispatch(deleteExpense(id));
        }
    };
};
export default connect(
    mapStateToProps,
    mapDispatchToProps
)(ExpenseEntryItemList);
```

Ensuite, créez un fichier, App.js, dans le dossier src/components et utilisez le composant ExpenseEntryItemList.

```js
import React, { Component } from 'react';
import ExpenseEntryItemList from './ExpenseEntryItemList';

class App extends Component {
    render() {
        return (
            <div>
                <ExpenseEntryItemList />
            </div>
        );
    }
}
export default App;
```

Ensuite, créez un fichier, index.js, dans le dossier src.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import { createStore } from 'redux';
import { Provider } from 'react-redux';
import rootReducer from './reducers';
import App from './components/App';

const store = createStore(rootReducer);

ReactDOM.render(
    <Provider store={store}>
        <App />
    </Provider>,
    document.getElementById('root')
);
```

Ici,

- Créer un magasin en utilisant createStore en attachant notre reducer.
- Nous avons utilisé le composant Provider de la bibliothèque React redux et défini le magasin comme props, ce qui permet à tous les composants imbriqués de se connecter au magasin en utilisant l'API connect.

Enfin, créez un dossier public sous le dossier racine et créez le fichier index.html.

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>React Containment App</title>
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

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

En cliquant sur le lien de suppression, l'article sera retiré de la boutique redux.