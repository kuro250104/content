## Introduction

La programmation client http permet à l'application de se connecter et d'extraire des données du serveur http via JavaScript. Elle réduit le transfert de données entre le client et le serveur, car elle ne récupère que les données requises au lieu de l'ensemble de la conception, ce qui améliore la vitesse du réseau. Elle améliore l'expérience de l'utilisateur et devient une fonction indispensable de toute application Web moderne.

Aujourd'hui, de nombreuses applications côté serveur exposent leurs fonctionnalités par le biais d'une API REST (fonctionnalité sur le protocole HTTP) et permettent à n'importe quelle application cliente de consommer ces fonctionnalités.

React ne fournit pas son propre api de programmation http mais il supporte l'api fetch() intégré au navigateur ainsi que des bibliothèques client tierces comme axios pour faire de la programmation côté client. Dans ce chapitre, nous allons apprendre comment faire de la programmation http dans une application React. Le développeur doit avoir des connaissances de base en programmation http pour comprendre ce chapitre.

## Expense Rest Api Server

La condition préalable à la programmation Http est la connaissance de base du protocole Http et de la technique REST API. La programmation Http implique deux parties, le serveur et le client. React fournit un support pour créer une application côté client. Express, un framework web populaire, permet de créer des applications côté serveur.

Créons d'abord un serveur Expense Rest Api en utilisant le cadre express, puis accédons-y depuis notre application ExpenseManager en utilisant l'api fetch intégrée au navigateur.

Ouvrez une invite de commande et créez un nouveau dossier, express-rest-api.

```bash
cd /go/to/workspace 
mkdir apiserver 
cd apiserver
```

Initialiser une nouvelle application de nœud en utilisant la commande ci-dessous -

```bash
npm init
```

Le npm init va nous demander d'entrer les détails de base du projet. Entrons apiserver comme nom de projet et server.js comme point d'entrée. Laissez les autres configurations avec l'option par défaut.

```bash
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (apiserver)
version: (1.0.0)
description: Rest api for Expense Application
entry point: (index.js) server.js
test command:
git repository:
keywords:
author:
license: (ISC)
About to write to \path\to\workspace\expense-rest-api\package.json:
{
    "name": "expense-rest-api",
    "version": "1.0.0",
    "description": "Rest api for Expense Application",
    "main": "server.js",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "author": "",
    "license": "ISC"
}
Is this OK? (yes) yes
```

Ensuite, installez les modules express, nedb & cors en utilisant la commande ci-dessous -

```bash
npm install express nedb cors
```

- express est utilisé pour créer une application côté serveur.
- nedb est un datastore utilisé pour stocker les données de dépenses.
- cors est un intergiciel pour le cadre express permettant de configurer les détails d'accès du client.

Ensuite, créons un fichier, data.csv, et remplissons-le avec les données de dépenses initiales à des fins de test. La structure du fichier est qu'il contient une entrée de dépense par ligne.

```bash
Pizza,80,2020-10-10,Food
Grape Juice,30,2020-10-12,Food
Cinema,210,2020-10-16,Entertainment
Java Programming book,242,2020-10-15,Academic
Mango Juice,35,2020-10-16,Food
Dress,2000,2020-10-25,Cloth
Tour,2555,2020-10-29,Entertainment
Meals,300,2020-10-30,Food
Mobile,3500,2020-11-02,Gadgets
Exam Fees,1245,2020-11-04,Academic
```

Ensuite, créez un fichier expensedb.js et incluez le code permettant de charger les données de dépenses initiales dans le magasin de données. Le code vérifie la présence de données initiales dans le magasin de données et ne charge que si les données ne sont pas disponibles dans le magasin.

```js
var store = require("nedb")
var fs = require('fs');
var expenses = new store({ filename: "expense.db", autoload: true })
expenses.find({}, function (err, docs) {
    if (docs.length == 0) {
        loadExpenses();
    }
})
function loadExpenses() {
    readCsv("data.csv", function (data) {
        console.log(data);

        data.forEach(function (rec, idx) {
            item = {}
            item.name = rec[0];
            item.amount = parseFloat(rec[1]);
            item.spend_date = new Date(rec[2]);
            item.category = rec[3];

            expenses.insert(item, function (err, doc) {
                console.log('Inserted', doc.item_name, 'with ID', doc._id);
            })
        })
    })
}
function readCsv(file, callback) {
    fs.readFile(file, 'utf-8', function (err, data) {
        if (err) throw err;
        var lines = data.split('\r\n');
        var result = lines.map(function (line) {
            return line.split(',');
        });
        callback(result);
    });
}
module.exports = expenses
```

Ensuite, créez un fichier, server.js, et incluez le code réel pour lister, ajouter, mettre à jour et supprimer les entrées de dépenses.

```js
var express = require("express")
var cors = require('cors')
var expenseStore = require("./expensedb.js")
var app = express()
app.use(cors());
var bodyParser = require("body-parser");
app.use(bodyParser.urlencoded({ extended: false }));
app.use(bodyParser.json());
var HTTP_PORT = 8000
app.listen(HTTP_PORT, () => {
    console.log("Server running on port %PORT%".replace("%PORT%", HTTP_PORT))
});
app.get("/", (req, res, next) => {
    res.json({ "message": "Ok" })
});
app.get("/api/expenses", (req, res, next) => {
    expenseStore.find({}, function (err, docs) {
        res.json(docs);
    });
});
app.get("/api/expense/:id", (req, res, next) => {
    var id = req.params.id;
    expenseStore.find({ _id: id }, function (err, docs) {
        res.json(docs);
    })
});
app.post("/api/expense/", (req, res, next) => {
    var errors = []
    if (!req.body.item) {
        errors.push("No item specified");
    }
    var data = {
        name: req.body.name,
        amount: req.body.amount,
        category: req.body.category,
        spend_date: req.body.spend_date,
    }
    expenseStore.insert(data, function (err, docs) {
        return res.json(docs);
    });
})
app.put("/api/expense/:id", (req, res, next) => {
    var id = req.params.id;
    var errors = []
    if (!req.body.item) {
        errors.push("No item specified");
    }
    var data = {
        _id: id,
        name: req.body.name,
        amount: req.body.amount,
        category: req.body.category,
        spend_date: req.body.spend_date,
    }
    expenseStore.update( { _id: id }, data, function (err, docs) {
        return res.json(data);
    });
})
app.delete("/api/expense/:id", (req, res, next) => {
    var id = req.params.id;
    expenseStore.remove({ _id: id }, function (err, numDeleted) {
        res.json({ "message": "deleted" })
    });
})
app.use(function (req, res) {
    res.status(404);
});
```

Maintenant, il est temps d'exécuter l'application.

```bash
npm run start
```

Ensuite, ouvrez un navigateur et saisissez ```http://localhost:8000/``` dans la barre d'adresse.

```bash
{ 
    "message": "Ok" 
}
```

Cela confirme que notre application fonctionne bien.

Enfin, changez l'url en ```http://localhost:8000/api/expense``` et appuyez sur la touche Entrée. Le navigateur affichera les entrées de dépenses initiales au format JSON.

```js
[
    ...
    {
        "name": "Pizza",
        "amount": 80,
        "spend_date": "2020-10-10T00:00:00.000Z",
        "category": "Food",
        "_id": "5H8rK8lLGJPVZ3gD"
    },
    ...
]
```

Utilisons notre serveur de dépenses nouvellement créé dans notre application de gestion des dépenses via l'api ```fetch()``` dans la section suivante.

## L'api fetch()

Créons une nouvelle application pour présenter la programmation côté client dans React.

Tout d'abord, créez une nouvelle application react, react-http-app en utilisant le bundler Create React App ou Rollup en suivant les instructions du chapitre Créer une application React.

Ensuite, ouvrez l'application dans votre éditeur préféré.

Ensuite, créez le dossier src sous le répertoire racine de l'application.

Ensuite, créez un dossier de composants sous le dossier src.

Ensuite, créez un fichier, ExpenseEntryItemList.css, dans le dossier src/components et incluez les styles de table génériques.

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

Ensuite, importez la bibliothèque React.

```js
import React from 'react';
```

Ensuite, créez une classe, ExpenseEntryItemList et appelez le constructeur avec les props.

```js
class ExpenseEntryItemList extends React.Component {
    constructor(props) {
        super(props);
    }
}
```

Ensuite, initialiser l'état avec une liste vide dans le constructeur.

```js
this.state = {
    isLoaded: false,
    items: []
}
```

Ensuite, créez une méthode, setItems, pour mettre en forme les éléments reçus du serveur distant, puis placez-la dans l'état du composant.

```js
setItems(remoteItems) {
    var items = [];
    remoteItems.forEach((item) => {
        let newItem = {
            id: item._id,
            name: item.name,
            amount: item.amount,
            spendDate: item.spend_date,
            category: item.category
        }
        items.push(newItem)
    });
    this.setState({
        isLoaded: true,
        items: items
    });
}
```

Ensuite, ajoutez une méthode, fetchRemoteItems, pour récupérer les éléments depuis le serveur.

```js
fetchRemoteItems() {
    fetch("http://localhost:8000/api/expenses")
    .then(res => res.json())
    .then(
        (result) => {
        this.setItems(result);
        },
        (error) => {
        this.setState({
            isLoaded: false,
            error
        });
        }
    )
}
```

Ici,

- fetch L'api est utilisée pour récupérer l'élément depuis le serveur distant.
- setItems est utilisé pour formater et stocker les éléments dans l'état.

Ensuite, ajoutez une méthode, deleteRemoteItem, pour supprimer l'élément du serveur distant.

```js
deleteRemoteItem(id) {
    fetch('http://localhost:8000/api/expense/' + id, { method: 'DELETE' })
    .then(res => res.json())
    .then(
        () => {
        this.fetchRemoteItems()
        }
    )
}
```

Ici,

- fetch api est utilisé pour supprimer et récupérer l'élément à partir du serveur distant.
- setItems est à nouveau utilisé pour formater et stocker les éléments dans l'état.

Ensuite, appelez l'api du cycle de vie ipour charger les éléments dans le composant pendant sa phase de montage.

```js
componentDidMount() { 
    this.fetchRemoteItems(); 
}
```

Ensuite, écrivez un gestionnaire d'événement pour supprimer l'élément de la liste.

```js
handleDelete = (id, e) => { 
    e.preventDefault(); 
    console.log(id); 

    this.deleteRemoteItem(id); 
}
```

Ensuite, écrivez la méthode de rendu.

```js
render() {
    let lists = [];
    if (this.state.isLoaded) {
        lists = this.state.items.map((item) =>
            <tr key={item.id} onMouseEnter={this.handleMouseEnter} onMouseLeave={this.handleMouseLeave}>
                <td>{item.name}</td>
                <td>{item.amount}</td>
                <td>{new Date(item.spendDate).toDateString()}</td>
                <td>{item.category}</td>
                <td><a href="#" onClick={(e) => this.handleDelete(item.id, e)}>Remove</a></td>
            </tr>
        );
    }
    return (
        <div>
            <table onMouseOver={this.handleMouseOver}>
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
                </tbody>
            </table>
        </div>
    );
}
```

Enfin, exportez le composant.

```js
export default ExpenseEntryItemList;
```

Ensuite, créez un fichier, index.js, dans le dossier src et utilisez le composant ExpenseEntryItemList.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import ExpenseEntryItemList from './components/ExpenseEntryItemList';

ReactDOM.render(
    <React.StrictMode>
            <ExpenseEntryItemList />
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
        <title>React App</title>
    </head>
    <body>
        <div id="root"></div>
        <script type="text/JavaScript" src="./index.js"></script>
    </body>
</html>
```

Ensuite, ouvrez une nouvelle fenêtre de terminal et démarrez notre application serveur.

```bash
cd /go/to/server/application 
npm start
```

Ensuite, servez l'application client en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.