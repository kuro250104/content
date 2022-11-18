## Introduction

Dans les applications modernes, les développeurs rencontrent de nombreuses situations où une liste d'éléments (par exemple, des tâches à accomplir, des commandes, des factures, etc. React fournit une technique claire, intuitive et facile pour créer une interface utilisateur basée sur des listes. React utilise deux fonctionnalités existantes pour accomplir cette fonction.

- La méthode map intégrée de JavaScript.
- Expression React en jsx.

La fonction map accepte une collection et une fonction de mappage. La fonction de mappage sera appliquée à chacun des éléments de la collection et les résultats seront utilisés pour générer une nouvelle liste.

Par exemple, déclarez un tableau JavaScript contenant 5 nombres aléatoires, comme indiqué ci-dessous -

```js
let list = [10, 30, 45, 12, 24]
```

Maintenant, appliquez une fonction anonyme, qui double son entrée comme indiqué ci-dessous -

```js
result = list.map((input) => input * 2);
```

Ensuite, la liste résultante est -

```js
[20, 60, 90, 24, 48]
```

Pour rafraîchir l'expression React, créons une nouvelle variable et assignons un élément React.

```js
var hello = <h1>Hello!</h1> 
var final = <div>{helloElement}</div>
```

Maintenant, l'expression React, hello sera fusionnée avec final et generate,

```html
<div><h1>Hello!</h1></div>
```

Appliquons ce concept à la création d'un composant permettant d'afficher une collection de postes de dépenses sous forme de tableau.

Ouvrez notre application de gestion des dépenses dans votre éditeur préféré.

Ensuite, créez un fichier, ExpenseEntryItemList.css dans le dossier src/components pour inclure les styles du composant.

Ensuite, créez un fichier, ExpenseEntryItemList.js dans le dossier src/components pour créer le composant ExpenseEntryItemList.

Ensuite, importez la bibliothèque React et la feuille de style.

```js
import React from 'react'; 
import './ExpenseEntryItemList.css';
```

Ensuite, créez la classe ExpenseEntryItemList et appelez la fonction du constructeur.

```js
class ExpenseEntryItemList extends React.Component {  
    constructor(props) { 
        super(props); 
    } 
}
```

Ensuite, créez une fonction de rendu.

```js
render() { 
}
```

Next, Use map method to generate a collection of HTML table rows each representing a single expense entry item in the list.

```js
render() {
    const lists = this.props.items.map( (item) => 
        <tr key={item.id}>
            <td>{item.name}</td>
            <td>{item.amount}</td>
            <td>{new Date(item.spendDate).toDateString()}</td>
            <td>{item.category}</td>
        </tr>
    );
}
```

Ici, la clé identifie chaque ligne et elle doit être unique dans la liste.

Ensuite, dans la méthode ```render()```, créez un tableau HTML et incluez l'expression lists dans la section rows.

```js
return (
   <table>
      <thead>
         <tr>
            <th>Item</th>
            <th>Amount</th>
            <th>Date</th>
            <th>Category</th>
         </tr>
      </thead>
      <tbody>
         {lists}
      </tbody>
   </table>
);
```

Enfin, exportez le composant.

```js
export default ExpenseEntryItemList;
```

Maintenant, nous avons créé avec succès le composant pour rendre les postes de dépenses dans le tableau HTML. Le code complet est le suivant -

```js
import React from 'react';
import './ExpenseEntryItemList.css'

class ExpenseEntryItemList extends React.Component {
    constructor(props) {
        super(props);
    }
    render() {
        const lists = this.props.items.map( (item) => 
            <tr key={item.id}>
                <td>{item.name}</td>
                <td>{item.amount}</td>
                <td>{new Date(item.spendDate).toDateString()}</td>
                <td>{item.category}</td>
            </tr>
        );
        return (
            <table>
                <thead>
                <tr>
                    <th>Item</th>
                    <th>Amount</th>
                    <th>Date</th>
                    <th>Category</th>
                </tr>
                </thead>
                <tbody>
                {lists}
                </tbody>
            </table>
        );
    }
}
export default ExpenseEntryItemList;
```

Ensuite, ouvrez index.js et importez notre composant ExpenseEntryItemList nouvellement créé.

```js
import ExpenseEntryItemList from './components/ExpenseEntryItemList'
```

Ensuite, déclarez une liste (d'éléments d'entrée de dépenses) et remplissez-la avec des valeurs aléatoires dans le fichier index.js.

```js
const items = [
    { id: 1, name: "Pizza", amount: 80, spendDate: "2020-10-10", category: "Food" },
    { id: 1, name: "Grape Juice", amount: 30, spendDate: "2020-10-12", category: "Food" },
    { id: 1, name: "Cinema", amount: 210, spendDate: "2020-10-16", category: "Entertainment" },
    { id: 1, name: "Java Programming book", amount: 242, spendDate: "2020-10-15", category: "Academic" },
    { id: 1, name: "Mango Juice", amount: 35, spendDate: "2020-10-16", category: "Food" },
    { id: 1, name: "Dress", amount: 2000, spendDate: "2020-10-25", category: "Cloth" },
    { id: 1, name: "Tour", amount: 2555, spendDate: "2020-10-29", category: "Entertainment" },
    { id: 1, name: "Meals", amount: 300, spendDate: "2020-10-30", category: "Food" },
    { id: 1, name: "Mobile", amount: 3500, spendDate: "2020-11-02", category: "Gadgets" },
    { id: 1, name: "Exam Fees", amount: 1245, spendDate: "2020-11-04", category: "Academic" }
]
```

Ensuite, utilisez le composant ExpenseEntryItemList en passant les éléments par les attributs d'éléments.

```js
ReactDOM.render(
    <React.StrictMode>
        <ExpenseEntryItemList items={items} />
    </React.StrictMode>,
    document.getElementById('root')
);
```

Le code complet de index.js est le suivant -

```js
import React from 'react';
import ReactDOM from 'react-dom';
import ExpenseEntryItemList from './components/ExpenseEntryItemList'

const items = [
    { id: 1, name: "Pizza", amount: 80, spendDate: "2020-10-10", category: "Food" },
    { id: 1, name: "Grape Juice", amount: 30, spendDate: "2020-10-12", category: "Food" },
    { id: 1, name: "Cinema", amount: 210, spendDate: "2020-10-16", category: "Entertainment" },
    { id: 1, name: "Java Programming book", amount: 242, spendDate: "2020-10-15", category: "Academic" },
    { id: 1, name: "Mango Juice", amount: 35, spendDate: "2020-10-16", category: "Food" },
    { id: 1, name: "Dress", amount: 2000, spendDate: "2020-10-25", category: "Cloth" },
    { id: 1, name: "Tour", amount: 2555, spendDate: "2020-10-29", category: "Entertainment" },
    { id: 1, name: "Meals", amount: 300, spendDate: "2020-10-30", category: "Food" },
    { id: 1, name: "Mobile", amount: 3500, spendDate: "2020-11-02", category: "Gadgets" },
    { id: 1, name: "Exam Fees", amount: 1245, spendDate: "2020-11-04", category: "Academic" }
]
ReactDOM.render(
    <React.StrictMode>
        <ExpenseEntryItem item={item} />
    </React.StrictMode>,
    document.getElementById('root')
);
```

Ensuite, ouvrez ExpenseEntryItemList.css et ajoutez un style pour le tableau.

```js
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
```

Ensuite, servez l'application en utilisant la commande npm.

```js
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

| **Article** | **Montant** | **Date** | **Catégorie** |
| --- | --- | --- | --- |
| Pizza | 80 | Sat Oct 10 2020 | Alimentation |
| Grape Juice | 30 | Mon Oct 12 2020 | Alimentation |
| Cinema | 210 | Fri Oct 16 2020 | Divertissement |
| Java Programming book | 242 | Thu Oct 15 2020 | Académique |
| Mango Juice | 35 | Fri Oct 16 2020 | Alimentation |
| Dress | 2000 | Sun Oct 25 2020 | Tissu |
| Tour | 2555 | Thu Oct 29 2020 | Divertissement |
| Meals | 300 | Fri Oct 30 2020 | Alimentation |
| Mobile | 3500 | Mon Nov 02 2020 | Gadgets |
| Exam Fees | 1245 | Wed Nov 04 2020 | Académique |