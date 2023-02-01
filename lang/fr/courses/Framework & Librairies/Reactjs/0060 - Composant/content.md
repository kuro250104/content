## Introduction

Le composant React est la brique de base d'une application React. Apprenons comment créer un nouveau composant React et les caractéristiques des composants React dans ce chapitre.

Un composant React représente un petit morceau d'interface utilisateur dans une page Web. La tâche principale d'un composant React est de rendre son interface utilisateur et de la mettre à jour lorsque son état interne est modifié. En plus du rendu de l'interface utilisateur, il gère les événements appartenant à son interface utilisateur. Pour résumer, le composant React fournit les fonctionnalités suivantes.

- Rendu initial de l'interface utilisateur.
- Gestion et traitement des événements.
- Mise à jour de l'interface utilisateur chaque fois que l'état interne est modifié.

Le composant React permet d'accomplir ces fonctionnalités en utilisant trois concepts -

- **Properties** − Permet au composant de recevoir des entrées.
- **Events** − Permettre au composant de gérer les événements DOM et l'interaction avec l'utilisateur final.
- **State** − Permet au composant de rester "stateful". Un composant à état stable met à jour son interface utilisateur en fonction de son état.

Apprenons tous les concepts un par un dans les chapitres suivants.

## Création d'un composant React

La bibliothèque React possède deux types de composants. Les types sont classés en fonction de la façon dont ils sont créés.

- **Composant fonctionnel** - Utilise une simple fonction JavaScript.
- **Composant de classe ES6** - Utilise une classe ES6.

Les principales différences entre les composants de fonction et de classe sont les suivantes : 

- Le composant de fonction et le composant de classe.
- Les composants fonctionnels sont très minimes par nature. Leur seule exigence est de retourner un élément React.

```js
function Hello() { 
    return '<div>Hello</div>'
}
```

La même fonctionnalité peut être réalisée en utilisant le composant de classe ES6 avec peu de codage supplémentaire.

```js
class ExpenseEntryItem extends React.Component {         
    render() { 
        return ( 
            <div>Hello</div> 
        ); 
    }
}
```

- Les composants de classe prennent en charge la gestion de l'état dès le départ, tandis que les composants de fonction ne prennent pas en charge la gestion de l'état. Cependant, React fournit un hook, ```useState()``` pour les composants de fonction afin de maintenir leur état.
- Les composants de classe ont un cycle de vie et l'accès aux événements de chaque cycle de vie par le biais d'apis de rappel dédiées. Les composants fonctionnels n'ont pas de cycle de vie. Encore une fois, React fournit un hook, ```useEffect()``` pour le composant fonction afin d'accéder aux différentes étapes du composant.

## Création d'un composant de classe

Créons un nouveau composant React (dans notre application de gestion des dépenses), ExpenseEntryItem, pour présenter un élément de saisie des dépenses. L'élément de saisie des dépenses est composé du nom, du montant, de la date et de la catégorie. La représentation objet du poste de dépense est :

```js
{ 
    'name': 'Mango juice', 
    'amount': 30.00, 
    'spend_date': '2020-10-10' 
    'category': 'Food', 
}
```

Ouvrez l'application de gestion des dépenses dans votre éditeur préféré.

Ensuite, créez un fichier, ExpenseEntryItem.css, dans le dossier src/components pour donner un style à notre composant.

Ensuite, créez un fichier, ExpenseEntryItem.js, dans le dossier src/components en étendant React.Component.

```js
import React from 'react'; 
import './ExpenseEntryItem.css'; 
class ExpenseEntryItem extends React.Component { 
}
```

Ensuite, créez une méthode ```render()``` dans la classe ExpenseEntryItem.

```js
class ExpenseEntryItem extends React.Component { 
    render() { 
    } 
}
```

Ensuite, créez l'interface utilisateur en utilisant JSX et renvoyez-la à partir de la méthode render.

```js
class ExpenseEntryItem extends React.Component {
    render() {
        return (
            <div>
                <div><b>Item:</b> <em>Mango Juice</em></div>
                <div><b>Amount:</b> <em>30.00</em></div>
                <div><b>Spend Date:</b> <em>2020-10-10</em></div>
                <div><b>Category:</b> <em>Food</em></div>
            </div>
        );
    }
}
```

Ensuite, spécifiez le composant comme classe d'exportation par défaut.

```js
import React from 'react';
import './ExpenseEntryItem.css';

class ExpenseEntryItem extends React.Component {
    render() {
        return (
            <div>
                <div><b>Item:</b> <em>Mango Juice</em></div>
                <div><b>Amount:</b> <em>30.00</em></div>
                <div><b>Spend Date:</b> <em>2020-10-10</em></div>
                <div><b>Category:</b> <em>Food</em></div>
            </div>
        );
    }
}
export default ExpenseEntryItem;
```

Maintenant, nous avons créé avec succès notre premier composant React. Utilisons notre composant nouvellement créé dans index.js.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import ExpenseEntryItem from './components/ExpenseEntryItem'

ReactDOM.render(
    <React.StrictMode>
        <ExpenseEntryItem />
    </React.StrictMode>,
    document.getElementById('root')
);
```

### Exemple

La même fonctionnalité peut être réalisée dans une page web en utilisant le CDN, comme indiqué ci-dessous.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8" />
        <title>React application :: ExpenseEntryItem component</title>
    </head>
    <body>
        <div id="react-app"></div>
        
        <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script>
        <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script>
        <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
        <script type="text/babel">
            class ExpenseEntryItem extends React.Component {
                render() {
                return (
                    <div>
                        <div><b>Item:</b> <em>Mango Juice</em></div>
                        <div><b>Amount:</b> <em>30.00</em></div>
                        <div><b>Spend Date:</b> <em>2020-10-10</em></div>
                        <div><b>Category:</b> <em>Food</em></div>
                    </div>
                );
                }
            }
            ReactDOM.render(
                <ExpenseEntryItem />,
                document.getElementById('react-app') );
        </script>
    </body>
</html>
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

### Sortie

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

```bash
Item: Mango Juice
Amount: 30.00
Spend Date: 2020-10-10
Category: Food
```

## Création d'un composant de fonction

Un composant React peut également être créé en utilisant une simple fonction JavaScript, mais avec des fonctionnalités limitées. Le composant React basé sur des fonctions ne prend pas en charge la gestion de l'état et d'autres fonctions avancées. Il peut être utilisé pour créer rapidement un composant simple.

L'ExpenseEntryItem ci-dessus peut être réécrit en fonction de ce qui est spécifié ci-dessous.

```js
function ExpenseEntryItem() {
    return (
        <div>
            <div><b>Item:</b> <em>Mango Juice</em></div>
            <div><b>Amount:</b> <em>30.00</em></div>
            <div><b>Spend Date:</b> <em>2020-10-10</em></div>
            <div><b>Category:</b> <em>Food</em></div>
        </div>
    );
}
```

Ici, nous avons juste inclus la fonctionnalité de rendu et c'est suffisant pour créer un simple composant React.
