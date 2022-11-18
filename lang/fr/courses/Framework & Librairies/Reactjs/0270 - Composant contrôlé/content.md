## Introduction

Le composant contrôlé doit suivre un processus spécifique pour faire de la programmation de formulaire. Vérifions le processus étape par étape à suivre pour un seul élément d'entrée.

Créez un élément de formulaire.

```html
<input type="text" name="username" />
```

Créer un état pour l'élément d'entrée.

```js
this.state = {
    username: '' 
}
```

Ajoutez un attribut de valeur et attribuez la valeur de l'état.

```js
<input type="text" name="username" value={this.state.username} />
```

Ajoutez un attribut onChange et attribuez une méthode de traitement.

```js
<input type="text" name="username" value={this.state.username} onChange={this.handleUsernameChange} />
```

Écrivez la méthode du gestionnaire et mettez à jour l'état chaque fois que l'événement est déclenché.

```js
handleUsernameChange(e) {
    this.setState({
        username = e.target.value
    });
}
```

Liez le gestionnaire d'événements dans le constructeur du composant grâce à la fonction ```bind()```.

```js
this.handleUsernameChange = this.handleUsernameChange.bind(this)
```

Enfin, récupérez la valeur d'entrée en utilisant le nom d'utilisateur de this.state pendant la validation et la soumission.

```js
handleSubmit(e) {
    e.preventDefault();
    alert(this.state.username);
}
```

Dans ce chapitre, nous allons créer un formulaire simple pour ajouter une entrée de dépense en utilisant le composant contrôleur.

Tout d'abord, créez une nouvelle application React, react-form-app en utilisant le bundler Create React App ou Rollup en suivant les instructions du chapitre Créer une application React.

Next, open the application in your favorite editor.

Dans l'étape suivante, créez le dossier src sous le répertoire racine de l'application.

En suivant le processus ci-dessus, créez un dossier de composants sous le dossier src.

Ensuite, créez un fichier, ExpenseForm.css, dans le dossier src pour donner un style au composant.

```css
input[type=text], input[type=number], input[type=date], select {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}
input[type=submit] {
    width: 100%;
    background-color: #4CAF50;
    color: white;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}
input[type=submit]:hover {
    background-color: #45a049;
}
input:focus {
    border: 1px solid #d9d5e0;
}
#expenseForm div {
    border-radius: 5px;
    background-color: #f2f2f2;
    padding: 20px;
}
```

Ensuite, créez un fichier, ExpenseForm.js, dans le dossier src/components et commencez à le modifier.

Ensuite, importez la bibliothèque React.

```js
import React from 'react';
```

Ensuite, importez le fichier ExpenseForm.css.

```js
import './ExpenseForm.css'
```

Ensuite, créez une classe, ExpenseForm et appelez le constructeur avec les props.

```js
class ExpenseForm extends React.Component {
    constructor(props) {
        super(props);
    }
}
```

Ensuite, il faut initialiser l'état du composant.

```js
this.state = { 
    item: {}
}
```

Ensuite, créez la méthode ```render()``` et ajoutez un formulaire avec des champs de saisie pour ajouter des postes de dépenses.

```js
render() {
    return (
        <div id="expenseForm">
            <form>
                <label for="name">Title</label>
                <input type="text" id="name" name="name" placeholder="Enter expense title" />
                <label for="amount">Amount</label>
                <input type="number" id="amount" name="amount" placeholder="Enter expense amount" />
                <label for="date">Spend Date</label>
                <input type="date" id="date" name="date" placeholder="Enter date" />
                <label for="category">Category</label>
                <select id="category" name="category" 
                <option value="">Select</option>
                <option value="Food">Food</option>
                <option value="Entertainment">Entertainment</option>
                <option value="Academic">Academic</option>
                </select>
                <input type="submit" value="Submit" />
            </form>
        </div>
    )
}
```

Ensuite, créez un gestionnaire d'événements pour tous les champs de saisie afin de mettre à jour le détail des dépenses dans l'état.

```js
handleNameChange(e) {
    this.setState( (state, props) => {
        let item = state.item
        item.name = e.target.value;
        return { item: item }
    });
}
handleAmountChange(e) {
    this.setState( (state, props) => {
        let item = state.item
        item.amount = e.target.value;
        return { item: item }
    });
}
handleDateChange(e) {
    this.setState( (state, props) => {
        let item = state.item
        item.date = e.target.value;
        return { item: item }
    });
}
handleCategoryChange(e) {
    this.setState( (state, props) => {
        let item = state.item
        item.category = e.target.value;
        return { item: item }
    });
}
```

Ensuite, liez le gestionnaire d'événements dans le constructeur.

```js
this.handleNameChange = this.handleNameChange.bind(this);
this.handleAmountChange = this.handleAmountChange.bind(this);
this.handleDateChange = this.handleDateChange.bind(this);
this.handleCategoryChange = this.handleCategoryChange.bind(this);
```

Ensuite, ajoutez un gestionnaire d'événement pour l'action submit.

```js
onSubmit = (e) => {
    e.preventDefault();
    alert(JSON.stringify(this.state.item));
}
```

Ensuite, attachez les gestionnaires d'événements au formulaire.

```js
render() {
    return (
        <div id="expenseForm">
            <form onSubmit={(e) => this.onSubmit(e)}>
                <label for="name">Title</label>
                <input type="text" id="name" name="name" placeholder="Enter expense title" 
                value={this.state.item.name}
                onChange={this.handleNameChange} />

                <label for="amount">Amount</label>
                <input type="number" id="amount" name="amount" placeholder="Enter expense amount"
                value={this.state.item.amount}
                onChange={this.handleAmountChange} />

                <label for="date">Spend Date</label>
                <input type="date" id="date" name="date" placeholder="Enter date" 
                value={this.state.item.date}
                onChange={this.handleDateChange} />

                <label for="category">Category</label>
                <select id="category" name="category"
                value={this.state.item.category}
                onChange={this.handleCategoryChange} >
                <option value="">Select</option>
                <option value="Food">Food</option>
                <option value="Entertainment">Entertainment</option>
                <option value="Academic">Academic</option>
                </select>

                <input type="submit" value="Submit" />
            </form>
        </div>
    )
}
```

Enfin, exportez le composant.

```js
export default ExpenseForm
```

Le code complet du composant ExpenseForm est le suivant : -.

```js
import React from 'react';
import './ExpenseForm.css'

class ExpenseForm extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            item: {}
        }
        this.handleNameChange = this.handleNameChange.bind(this);
        this.handleAmountChange = this.handleAmountChange.bind(this);
        this.handleDateChange = this.handleDateChange.bind(this);
        this.handleCategoryChange = this.handleCategoryChange.bind(this);
    }
    handleNameChange(e) {
        this.setState( (state, props) => {
            let item = state.item
            item.name = e.target.value;
            return { item: item }
        });
    }
    handleAmountChange(e) {
        this.setState( (state, props) => {
            let item = state.item
            item.amount = e.target.value;
            return { item: item }
        });
    }
    handleDateChange(e) {
        this.setState( (state, props) => {
            let item = state.item
            item.date = e.target.value;
            return { item: item }
        });
    }
    handleCategoryChange(e) {
        this.setState( (state, props) => {
            let item = state.item
            item.category = e.target.value;
            return { item: item }
        });
    }
    onSubmit = (e) => {
        e.preventDefault();
        alert(JSON.stringify(this.state.item));
    }
    render() {
        return (
            <div id="expenseForm">
            <form onSubmit={(e) => this.onSubmit(e)}>
                <label for="name">Title</label>
                <input type="text" id="name" name="name" placeholder="Enter expense title" 
                value={this.state.item.name}
                onChange={this.handleNameChange} />

                <label for="amount">Amount</label>
                <input type="number" id="amount" name="amount" placeholder="Enter expense amount"
                value={this.state.item.amount}
                onChange={this.handleAmountChange} />

                <label for="date">Spend Date</label>
                <input type="date" id="date" name="date" placeholder="Enter date" 
                value={this.state.item.date}
                onChange={this.handleDateChange} />

                <label for="category">Category</label>
                <select id="category" name="category"
                value={this.state.item.category}
                onChange={this.handleCategoryChange} >
                <option value="">Select</option>
                <option value="Food">Food</option>
                <option value="Entertainment">Entertainment</option>
                <option value="Academic">Academic</option>
                </select>
            
                <input type="submit" value="Submit" />
            </form>
            </div>
        )
    }
}
export default ExpenseForm;
```

Ensuite, créez un fichier, index.js, dans le dossier src et utilisez le composant ExpenseForm.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import ExpenseForm from './components/ExpenseForm'

ReactDOM.render(
    <React.StrictMode>
        <ExpenseForm />
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

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

Enfin, saisissez un exemple de détail de dépense et cliquez sur soumettre. Les données soumises seront collectées et affichées dans une boîte de message contextuelle.