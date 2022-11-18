## Introduction

La communauté React propose une vaste collection de composants UI avancés. Material UI est l'un des frameworks d'interface utilisateur React les plus populaires. Nous allons apprendre à utiliser la bibliothèque Material UI dans ce chapitre.

## Installation

Material UI peut être installé à l'aide du paquet npm.

```bash
npm install @material-ui/core
```

Material UI recommande les polices Roboto pour l'interface utilisateur. Pour utiliser la police Roboto, incluez-la en utilisant les liens Gooogleapi.

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap" />
```

Pour utiliser les icônes des polices, utilisez le lien vers les icônes de googleapis.

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons" />
```

Pour utiliser les icônes SVG, installez le paquet @material-ui/icons.

```bash
npm install @material-ui/icons
```

## Working exemple

Recréons l'application de liste de dépenses et utilisons des composants d'interface matérielle au lieu de tableaux html.

Tout d'abord, créez une nouvelle application react, react-materialui-app en utilisant le bundler Create React App ou Rollup en suivant les instructions du chapitre Création d'une application React.

Ensuite, installez la bibliothèque React Transition Group -

```bash
cd /go/to/project npm install @material-ui/core @material-ui/icons --save
```

Ensuite, ouvrez l'application dans votre éditeur préféré.

Ensuite, créez le dossier src sous le répertoire racine de l'application.

Ensuite, créez un dossier de composants sous le dossier src.

Ensuite, créez un fichier, ExpenseEntryItemList.js dans le dossier src/components pour créer le composant ExpenseEntryItemList.

Ensuite, importez la bibliothèque React et la feuille de style.

```js
import React from 'react';
```

Ensuite, importez la bibliothèque Material-UI.

```js
import { withStyles } from '@material-ui/core/styles'; 
import Table from '@material-ui/core/Table'; 
import TableBody from '@material-ui/core/TableBody'; 
import TableCell from '@material-ui/core/TableCell'; 
import TableContainer from '@material-ui/core/TableContainer'; 
import TableHead from '@material-ui/core/TableHead'; 
import TableRow from '@material-ui/core/TableRow'; 
import Paper from '@material-ui/core/Paper';
```

Ensuite, créez la classe ExpenseEntryItemList et appelez la fonction du constructeur.

```js
class ExpenseEntryItemList extends React.Component {
    constructor(props) {
        super(props);
    }
}
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap" />
```

Ensuite, créez une fonction de rendu.

```js
render() { 
}
```

Ensuite, appliquez des styles pour les lignes et les cellules du tableau dans la méthode de rendu

```js
const StyledTableCell = withStyles((theme) => ({
    head: {
        backgroundColor: theme.palette.common.black,
        color: theme.palette.common.white,
    },
    body: {
        fontSize: 14,
    },
}))(TableCell);
const StyledTableRow = withStyles((theme) => ({
    root: {
        '&:nth-of-type(odd)': {
            backgroundColor: theme.palette.action.hover,
        },
    },
}))(TableRow);
```

Ensuite, utilisez la méthode map pour générer une collection de Material UI StyledTableRow, chacune représentant un seul élément de saisie des dépenses dans la liste.

```js
const lists = this.props.items.map((item) =>
    <StyledTableRow key={item.id}>
        <StyledTableCell component="th" scope="row">
            {item.name}
        </StyledTableCell>
        <StyledTableCell align="right">{item.amount}</StyledTableCell>
        <StyledTableCell align="right">
            {new Date(item.spendDate).toDateString()}
        </StyledTableCell>
        <StyledTableCell align="right">{item.category}</StyledTableCell>
    </StyledTableRow>
);
```

Ici, la clé identifie chaque ligne et elle doit être unique dans la liste.

Ensuite, dans la méthode ```render()```, créez un tableau Material UI et incluez l'expression lists dans la section rows et renvoyez-le.

```js
return (
<TableContainer component={Paper}>
    <Table aria-label="customized table">
        <TableHead>
            <TableRow>
                <StyledTableCell>Title</StyledTableCell>
                <StyledTableCell align="right">Amount</StyledTableCell>
                <StyledTableCell align="right">Spend date</StyledTableCell>
                <StyledTableCell align="right">Category</StyledTableCell>
            </TableRow>
        </TableHead>
        <TableBody>
            {lists}
        </TableBody>
    </Table>
</TableContainer>
);
```

Enfin, exportez le composant.

```js
export default ExpenseEntryItemList;
```

Maintenant, nous avons créé avec succès le composant pour rendre les postes de dépenses en utilisant les composants matériels de l'interface utilisateur.

Le code source complet de ce composant est indiqué ci-dessous.

```js
import React from 'react';

import { withStyles } from '@material-ui/core/styles';
import Table from '@material-ui/core/Table';
import TableBody from '@material-ui/core/TableBody';
import TableCell from '@material-ui/core/TableCell';
import TableContainer from '@material-ui/core/TableContainer';
import TableHead from '@material-ui/core/TableHead';
import TableRow from '@material-ui/core/TableRow';
import Paper from '@material-ui/core/Paper';

class ExpenseEntryItemList extends React.Component {
    constructor(props) {
        super(props);
    }
    render() {
        const StyledTableCell = withStyles((theme) => ({
            head: {
                backgroundColor: theme.palette.common.black,
                color: theme.palette.common.white,
            },
            body: {
                fontSize: 14,
            },
        }))(TableCell);
        const StyledTableRow = withStyles((theme) => ({
            root: {
                '&:nth-of-type(odd)': {
                backgroundColor: theme.palette.action.hover,
                },
            },
        }))(TableRow);
        const lists = this.props.items.map((item) =>
            <StyledTableRow key={item.id}>
                <StyledTableCell component="th" scope="row">
                {item.name}
                </StyledTableCell>
                <StyledTableCell align="right">{item.amount}</StyledTableCell>
                <StyledTableCell align="right">{new Date(item.spendDate).toDateString()}</StyledTableCell>
                <StyledTableCell align="right">{item.category}</StyledTableCell>
            </StyledTableRow>
        );
        return (
        <TableContainer component={Paper}>
            <Table aria-label="customized table">
                <TableHead>
                <TableRow>
                    <StyledTableCell>Title</StyledTableCell>
                    <StyledTableCell align="right">Amount</StyledTableCell>
                    <StyledTableCell align="right">Spend date</StyledTableCell>
                    <StyledTableCell align="right">Category</StyledTableCell>
                </TableRow>
                </TableHead>
                <TableBody>
                {lists}
                </TableBody>
            </Table>
        </TableContainer> );
    }
}
export default ExpenseEntryItemList;
```

Ensuite, ouvrez index.js et importez la bibliothèque react et notre composant ExpenseEntryItemList nouvellement créé.

```js
import React from 'react'; 
import ReactDOM from 'react-dom'; 
import ExpenseEntryItemList from './components/ExpenseEntryItemList';
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
import ExpenseEntryItemList from './components/ExpenseEntryItemList';

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
        <ExpenseEntryItemList items={items} />
    </React.StrictMode>,
    document.getElementById('root')
);
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le fichier index.html dans le dossier public et incluez la police et les icônes de l'interface utilisateur matérielle.

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>Material UI App</title>
        <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap" />
        <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons" />
    </head>
    <body>
        <div id="root"></div>
        <script type="text/JavaScript" src="./index.js"></script>
    </body>
</html>
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.