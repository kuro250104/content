## Introduction

Dans une application web, le routage est un processus qui consiste à lier une URL web à une ressource spécifique dans l'application web. Dans React, il s'agit de lier une URL à un composant. React ne prend pas en charge le routage de manière native, car il s'agit essentiellement d'une bibliothèque d'interface utilisateur. La communauté React fournit de nombreux composants tiers pour gérer le routage dans l'application React. Nous allons découvrir React Router, une bibliothèque de routage de premier choix pour les applications React.

## Installer React Router

Voyons comment installer le composant React Router dans notre application Expense Manager.

Ouvrez une invite de commande et allez dans le dossier racine de notre application.

```bash
cd /go/to/expense/manager
```

Install the react router using below command.

```bash
npm install react-router-dom --save
```

## Concept

Le routeur React fournit quatre composants pour gérer la navigation dans une application React.

- **Router** − Le routeur est le composant de premier niveau. Il englobe l'ensemble de l'application.
- **Link** − Similaire à la balise anchor en html. Elle définit l'url cible ainsi que le texte de référence.

```js
<Link to="/">Home</Link>
```

Ici, l'attribut **to** est utilisé pour définir l'url cible.

**Switch & Route** - Les deux sont utilisés ensemble. Ils font correspondre l'url cible au composant. Switch est le composant parent et Route est le composant enfant. Le composant Switch peut avoir plusieurs composants Route et chaque composant Route fait correspondre une url particulière à un composant.

```js
<Switch>
    <Route exact path="/">
        <Home />
    </Route>
    <Route path="/home">
        <Home />
    </Route>
    <Route path="/list">
        <ExpenseEntryItemList />
    </Route>
</Switch>
```

Ici, l'attribut path est utilisé pour faire correspondre l'url. Fondamentalement, Switch fonctionne de manière similaire à l'instruction switch traditionnelle dans un langage de programmation. Il fait correspondre l'url cible avec chaque route enfant (attribut path) une par une dans l'ordre et invoque la première route trouvée.

Avec le composant routeur, le routeur React fournit une option pour définir et obtenir des informations dynamiques à partir de l'url. Par exemple, dans un site web d'articles, l'url peut avoir le type d'article attaché à lui et le type d'article doit être dynamiquement extrait et doit être utilisé pour récupérer le type spécifique d'articles.

```js
<Link to="/article/c">C Programming</Link>
<Link to="/article/java">Java Programming</Link>

...
...

<Switch>
    <Route path="article/:tag" children={<ArticleList />} />
</Switch>
```

Ensuite, dans le composant enfant (composant de classe),

```js
import { withRouter } from "react-router"

class ArticleList extends React.Component {
    ...
    ...
    static getDerivedStateFromProps(props, state) {
        let newState = {
            tag: props.match.params.tag
        }
        return newState;
    }
    ...
    ...
}
export default WithRouter(ArticleList)
```

Ici, WithRouter permet au composant ArticleList d'accéder aux informations des balises par le biais de props.

On peut procéder de la même manière pour les composants fonctionnels.

```js
function ArticleList() {
    let { tag } = useParams();
    return (
        <div>
            <h3>ID: {id}</h3>
        </div>
    );
}
```

Ici, useParams est un React Hooks personnalisé fourni par le composant React Router.

## Nested routing

React router supporte également le routage imbriqué. React router fournit un autre React Hooks, ```useRouteMatch()``` pour extraire les informations de la route parent dans les routes imbriquées.

```js
function ArticleList() {
    // get the parent url and the matched path
    let { path, url } = useRouteMatch();

    return (
        <div>
            <h2>Articles</h2>
            <ul>
                <li>
                <Link to={`${url}/pointer`}>C with pointer</Link>
                </li>
                <li>
                <Link to={`${url}/basics`}>C basics</Link>
                </li>
            </ul>

            <Switch>
                <Route exact path={path}>
                <h3>Please select an article.</h3>
                </Route>
                <Route path={`${path}/:article`}>
                <Article />
                </Route>
            </Switch>
        </div>
    );
}
function Article() {
    let { article } = useParams();
    return (
        <div>
            <h3>The select article is {article}</h3>
        </div>
    );
}
```

Ici, useRouteMatch renvoie le chemin correspondant et l'url cible. L'url peut être utilisé pour créer le niveau suivant de liens et le chemin peut être utilisé pour mapper le niveau suivant de composants/écrans.

## Création de la navigation

Apprenons à faire du routage en créant le routage possible dans notre application de gestion des dépenses. Les écrans minimums de l'application sont donnés ci-dessous -

- **Home screen** − Atterrissage ou écran initial de l'application
- **Expense list screen** − Affiche les postes de dépenses sous forme de tableau.
- **Expense add screen** − Interface d'ajout d'un poste de dépense

Tout d'abord, créez une nouvelle application react, react-router-app en utilisant le bundler Create React App ou Rollup en suivant les instructions du chapitre Création d'une application React.

Ensuite, ouvrez l'application dans votre éditeur préféré.

Ensuite, créez le dossier src sous le répertoire racine de l'application.

Ensuite, créez un dossier de composants sous le dossier src.

Ensuite, créez un fichier, Home.js, dans le dossier src/components et commencez à le modifier.

Ensuite, importez la bibliothèque React.

```js
import React from 'react';
```

Ensuite, importez Link de la bibliothèque React router.

```js
import { Link } from 'react-router-dom'
```

Ensuite, créez une classe, Home et appelez le constructeur avec les props.

```js
class Home extends React.Component {
    constructor(props) {
        super(props);
    }
}
```

Ensuite, ajoutez la méthode ```render()``` et affichez le message de bienvenue et les liens pour ajouter et lister les dépenses à l'écran.

```js
render() {
    return (
        <div>
            <p>Welcome to the React tutorial</p>
            <p><Link to="/list">Click here</Link> to view expense list</p>
            <p><Link to="/add">Click here</Link> to add new expenses</p>
        </div>
    )
}
```

Enfin, exportez le composant.

```js
export default Home;
```

Le code source complet du composant Home est donné ci-dessous -

```js
import React from 'react';
import { Link } from 'react-router-dom'

class Home extends React.Component {
    constructor(props) {
        super(props);
    }
    render() {
        return (
            <div>
                <p>Welcome to the React tutorial</p>
                <p><Link to="/list">Click here</Link> to view expense list</p>
                <p><Link to="/add">Click here</Link> to add new expenses</p>
            </div>
        )
    }
}
export default Home;
```

Ensuite, créez le fichier ExpenseEntryItemList.js dans le dossier src/components et créez le composant ExpenseEntryItemList.

```js
import React from 'react';
import { Link } from 'react-router-dom'

class ExpenseEntryItemList extends React.Component {
    constructor(props) {
        super(props);
    }
    render() {
        return (
            <div>
                <h1>Expenses</h1>
                <p><Link to="/add">Click here</Link> to add new expenses</p>
                <div>
                Expense list
                </div>
            </div>
        )
    }
}
export default ExpenseEntryItemList;
```

Ensuite, créez le fichier ExpenseEntryItemForm.js dans le dossier src/components et créez le composant ExpenseEntryItemForm.

```js
import React from 'react';
import { Link } from 'react-router-dom'

class ExpenseEntryItemForm extends React.Component {
    constructor(props) {
        super(props);
    }
    render() {
        return (
            <div>
                <h1>Add Expense item</h1>
                <p><Link to="/list">Click here</Link> to view new expense list</p>
                <div>
                Expense form
                </div>
            </div>
        )
    }
}
export default ExpenseEntryItemForm;
```

Ensuite, créez un fichier, App.css, dans le dossier src/components et ajoutez des styles css génériques.

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
```

Ensuite, créez un fichier, App.js, dans le dossier src/components et commencez à le modifier. Le but du composant App est de gérer tout l'écran dans un seul composant. Il va configurer le routage et permettre la navigation vers tous les autres composants.

Ensuite, importez la bibliothèque React et d'autres composants.

```js
import React from 'react';

import Home from './Home'
import ExpenseEntryItemList from './ExpenseEntryItemList'
import ExpenseEntryItemForm from './ExpenseEntryItemForm'

import './App.css'
```

Ensuite, importez les composants du routeur React.

```js
import {
    BrowserRouter as Router,
    Link,
    Switch,
    Route
} from 'react-router-dom'
```

Ensuite, écrivez la méthode ```render()``` et configurez le routage.

```js
function App() {
    return (
        <Router>
            <div>
                <nav>
                <ul>
                    <li>
                        <Link to="/">Home</Link>
                    </li>
                    <li>
                        <Link to="/list">List Expenses</Link>
                    </li>
                    <li>
                        <Link to="/add">Add Expense</Link>
                    </li>
                </ul>
                </nav>

                <Switch>
                <Route path="/list">
                    <ExpenseEntryItemList />
                </Route>
                <Route path="/add">
                    <ExpenseEntryItemForm />
                </Route>
                <Route path="/">
                    <Home />
                </Route>
                </Switch>
            </div>
        </Router>
    );
}
```

Ensuite, créez un fichier, index.js, dans le dossier src et utilisez le composant App.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './components/App';

ReactDOM.render(
    <React.StrictMode>
        <App />
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
        <title>React router app</title>
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

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

Essayez de naviguer sur les liens et confirmez que le routage fonctionne.