## Introduction

Faisons un peu de gestion d'événements dans notre application de dépenses. Nous pouvons essayer de mettre en évidence l'élément d'entrée des dépenses dans le tableau lorsque l'utilisateur passe le curseur dessus.

Ouvrez l'application de gestion des dépenses dans votre éditeur préféré.

Ouvrez le fichier ExpenseEntryItemList.js et ajoutez une méthode handleMouseEnter pour gérer l'événement déclenché (onMouseEnter) lorsque l'utilisateur déplace le pointeur de la souris dans les éléments de dépense (td - cellule du tableau).

```js
handleMouseEnter(e) { 
    e.target.parentNode.classList.add("highlight");
}
```

Ici,

- Le gestionnaire d'événement essaie de trouver le nœud parent (tr) du nœud cible de l'événement (td) en utilisant la méthode parentNode. La méthode parentNode est la méthode DOM standard pour trouver le parent immédiat du nœud actuel.
- Une fois le nœud parent trouvé, le gestionnaire d'événement accède à la liste des classes css attachées au nœud parent et ajoute la classe 'highlight' en utilisant la méthode add. classList est la propriété DOM standard pour obtenir la liste des classes attachées au nœud et elle peut être utilisée pour ajouter / supprimer une classe d'un nœud DOM.

Ensuite, ajoutez une méthode, handleMouseLeave, pour gérer l'événement déclenché lorsque l'utilisateur quitte le poste de dépenses.

```js
handleMouseLeave(e) { 
    e.target.parentNode.classList.remove("highlight"); 
}
```

Ici, le gestionnaire d'événements supprime la classe de surbrillance du DOM.

Ensuite, ajoutez une méthode, handleMouseOver pour vérifier où la souris est actuellement positionnée. Il est facultatif de trouver l'endroit où se trouve le pointeur de la souris dans le DOM.

```js
handleMouseOver(e) { 
    console.log("The mouse is at (" + e.clientX + ", " + e.clientY + ")"); 
}
```

Ensuite, liez tous les gestionnaires d'événements dans le constructeur du composant.

```js
this.handleMouseEnter = this.handleMouseEnter.bind(); 
this.handleMouseLeave = this.handleMouseLeave.bind(); 
this.handleMouseOver = this.handleMouseOver.bind();
```

Ensuite, attachez les gestionnaires d'événements à la balise correspondante dans la méthode de rendu.

```js
render() {
    const lists = this.props.items.map((item) =>
        <tr key={item.id} onMouseEnter={this.handleMouseEnter} onMouseLeave={this.handleMouseLeave}>
            <td>{item.name}</td>
            <td>{item.amount}</td>
            <td>{new Date(item.spendDate).toDateString()}</td>
            <td>{item.category}</td>
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
                </tr>
            </thead>
            <tbody>
                {lists}
            </tbody>
        </table>
    );
}
```

Le code final et complet de l'ExpenseEntryItemList est le suivant : -.

```js
import React from 'react';
import './ExpenseEntryItemList.css';

class ExpenseEntryItemList extends React.Component {
    constructor(props) {
        super(props);

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
    render() {
        const lists = this.props.items.map((item) =>
            <tr key={item.id} onMouseEnter={this.handleMouseEnter} onMouseLeave={this.handleMouseLeave}>
                <td>{item.name}</td>
                <td>{item.amount}</td>
                <td>{new Date(item.spendDate).toDateString()}</td>
                <td>{item.category}</td>
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

Ensuite, ouvrez le fichier css, ExpenseEntryItemList.css et ajoutez une classe css, highlight.

```css
tr.highlight td { 
    background-color: #a6a8bd; 
}
```

Ensuite, ouvrez index.js et utilisez le composant ExpenseEntryItemList.

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

L'application répondra aux événements de la souris et mettra en évidence la ligne actuellement sélectionnée.

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