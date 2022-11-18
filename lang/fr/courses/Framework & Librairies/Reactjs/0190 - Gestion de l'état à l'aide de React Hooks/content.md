## Introduction

React introduit un tout nouveau concept appelé React Hooks à partir de React 16.8. Même s'il s'agit d'un concept relativement nouveau, il permet aux composants fonctionnels de React d'avoir leur propre état et cycle de vie. De plus, React Hooks permet aux composants fonctionnels d'utiliser de nombreuses fonctionnalités qui n'étaient pas disponibles auparavant. Dans ce chapitre, nous allons voir comment gérer l'état d'un composant fonctionnel en utilisant React Hooks.

### Qu'est-ce que React Hooks ?

Les React Hooks sont des fonctions spéciales fournies par React pour gérer une fonctionnalité spécifique à l'intérieur d'un composant fonctionnel React. React fournit une fonction Hook pour chaque fonctionnalité supportée. Par exemple, React fournit la fonction useState() pour gérer l'état dans un composant fonctionnel. Quand un composant fonctionnel React utilise React Hooks, React Hooks s'attache au composant et fournit des fonctionnalités supplémentaires.

La signature générale de ```UseState()``` Hook est la suivante : -

```js
const [<state variable>, <state update function>] = useState(<initial value>);
```

Par exemple, la gestion de l'état d'un composant d'horloge à l'aide de Hooks peut être effectuée comme indiqué ci-dessous.

```js
const [currentDateTime, setCurrentDateTime] = useState(new Date()); 
setInterval(() => setCurrentDateTime(new Date()), 1000);
```

Ici,

- **currentDateTime** − Variable utilisée pour contenir la date et l'heure actuelles (retournée par ```setState()```)
- **setCurrentDate()** − Function utilisée pour définir la date et l'heure actuelles (renvoyée par ```setState()```)

### Create a stateful component

Recréons notre composant d'horloge en utilisant des crochets dans ce chapitre.

Tout d'abord, créez une nouvelle application react, react-clock-hook-app en utilisant le bundler Create React App ou Rollup en suivant les instructions du chapitre Création d'une application React.

Ensuite, ouvrez l'application dans votre éditeur préféré.

Ensuite, créez le dossier src sous le répertoire racine de l'application.

Ensuite, créez un dossier de composants sous le dossier src.

Ensuite, créez un fichier Clock.js dans le dossier src/components et commencez à le modifier.

Ensuite, importez la bibliothèque React et React state Hook, setState.

```js
import React, { useState } from 'react';
```

Ensuite, créez le composant Clock.

```js
function Clock() { 
}
```

Ensuite, créez des crochets d'état pour maintenir la date et l'heure.

```js
const [currentDateTime, setCurrentDateTime] = useState(new Date());
```

Ensuite, réglez la date et l'heure pour chaque seconde.

```js
setInterval(() => setCurrentDateTime(new Date()), 1000);
```

Ensuite, créez l'interface utilisateur pour afficher la date et l'heure actuelles en utilisant currentDateTime et renvoyez-la.

```js
return ( <div><p>The current time is {currentDateTime.toString()}</p></div> );
```

Enfin, exportez le composant en utilisant l'extrait de code -

```js
export default Clock;
```

Le code source complet du composant Clock est le suivant -

```js
import React, { useState } from 'react';

function Clock(props) {
    const [currentDateTime, setCurrentDateTime] = useState(new Date());
    setInterval(() => setCurrentDateTime(new Date()), 1000);
    return (
        <div><p>The current time is {currentDateTime.toString()}</p></div>
    );
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

L'application ci-dessus fonctionne bien. Mais, la fonction ```setCurrentDateTime()``` définie pour s'exécuter toutes les secondes doit être supprimée lorsque l'application se termine. Nous pouvons le faire en utilisant un autre Hook, useEffect fourni par React. Nous l'apprendrons dans le prochain chapitre (cycle de vie des composants).

## Introduction de l'état dans l'application de gestion des dépenses

Introduisons la gestion de l'état dans l'application de gestion des dépenses en ajoutant une fonction simple pour supprimer un élément de dépenses en utilisant des crochets dans ce chapitre.

Ouvrez l'application de gestion des dépenses dans votre éditeur préféré.

Ensuite, créez un nouveau fichier, ExpenseEntryItemListFn.js, dans le dossier src/components et commencez à le modifier.

Ensuite, importez la bibliothèque React et React state Hook, setState.

```js
import React, { useState } from 'react';
```

Ensuite, importez le css, ExpenseEntryItem.css.

```js
import './ExpenseEntryItemList.css'
```

Ensuite, créez le composant ExpenseEntryItemListFn.

```js
function ExpenseEntryItemListFn(props) { }
```

Ensuite, initialisez les crochets d'état du composant avec les éléments de dépense transmis aux composants par le biais des propriétés.

```js
const [items, setItems] = useState(props.items);
```

Ensuite, créez des gestionnaires d'événements pour mettre en évidence les lignes.

```js
function handleMouseEnter(e) {
    e.target.parentNode.classList.add("highlight");
}
function handleMouseLeave(e) {
    e.target.parentNode.classList.remove("highlight");
}
function handleMouseOver(e) {
    console.log("The mouse is at (" + e.clientX + ", " + e.clientY + ")");
}
```

Ensuite, créez un gestionnaire d'événement pour supprimer les éléments sélectionnés en utilisant items et setItems().

```js
function handleDelete(id, e) {
    e.preventDefault();
    console.log(id);
    let newItems = [];
    items.forEach((item, idx) => {
        if (item.id != id)
            newItems.push(item)
    })
    setItems(newItems);
}
```

Ensuite, créez la méthode ```getTotal()``` pour calculer le montant total.

```js
function getTotal() {
    let total = 0;
    for (var i = 0; i < items.length; i++) {
        total += items[i].amount
    }
    return total;
}
```

Ensuite, créez une interface utilisateur pour afficher les dépenses en passant en boucle sur les articles.

```js
const lists = items.map((item) =>
    <tr key={item.id} onMouseEnter={handleMouseEnter} onMouseLeave={handleMouseLeave}>
        <td>{item.name}</td>
        <td>{item.amount}</td>
        <td>{new Date(item.spendDate).toDateString()}</td>
        <td>{item.category}</td>
        <td><a href="#" onClick={(e) => handleDelete(item.id, e)}>Remove</a></td>
    </tr>
);
```

Ensuite, créez l'interface utilisateur complète pour montrer les dépenses et renvoyez-la.

```js
return (
    <table onMouseOver={handleMouseOver}>
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
                {getTotal()}
                </td>
            </tr>
        </tbody>
    </table>
);
```

Enfin, exportez la fonction comme indiqué ci-dessous -

```js
export default ExpenseEntryItemListFn;
```

Le code complet de l'ExpenseEntryItemListFn est le suivant -

```js
import React, { useState } from 'react';
import './ExpenseEntryItemList.css'

function ExpenseEntryItemListFn(props) {
    const [items, setItems] = useState(props.items);

    function handleMouseEnter(e) {
        e.target.parentNode.classList.add("highlight");
    }
    function handleMouseLeave(e) {
        e.target.parentNode.classList.remove("highlight");
    }
    function handleMouseOver(e) {
        console.log("The mouse is at (" + e.clientX + ", " + e.clientY + ")");
    }
    function handleDelete(id, e) {
        e.preventDefault();
        console.log(id);
        let newItems = [];
        items.forEach((item, idx) => {
            if (item.id != id)
                newItems.push(item)
        })
        setItems(newItems);
    }
    function getTotal() {
        let total = 0;
        for (var i = 0; i < items.length; i++) {
            total += items[i].amount
        }
        return total;
    }
    const lists = items.map((item) =>
        <tr key={item.id} onMouseEnter={handleMouseEnter} onMouseLeave={handleMouseLeave}>
            <td>{item.name}</td>
            <td>{item.amount}</td>
            <td>{new Date(item.spendDate).toDateString()}</td>
            <td>{item.category}</td>
            <td><a href="#"
                onClick={(e) => handleDelete(item.id, e)}>Remove</a></td>
        </tr>
    );
    return (
        <table onMouseOver={handleMouseOver}>
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
                    {getTotal()}
                </td>
                </tr>
            </tbody>
        </table>
    );
}
export default ExpenseEntryItemListFn;
```

Ensuite, mettez à jour le fichier index.js et incluez le composant ExpenseEntyItemListFn -

```js
import React from 'react';
import ReactDOM from 'react-dom';
import ExpenseEntryItemListFn from './components/ExpenseEntryItemListFn'

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
        <ExpenseEntryItemListFn items={items} />
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