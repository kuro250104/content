## Introduction

Comme nous l'avons appris précédemment, le composant non contrôlé ne prend pas en charge la programmation de formulaire basée sur React. Obtenir une valeur d'un élément React DOM (élément de formulaire) n'est pas possible sans utiliser l'api React. Une façon d'obtenir le contenu d'un composant React est d'utiliser la fonctionnalité React ref.

React fournit un attribut ref pour tous ses éléments DOM et une api correspondante, React.createRef() pour créer une nouvelle référence (this.ref). La référence nouvellement créée peut être attachée à l'élément de formulaire et la valeur de l'élément de formulaire attaché peut être accédée en utilisant this.ref.current.value lorsque cela est nécessaire (pendant la validation et la soumission).

Voyons le processus étape par étape pour faire de la programmation de formulaires dans un composant non contrôlé.

Créez une référence.

```js
this.inputRef = React.createRef();
```

Créez un élément de formulaire.

```html
<input type="text" name="username" />
```

Attachez la référence déjà créée dans l'élément de formulaire.

```js
<input type="text" name="username" ref={this.inputRef} />
```

Pour définir la valeur par défaut d'un élément d'entrée, utilisez l'attribut defaultValue au lieu de l'attribut value. Si la valeur est utilisée, elle sera mise à jour pendant la phase de rendu du composant.

```js
<input type="text" name="username" ref={this.inputRef} defaultValue="default value" />
```

Enfin, obtenez la valeur de l'entrée en utilisant this.inputRef.current.value pendant la validation et la soumission.

```js
handleSubmit(e) {
    e.preventDefault();

    alert(this.inputRef.current.value);
}
```

Dans ce chapitre, nous allons créer un formulaire simple pour ajouter une entrée de dépense en utilisant un composant non contrôlé.

Tout d'abord, créez une nouvelle application react, react-form-uncontrolled-app en utilisant le bundler Create React App ou Rollup en suivant les instructions du chapitre Création d'une application React.

Ensuite, ouvrez l'application dans votre éditeur préféré.

Créez le dossier src sous le répertoire racine de l'application.

Ensuite, créez un dossier de composants sous le dossier src.

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

Ensuite, créez une référence React pour tous les champs de saisie.

```js
this.nameInputRef = React.createRef();
this.amountInputRef = React.createRef();
this.dateInputRef = React.createRef();
this.categoryInputRef = React.createRef();
```

Ensuite, créez la méthode render() et ajoutez un formulaire avec des champs de saisie pour ajouter des éléments de dépense.

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
                <select id="category" name="category" >
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

Ensuite, ajoutez un gestionnaire d'événement pour l'action submit.

```js
onSubmit = (e) => {
    e.preventDefault();

    let item = {};

    item.name = this.nameInputRef.current.value;
    item.amount = this.amountInputRef.current.value;
    item.date = this.dateInputRef.current.value;
    item.category = this.categoryInputRef.current.value;

    alert(JSON.stringify(item));
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
                ref={this.nameInputRef} />

                <label for="amount">Amount</label>
                <input type="number" id="amount" name="amount" placeholder="Enter expense amount" 
                ref={this.amountInputRef} />      

                <label for="date">Spend Date</label>
                <input type="date" id="date" name="date" placeholder="Enter date" 
                ref={this.dateInputRef} />

                <label for="category">Category</label>
                <select id="category" name="category" 
                ref={this.categoryInputRef} >
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

Le code complet du composant ExpenseForm est donné ci-dessous

```js
import React from 'react';
import './ExpenseForm.css'

class ExpenseForm extends React.Component {
    constructor(props) {
        super(props);

        this.nameInputRef = React.createRef();
        this.amountInputRef = React.createRef();
        this.dateInputRef = React.createRef();
        this.categoryInputRef = React.createRef();
    }
    onSubmit = (e) => {
        e.preventDefault();
        let item = {};
        item.name = this.nameInputRef.current.value;
        item.amount = this.amountInputRef.current.value;
        item.date = this.dateInputRef.current.value;
        item.category = this.categoryInputRef.current.value;

        alert(JSON.stringify(item));
    }
    render() {
        return (
            <div id="expenseForm">
                <form onSubmit={(e) => this.onSubmit(e)}>
                <label for="name">Title</label>
                <input type="text" id="name" name="name" placeholder="Enter expense title" 
                    ref={this.nameInputRef} />

                <label for="amount">Amount</label>
                <input type="number" id="amount" name="amount" placeholder="Enter expense amount" 
                    ref={this.amountInputRef} />   

                <label for="date">Spend Date</label>
                <input type="date" id="date" name="date" placeholder="Enter date" 
                    ref={this.dateInputRef} />

                <label for="category">Category</label>
                <select id="category" name="category" 
                    ref={this.categoryInputRef} >
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