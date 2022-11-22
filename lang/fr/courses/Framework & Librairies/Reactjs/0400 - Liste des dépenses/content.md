## Introduction

Ouvrez ExpenseEntryItemList.js et importez connect de la bibliothèque redux.

```js
import { connect } from 'react-redux';
```

Ensuite, importez les actions addExpenseList et deleteExpense.

```js
import { getExpenseList, deleteExpense } from '../actions/expenseActions';
```

Ensuite, ajoutez le constructeur avec les props.

```js
constructor(props) { 
    super(props); 
}
```

Ensuite, appelez getExpenseList dans le cycle de vie de componentDidMount().

```js
componentDidMount() { 
    this.props.getExpenseList(); 
}
```

Ensuite, écrivez une méthode pour gérer l'option de suppression des dépenses.

```js
handleDelete = (id,e) => { 
    e.preventDefault(); 
    this.props.deleteExpense(id); 
}
```

Maintenant, écrivons une fonction, getTotal, pour calculer le total des dépenses.

```js
getTotal() {
    let total = 0;
    if (this.props.expenses != null) {
        for (var i = 0; i < this.props.expenses.length; i++) {
            total += this.props.expenses[i].amount
        }
    }
    return total;
}
```

Ensuite, mettez à jour la méthode de rendu et listez les postes de dépenses.

```js
render() {
    let lists = [];

    if (this.props.expenses != null) {
        lists = this.props.expenses.map((item) =>
            <tr key={item.id}>
                <td>{item.name}</td>
                <td>{item.amount}</td>
                <td>{new Date(item.spendDate).toDateString()}</td>
                <td>{item.category}</td>
                <td><a href="#"
                onClick={(e) => this.handleDelete(item.id, e)}>Remove</a></td>
            </tr>
        );
    }
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

Ensuite, écrivez les méthodes mapStateToProps et mapDispatchToProps.

```js
const mapStateToProps = state => {
    return {      
        expenses: state.data
    };
};
const mapDispatchToProps = {
    getExpenseList,
    deleteExpense
};
```

Ici, nous avons mappé l'élément de dépenses du magasin redux à la propriété expenses et attaché distpatcher, getExpenseList et deleteExpense aux propriétés du composant.

Enfin, connectez le composant au magasin Redux en utilisant l'api connect.

```js
export default connect(
    mapStateToProps,
    mapDispatchToProps
)(ExpenseEntryItemList);
```

Le code source complet de l'application est donné ci-dessous -

```js
import React from "react";
import { connect } from 'react-redux';
import { getExpenseList, deleteExpense } from '../actions/expenseActions';

class ExpenseEntryItemList extends React.Component {
    constructor(props) {
        super(props);
    }
    componentDidMount() {
        this.props.getExpenseList();
    }
    handleDelete = (id, e) => {
        e.preventDefault();
        this.props.deleteExpense(id);
    }
    getTotal() {
        let total = 0;
        if (this.props.expenses != null) {
            for (var i = 0; i < this.props.expenses.length; i++) {
                total += this.props.expenses[i].amount
            }
        }
        return total;
    }
    render() {
        let lists = [];
        if (this.props.expenses != null) {
            lists = this.props.expenses.map((item) =>
                <tr key={item.id}>
                <td>{item.name}</td>
                <td>{item.amount}</td>
                <td>{new Date(item.spendDate).toDateString()}</td>
                <td>{item.category}</td>
                <td><a href="#"
                    onClick={(e) => this.handleDelete(item.id, e)}>Remove</a>
                </td>
                </tr>
            );
        }
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
        expenses: state.data
    };
};
const mapDispatchToProps = {
    getExpenseList,
    deleteExpense
};
export default connect(
    mapStateToProps,
    mapDispatchToProps
)(ExpenseEntryItemList);
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.