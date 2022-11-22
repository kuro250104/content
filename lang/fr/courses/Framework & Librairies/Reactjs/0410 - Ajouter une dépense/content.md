## Introduction

Ouvrez ExpenseEntryItemList.js et importez connect de la bibliothèque redux.

```js
import { connect } from 'react-redux';
```

Ensuite, importez la bibliothèque Formik..

```js
iimport { Formik } from 'formik';
```

Ensuite, importez la méthode withRouter de la bibliothèque des routeurs.

```js
import { withRouter } from "react-router-dom";
```

Ensuite, importez addExpense de notre bibliothèque d'actions.

```js
import { addExpense } from '../actions/expenseActions';
```

Ensuite, créez un constructeur avec des valeurs initiales pour les dépenses.

```js
constructor(props) {
    super(props); 
    this.initialValues = { name: '', amount: '', spend_date: '', category: '' } 
}
```

Ensuite, écrivez la méthode de validation.

```js
validate = (values) => {
    const errors = {};
    if (!values.name) {
        errors.name = 'Required';
    }
    if (!values.amount) {
        errors.amount = 'Required';
    }
    if (!values.spend_date) {
        errors.spend_date = 'Required';
    }
    if (!values.category) {
        errors.category = 'Required';
    }
    return errors;
}
```

Ensuite, ajoutez la méthode de gestion des événements.

```js
handleSubmit = (values, setSubmitting) =< {
    setTimeout(() =< {
        let newItem = {
            name: values.name,
            amount: values.amount,
            spendDate: values.spend_date,
            category: values.category
        }
        this.props.addExpense(newItem);
        setSubmitting(false);
        this.props.history.push("/list");
    }, 400);
}
```

Ici,

- Utilisation de la méthode addExpense pour ajouter un poste de dépense
- Utilisez la méthode de l'historique des routeurs pour passer à la page de la liste des dépenses.

Ensuite, mettre à jour la méthode de rendu avec le formulaire créé en utilisant la bibliothèque Formik.

```js
render() {
    return (
        <div id="expenseForm">
            <Formik
                initialValues={this.initialValues}
                validate={values => this.validate(values)}
                onSubmit={(values, { setSubmitting }) => this.handleSubmit(values, setSubmitting)}>
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
                }) => (
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

                        <label for="spend_date">Spend Date <span>{errors.spend_date && touched.spend_date && errors.spend_date}</span></label>
                        <input type="date" id="spend_date" name="spend_date" placeholder="Enter date"
                            onChange={handleChange}
                            onBlur={handleBlur}
                            value={values.spend_date} />

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

Ensuite, faites correspondre la méthode de répartition aux propriétés du composant.

```js
const mapDispatchToProps = { 
    addExpense, 
};
```

Enfin, connectez le composant au magasin et enveloppez également le composant avec WithRouter pour obtenir un accès programmatique aux liens du routeur.

```js
export default withRouter(connect(
    null,
    mapDispatchToProps
)(ExpenseEntryItemForm));
```

Le code source complet du composant est le suivant -

```js
import React from "react";

import { connect } from 'react-redux';
import { Formik } from 'formik';
import { withRouter } from "react-router-dom";
import { addExpense } from '../actions/expenseActions';

class ExpenseEntryItemForm extends React.Component {
    constructor(props) {
        super(props);

        this.initialValues = { name: '', amount: '', spend_date: '', category: '' }
    }
    validate = (values) => {
        const errors = {};
        if (!values.name) {
            errors.name = 'Required';
        }
        if (!values.amount) {
            errors.amount = 'Required';
        }
        if (!values.spend_date) {
            errors.spend_date = 'Required';
        }
        if (!values.category) {
            errors.category = 'Required';
        }
        return errors;
    }
    handleSubmit = (values, setSubmitting) => {
        setTimeout(() => {
            let newItem = {
                name: values.name,
                amount: values.amount,
                spendDate: values.spend_date,
                category: values.category
            }
            this.props.addExpense(newItem);
            setSubmitting(false);
            this.props.history.push("/list");
        }, 400);
    }
    render() {
        return (
            <div id="expenseForm">
                <Formik
                initialValues={this.initialValues}
                validate={values => this.validate(values)}
                onSubmit={(values, { setSubmitting }) => this.handleSubmit(values, setSubmitting)}>
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
                    }) => (
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

                            <label for="spend_date">Spend Date <span>{errors.spend_date && touched.spend_date && errors.spend_date}</span></label>
                            <input type="date" id="spend_date" name="spend_date" placeholder="Enter date"
                            onChange={handleChange}
                            onBlur={handleBlur}
                            value={values.spend_date} />

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
const mapDispatchToProps = {
    addExpense,
};
export default withRouter(connect(
    null,
    mapDispatchToProps
)(ExpenseEntryItemForm));
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

Enfin, nous avons réussi à créer une application react simple avec des fonctionnalités de base.

## Conclusion

React est l'un des frameworks d'interface utilisateur les plus populaires et les plus recommandés. Fidèle à sa popularité, il est développé depuis très longtemps et activement maintenu. L'apprentissage du framework React est un bon point de départ pour les développeurs frontaux et les aidera sûrement à améliorer leur carrière professionnelle.