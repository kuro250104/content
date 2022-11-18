## Introduction

Formik est une bibliothèque de formulaires React tierce. Elle fournit une programmation et une validation de base des formulaires. Elle est basée sur un composant contrôlé et réduit considérablement le temps de programmation des formulaires. Recréons le formulaire de dépense en utilisant la bibliothèque Formik.

Tout d'abord, créez une nouvelle application react, react-formik-app en utilisant le bundler Create React App ou Rollup en suivant les instructions du chapitre Création d'une application React.

Ensuite, installez la bibliothèque Formik.

```bash
cd /go/to/workspace npm install formik --save
```

Ensuite, ouvrez l'application dans votre éditeur préféré.

Ensuite, créez le dossier src sous le répertoire racine de l'application.

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
#expenseForm span {
    color: red;
}
```

Ensuite, créez un fichier, ExpenseForm.js, dans le dossier src/components et commencez à le modifier.

Ensuite, importez React et la bibliothèque Formik.

```js
import React from 'react'; 
import { Formik } from 'formik';
```

Ensuite, importez le fichier ExpenseForm.css.

```js
import './ExpenseForm.css'
```

Ensuite, créez la classe ExpenseForm.

```js
class ExpenseForm extends React.Component {        
    constructor(props) { 
        super(props); 
    } 
}
```

Ensuite, définissez les valeurs initiales de l'élément de dépense dans le constructeur.

```js
this.initialValues = { name: '', amount: '', date: '', category: '' }
```

Ensuite, créer une méthode de validation. Formik enverra les valeurs actuelles entrées par l'utilisateur.

```js
validate = (values) => {
    const errors = {};
    if (!values.name) {
        errors.name = 'Required';
    }
    if (!values.amount) {
        errors.amount = 'Required';
    }
    if (!values.date) {
        errors.date = 'Required';
    }
    if (!values.category) {
        errors.category = 'Required';
    }
    return errors;
}
```

Ensuite, créer une méthode pour soumettre le formulaire. Formik enverra les valeurs actuelles entrées par l'utilisateur.

```js
handleSubmit = (values, setSubmitting) => {
    setTimeout(() => {
        alert(JSON.stringify(values, null, 2));
        setSubmitting(false);
    }, 400);
}
```

Ensuite, créer la méthode ```render()```. Utiliser les méthodes handleChange, handleBlur et handleSubmit fournies par Formik comme gestionnaire d'évènements pour les éléments d'entrée.

```js
render() {
    return (
        <div id="expenseForm">
            <Formik
                initialValues={this.initialValues}
                validate={values => this.validate(values)}
                onSubmit={(values, { setSubmitting }) => this.handleSubmit(values, setSubmitting)} >
                {
                ({
                    values,
                    errors,
                    touched,
                    handleChange,
                    handleBlur,
                    handleSubmit,
                    isSubmitting,
                    /* and other goodies */
                }) 
                => (
                    <form onSubmit={handleSubmit}>
                        <label for="name">Title <span>{errors.name && touched.name && errors.name}</span></label>
                        <input type="text" id="name" name="name" placeholder="Enter expense title"
                            onChange={handleChange}
                            onBlur={handleBlur}
                            value={values.name} />

                        <label for="amount">Amount <span>{errors.amount && touched.amount && errors.amount}</span></label>
                        <input type="number" id="amount" name="amount" placeholder="Enter expense amount"
                            onChange={handleChange}
                            onBlur={handleBlur}
                            value={values.amount} />

                        <label for="date">Spend Date <span>{errors.date && touched.date && errors.date}</span></label>
                        <input type="date" id="date" name="date" placeholder="Enter date"
                            onChange={handleChange}
                            onBlur={handleBlur}
                            value={values.date} />

                        <label for="category">Category <span>{errors.category && touched.category && errors.category}</span></label>
                        <select id="category" name="category"
                            onChange={handleChange}
                            onBlur={handleBlur}
                            value={values.category}>
                            <option value="">Select</option>
                            <option value="Food">Food</option>
                            <option value="Entertainment">Entertainment</option>
                            <option value="Academic">Academic</option>
                        </select>

                        <input type="submit" value="Submit" disabled={isSubmitting} />
                    </form>
                )
                }
            </Formik>
        </div>
    )
}
```

Enfin, exportez le composant.

```js
export default ExpenseForm
```

Le code complet du composant ExpenseForm est donné ci-dessous.

```js
import React from 'react';
import './ExpenseForm.css'
import { Formik } from 'formik';

class ExpenseFormik extends React.Component {
    constructor(props) {
        super(props);

        this.initialValues = { name: '', amount: '', date: '', category: '' }
    }
    validate = (values) => {
        const errors = {};
        if (!values.name) {
            errors.name = 'Required';
        }
        if (!values.amount) {
            errors.amount = 'Required';
        }
        if (!values.date) {
            errors.date = 'Required';
        }
        if (!values.category) {
            errors.category = 'Required';
        }
        return errors;
    }
    handleSubmit = (values, setSubmitting) => {
        setTimeout(() => {
            alert(JSON.stringify(values, null, 2));
            setSubmitting(false);
        }, 400);
    }
    render() {
        return (
            <div id="expenseForm">
                <Formik
                initialValues={this.initialValues}
                validate={values => this.validate(values)}
                onSubmit={(values, { setSubmitting }) => this.handleSubmit(values, setSubmitting)} > 
                {
                    ({
                        values,
                        errors,
                        touched,
                        handleChange,
                        handleBlur,
                        handleSubmit,
                        isSubmitting,
                        /* and other goodies */
                    }) => 
                    (
                        <form onSubmit={handleSubmit}>
                            <label for="name">Title <span>{errors.name && touched.name && errors.name}</span></label>
                            <input type="text" id="name" name="name" placeholder="Enter expense title"
                            onChange={handleChange}
                            onBlur={handleBlur}
                            value={values.name} />

                            <label for="amount">Amount <span>{errors.amount && touched.amount && errors.amount}</span></label>
                            <input type="number" id="amount" name="amount" placeholder="Enter expense amount"
                            onChange={handleChange}
                            onBlur={handleBlur}
                            value={values.amount} />

                            <label for="date">Spend Date <span>{errors.date && touched.date && errors.date}</span></label>
                            <input type="date" id="date" name="date" placeholder="Enter date"
                            onChange={handleChange}
                            onBlur={handleBlur}
                            value={values.date} />

                            <label for="category">Category <span>{errors.category && touched.category && errors.category}</span></label>
                            <select id="category" name="category"
                            onChange={handleChange}
                            onBlur={handleBlur}
                            value={values.category}>
                            <option value="">Select</option>
                            <option value="Food">Food</option>
                            <option value="Entertainment">Entertainment</option>
                            <option value="Academic">Academic</option>
                            </select>

                            <input type="submit" value="Submit" disabled={isSubmitting} />
                        </form>
                    )
                }
                </Formik>
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