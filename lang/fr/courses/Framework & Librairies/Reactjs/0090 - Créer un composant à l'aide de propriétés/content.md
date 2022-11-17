## Introduction

Modifions notre composant ExpenseEntryItem et essayons d'utiliser les propriétés.

Ouvrez notre application de gestion des dépenses dans votre éditeur préféré.

Ouvrez le fichier ExpenseEntryItem dans le dossier src/components.

Introduire la fonction de construction avec des accessoires d'arguments.

```js
constructor(props) { 
    super(props); 
}
```

Ensuite, changez la méthode de rendu et introduisez la valeur de props.

```js
render() {
    return (
        <div>
            <div><b>Item:</b> <em>{this.props.name}</em></div>
            <div><b>Amount:</b> <em>{this.props.amount}</em></div>
            <div><b>Spend date:</b> 
                <em>{this.props.spenddate.tostring()}</em></div>
            <div><b>Category:</b> <em>{this.props.category}</em></div>
        </div>
    );
}
```

Ici,

- name représente le nom de l'élément de type String.
- montant représente le montant de l'article de type nombre
- spendDate représente la date de dépense de l'élément de type date.
- La catégorie représente la catégorie de l'élément de type String.

Maintenant, nous avons réussi à mettre à jour le composant en utilisant les propriétés.

```js
import React from 'react'
import './ExpenseEntryItem.css';
import styles from './ExpenseEntryItem.module.css'

class ExpenseEntryItem extends React.Component {
    constructor(props) {
        super(props);
    }
    render() {
        return (
            <div>
                <div><b>Item:</b> <em>{this.props.name}</em></div>
                <div><b>Amount:</b> <em>{this.props.amount}</em></div>
                <div><b>Spend Date:</b> 
                <em>{this.props.spendDate.toString()}</em></div>
                <div><b>Category:</b> <em>{this.props.category}</em></div>
            </div>
        );
    }
}
export default ExpenseEntryItem;
```

Maintenant, nous pouvons utiliser le composant en passant toutes les propriétés à travers les attributs dans le fichier index.js.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import ExpenseEntryItem from './components/ExpenseEntryItem'

const name = "Grape Juice"
const amount = 30.00
const spendDate = new Date("2020-10-10")
const category = "Food"

ReactDOM.render(
    <React.StrictMode>
        <ExpenseEntryItem
            name={name}
            amount={amount}
            spendDate={spendDate}
            category={category} />
    </React.StrictMode>,
    document.getElementById('root')
);
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

Le code complet pour le faire en utilisant le CDN dans une page web est le suivant -.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8" />
        <title>React based application</title>
    </head>
    <body>
        <div id="react-app"></div>
        
        <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script>
        <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script>
        <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
        <script type="text/babel">
            class ExpenseEntryItem extends React.Component {
                constructor(props) {
                super(props);
                }
                render() {
                return (
                    <div>
                        <div><b>Item:</b> <em>{this.props.name}</em></div>
                        <div><b>Amount:</b> <em>{this.props.amount}</em></div>
                        <div><b>Spend Date:</b> <em>{this.props.spendDate.toString()}</em></div>
                        <div><b>Category:</b> <em>{this.props.category}</em></div>
                    </div>
                );
                }
            }
            const name = "Grape Juice"
            const amount = 30.00
            const spendDate = new Date("2020-10-10")
            const category = "Food"

            ReactDOM.render(
                <ExpenseEntryItem 
                name={name} 
                amount={amount} 
                spendDate={spendDate} 
                category={category} />,
                document.getElementById('react-app') );
        </script>
    </body>
</html>
```

## Objets en tant que propriétés

Dans ce chapitre, nous allons apprendre à utiliser les objets JavaScript comme attributs.

Ouvrez notre application de gestion des dépenses dans votre éditeur préféré.

Ensuite, ouvrez le fichier ExpenseEntryItem.js.

Ensuite, modifiez la méthode ```render()``` et accédez à l'objet d'entrée item via la propriété ```this.props.item```.

```js
render() {
    return (
        <div>
            <div><b>Item:</b> <em>{this.props.item.name}</em></div>
            <div><b>Amount:</b> <em>{this.props.item.amount}</em></div>
            <div><b>Spend Date:</b> 
                <em>{this.props.item.spendDate.toString()}</em></div>
            <div><b>Category:</b> <em>{this.props.item.category}</em></div>
        </div>
    );
}
```

Ensuite, ouvrez index.js et représentez l'élément d'entrée des dépenses dans un objet JavaScript.

```js
const item = { 
    id: 1, 
    name : "Grape Juice", 
    amount : 30.5, 
    spendDate: new Date("2020-10-10"), 
    category: "Food" 
}
```

Ensuite, transmettez l'objet au composant en utilisant la syntaxe des accolades ({}) dans les attributs du composant.

```js
<ExpenseEntryItem item={item} />
```

Le code complet de index.js est le suivant -

```js
import React from 'react';
import ReactDOM from 'react-dom';
import ExpenseEntryItem from './components/ExpenseEntryItem'

const item = {
    id: 1, 
    name : "Grape Juice", 
    amount : 30.5, 
    spendDate: new Date("2020-10-10"), 
    category: "Food" 
}
ReactDOM.render(
    <React.StrictMode>
    <ExpenseEntryItem item={item} />
    </React.StrictMode>,
    document.getElementById('root')
);
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

Le code complet pour le faire en utilisant le CDN dans une page web est le suivant -.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8" />
        <title>React based application</title>
    </head>
    <body>
        <div id="react-app"></div>
        
        <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script>
        <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script>
        <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
        <script type="text/babel">
            class ExpenseEntryItem extends React.Component {
                constructor(props) {
                super(props);
                }
                render() {
                return (
                    <div>
                        <div><b>Item:</b> 
                            <em>{this.props.item.name}</em></div>
                        <div><b>Amount:</b> 
                            <em>{this.props.item.amount}</em></div>
                        <div><b>Spend Date:</b> 
                            <em>{this.props.item.spendDate.toString()}</em>
                        </div>
                        <div><b>Category:</b> 
                            <em>{this.props.item.category}</em>
                        </div>
                    </div>
                );
                }
            }
            const item = {
                id: 1, 
                name : "Grape Juice", 
                amount : 30.5, 
                spendDate: new Date("2020-10-10"), 
                category: "Food" 
            }
            ReactDOM.render(
                <ExpenseEntryItem item={item} />,
                document.getElementById('react-app') 
            );
        </script>
    </body>
</html>
```