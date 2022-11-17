## Introduction

Utilisons les composants nouvellement créés et améliorons notre composant ExpenseEntryItem.

Ouvrez notre application de gestion des dépenses dans votre éditeur préféré.

Ensuite, ouvrez le fichier ExpenseEntryItem.js.

Ensuite, importez FormattedMoney et FormattedDate.

```js
import FormattedMoney from './FormattedMoney' 
import FormattedDate from './FormattedDate'
```

Ensuite, mettez à jour la méthode de rendu en incluant les composants FormattedMoney et FormattedDater.

```js
render() {
    return (
        <div>
            <div><b>Item:</b> <em>{this.props.item.name}</em></div>
            <div><b>Amount:</b> 
                <em>
                <FormattedMoney value={this.props.item.amount} />
                </em>
            </div>
            <div><b>Spend Date:</b> 
                <em>
                <FormattedDate value={this.props.item.spendDate} />
                </em>
            </div>
            <div><b>Category:</b> 
                <em>{this.props.item.category}</em></div>
        </div>
    );
}
```

Ici, nous avons passé le montant et le spendDate à travers l'attribut value des composants.

Le code source final mis à jour du composant ExprenseEntryItem est donné ci-dessous -

```js
import React from 'react'
import FormattedMoney from './FormattedMoney'
import FormattedDate from './FormattedDate'

class ExpenseEntryItem extends React.Component {
    constructor(props) {
        super(props);
    }
    render() {
        return (
            <div>
                <div><b>Item:</b> <em>{this.props.item.name}</em></div>
                <div><b>Amount:</b> 
                <em>
                    <FormattedMoney value={this.props.item.amount} />
                </em>
                </div>
                <div><b>Spend Date:</b> 
                <em>
                    <FormattedDate value={this.props.item.spendDate} />
                </em>
                </div>
                <div><b>Category:</b> 
                <em>{this.props.item.category}</em></div>
            </div>
        );
    }
}
export default ExpenseEntryItem;
```

Ouvrez index.js et appelez le composant ExpenseEntryItem en passant l'objet item.

```js
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