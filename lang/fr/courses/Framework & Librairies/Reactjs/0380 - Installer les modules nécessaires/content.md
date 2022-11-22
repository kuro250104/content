## Introduction

L'application utilise les bibliothèques react de tierces parties indiquées ci-dessous -

- Redux
- React Redux
- React Router
- Formik
- Redux Thunk (pour l'api async fetch)

Installez toutes les bibliothèques en utilisant le gestionnaire de paquets npm à l'aide de la commande suivante : -.

```bash
npm install --save redux react-redux react-router-dom formik redux-thunk
```

## Configurer le routeur

Ensuite, créez un nouveau fichier, Home.js, dans le dossier src/components et écrivez un composant Home de base.

```js
import React from "react";

class Home extends React.Component {
    render() {
        return (
            <div>
                <h1>Home</h1>
            </div>
        );
    }
}
export default Home;
```

Ensuite, créez un nouveau fichier, ExpenseEntryItemForm.js, dans le dossier src/components et écrivez un composant ExpenseEntryItemForm de base.

```js
import React from "react";

class ExpenseEntryItemForm extends React.Component {
    render() {
        return (
            <div>
                <h1>Expense list</h1>
            </div>
        );
    }
}
export default ExpenseEntryItemForm;
```

Ensuite, créez un nouveau fichier, ExpenseEntryItemList.js, dans le dossier src/components et écrivez un composant ExpenseEntryItemList de base.

```js
import React from "react";

class ExpenseEntryItemList extends React.Component {
    render() {
        return (
            <div>
                <h1>Expense form</h1>
            </div>
        );
    }
}
export default ExpenseEntryItemList;
```

Créez un nouveau fichier, App.css, dans le dossier src/components et ajoutez des styles génériques pour l'application.

```css
html {
    font-family: sans-serif;
}
a{
    text-decoration: none;
}
p, li, a{
    font-size: 14px;
}
nav ul {
    width: 100%;
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
    background-color: rgb(235,235,235);
}
nav li {
    float: left;
}
nav li a {
    display: block;
    color: black;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
    font-size: 16px;
}
nav li a:hover {
    background-color: rgb(187, 202, 211);
}
input[type=text], input[type=number], input[type=date], select {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}
input[type=submit] {
    width: 100%;
    background-color: #4CAF50;
    color: white;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}
input[type=submit]:hover {
    background-color: #45a049;
}
input:focus {
    border: 1px solid #d9d5e0;
}
#expenseForm div {
    border-radius: 5px;
    background-color: #f2f2f2;
    padding: 20px;
}
#expenseForm span {
    color: red;
}
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

Ensuite, ouvrez App.js et importez les dépendances du routeur.

```js
import {
    BrowserRouter as Router,
    Link,
    Switch,
    Route
} from 'react-router-dom';
```

Ensuite, importez App.css.

```js
import './App.css';
```

Ensuite, importez les composants nouvellement créés.

```js
import Home from './Home'; 
import ExpenseEntryItemList from './ExpenseEntryItemList'; 
import ExpenseEntryItemForm from './ExpenseEntryItemForm';
```

Ensuite, configurez Router dans le composant App.

```js
class App extends React.Component {
    render() {
        return (
            <Router>
                <div>
                <nav>
                    <ul>
                        <li><Link to="/">Home</Link></li>
                        <li><Link to="/list">List Expenses</Link>lt;/li>
                        <li><Link to="/add">Add Expense</Link></li>
                    </ul>
                </nav>
                <Switch>
                    <Route path="/list">
                        <div style={   { padding: "10px 0px" }   }>
                            <ExpenseEntryItemList />
                        </div>
                    </Route>
                    <Route path="/add">
                        <div style={   { padding: "10px 0px" }   }>
                            <ExpenseEntryItemForm />
                        </div>
                    </Route>
                    <Route path="/">
                            <div>
                        <Home />
                        </div>
                    </Route>
                </Switch>
                </div>
            </Router>
        );
    }
}
```

Le code source complet du composant App est donné ci-dessous -

```js
import React from "react";
import {
   BrowserRouter as Router,
   Link,
   Switch,
   Route
} from 'react-router-dom';

import './App.css';
import Home from './Home';
import ExpenseEntryItemList from './ExpenseEntryItemList';
import ExpenseEntryItemForm from './ExpenseEntryItemForm';

class App extends React.Component {
    render() {
        return (
            <Router>
                <div>
                <nav>
                    <ul>
                        <li><Link to="/">Home</Link></li>
                        <li><Link to="/list">List Expenses</Link></li>
                        <li><Link to="/add">Add Expense</Link></li>
                    </ul>
                </nav>

                <Switch>
                    <Route path="/list">
                        <div style={{ padding: "10px 0px" }}>
                            <ExpenseEntryItemList />
                        </div>
                    </Route>
                    <Route path="/add">
                        <div style={{ padding: "10px 0px" }}>
                            <ExpenseEntryItemForm />
                        </div>
                    </Route>
                    <Route path="/">
                        <div>
                            <Home />
                        </div>
                    </Route>
                </Switch>
                </div>
            </Router>
        );
    }
}
export default App;
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.