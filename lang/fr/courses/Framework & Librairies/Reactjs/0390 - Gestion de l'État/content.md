## Introduction

Nous allons faire l'action suivante pour gérer notre magasin redux.

- Récupérer les dépenses du serveur par l'api async fetch et les placer dans le magasin Redux.
- Ajouter une nouvelle dépense au serveur par la programmation async fetch et set ajouter la nouvelle dépense dans le magasin Redux.
- Supprimez les dépenses existantes du serveur via l'api async fetch et mettez à jour le magasin Redux.

Créons des types d'action, un créateur d'action, des actions et des réducteurs pour gérer l'état de Redux.

Créez un dossier actions sous le dossier src.

Ensuite, créez un fichier, types.js, pour créer des types d'action.

```js
export const LIST_EXPENSE_STARTED = 'LIST_EXPENSE_STARTED';
export const LIST_EXPENSE_SUCCESS = 'LIST_EXPENSE_SUCCESS';
export const LIST_EXPENSE_FAILURE = 'LIST_EXPENSE_FAILURE';

export const ADD_EXPENSE_STARTED = 'ADD_EXPENSE_STARTED';
export const ADD_EXPENSE_SUCCESS = 'ADD_EXPENSE_SUCCESS';
export const ADD_EXPENSE_FAILURE = 'ADD_EXPENSE_FAILURE';

export const DELETE_EXPENSE_STARTED = 'DELETE_EXPENSE_STARTED';
export const DELETE_EXPENSE_SUCCESS = 'DELETE_EXPENSE_SUCCESS';
export const DELETE_EXPENSE_FAILURE = 'DELETE_EXPENSE_FAILURE';
```

Ensuite, créez un fichier, index.js sous le dossier actions pour créer des créateurs d'actions.

```js
import {
    LIST_EXPENSE_STARTED, LIST_EXPENSE_SUCCESS, LIST_EXPENSE_FAILURE,
    ADD_EXPENSE_STARTED, ADD_EXPENSE_SUCCESS, ADD_EXPENSE_FAILURE,
    DELETE_EXPENSE_STARTED, DELETE_EXPENSE_SUCCESS, DELETE_EXPENSE_FAILURE,
} from "./types";
export const getExpenseListStarted = () => {
    return {
        type: LIST_EXPENSE_STARTED
    }
}
export const getExpenseListSuccess = data => {
    return {
        type: LIST_EXPENSE_SUCCESS,
        payload: {
            data
        }
    }
}
export const getExpenseListFailure = error => {
    return {
        type: LIST_EXPENSE_FAILURE,
        payload: {
            error
        }
    }
}
export const addExpenseStarted = () => {
    return {
        type: ADD_EXPENSE_STARTED
    }
}
export const addExpenseSuccess = data => {
   return {
      type: ADD_EXPENSE_SUCCESS,
      payload: {
         data
      }
   }
}
export const addExpenseFailure = error => {
    return {
        type: ADD_EXPENSE_FAILURE,
        payload: {
            error
        }
    }
}
export const deleteExpenseStarted = () => {
    return {
        type: DELETE_EXPENSE_STARTED
    }
}
export const deleteExpenseSuccess = data => {
    return {
        type: DELETE_EXPENSE_SUCCESS,
        payload: {
            data
        }
    }
}
export const deleteExpenseFailure = error => {
    return {
        type: DELETE_EXPENSE_FAILURE,
        payload: {
            error
        }
    }
}
```

Ici, nous avons créé un créateur d'action pour chaque résultat possible (succès, échec et erreur) de l'api fetch. Comme nous allons utiliser trois appels d'api web et que chaque appel aura trois résultats possibles, nous utilisons 9 créateurs d'action.

Ensuite, créez un fichier, expenseActions.js, dans le dossier actions, et créez trois fonctions pour récupérer, ajouter et supprimer des dépenses et pour répartir les changements d'état.

```js
import {
    getExpenseListStarted, getExpenseListSuccess, getExpenseListFailure,
    addExpenseStarted, addExpenseSuccess, addExpenseFailure,
    deleteExpenseStarted, deleteExpenseSuccess, deleteExpenseFailure
} from "./index";
export const getExpenseList = () => async dispatch => {
    dispatch(getExpenseListStarted());
    try {
        const res = await fetch('http://localhost:8000/api/expenses');
        const data = await res.json();
        var items = [];
        data.forEach((item) => {
            let newItem = {
                id: item._id,
                name: item.name,
                amount: item.amount,
                spendDate: item.spend_date,
                category: item.category
            }
            items.push(newItem)
        });
        dispatch(getExpenseListSuccess(items));
    } catch (err) {
        dispatch(getExpenseListFailure(err.message));
    }
}
export const addExpense = (data) => async dispatch => {
    dispatch(addExpenseStarted());

    let newItem = {
        name: data.name,
        amount: data.amount,
        spend_date: data.spendDate,
        category: data.category
    }
    console.log(newItem);
    try {
        const res = await fetch('http://localhost:8000/api/expense', {
            method: 'POST',
            body: JSON.stringify(newItem),
            headers: {
                "Content-type": "application/json; charset=UTF-8"
            } 
        });
        const data = await res.json();
        newItem.id = data._id;
        dispatch(addExpenseSuccess(newItem));
    } catch (err) {
        console.log(err);
        dispatch(addExpenseFailure(err.message));
    }
}
export const deleteExpense = (id) => async dispatch => {
    dispatch(deleteExpenseStarted());
    try {
        const res = await fetch('http://localhost:8000/api/expense/' + id, {
            method: 'DELETE'
        });
        const data = await res.json();
        dispatch(deleteExpenseSuccess(id));
    } catch (err) {
        dispatch(deleteExpenseFailure(err.message));
    }
}
```

Ici,

- Utilisation de l'api async fetch pour faire des appels à l'api web.
- Utilisation de la fonction de répartition pour déclencher l'action appropriée en cas de succès, d'échec ou d'erreur.

Créez un dossier, reducers sous le dossier src et créez un fichier, index.js sous le dossier reducers pour créer des reducers Redux.

```js
import {
    LIST_EXPENSE_STARTED, LIST_EXPENSE_SUCCESS, LIST_EXPENSE_FAILURE,
    ADD_EXPENSE_STARTED, ADD_EXPENSE_SUCCESS, ADD_EXPENSE_FAILURE,
    DELETE_EXPENSE_STARTED, DELETE_EXPENSE_SUCCESS, DELETE_EXPENSE_FAILURE
} from "../actions/types";

// define initial state of user
const initialState = {
    data: null,
    loading: false,
    error: null
}
export default function expenseReducer(state = initialState, action) {
    switch (action.type) {
        case LIST_EXPENSE_STARTED:
            return {
                ...state,
                loading: true
            }
        case LIST_EXPENSE_SUCCESS:
            const { data } = action.payload;
            return {
                ...state,
                data,
                loading: false
            }
        case LIST_EXPENSE_FAILURE:
            const { error } = action.payload;
            return {
                ...state,
                error
            }
        case ADD_EXPENSE_STARTED:
            return {
                ...state,
                loading: true
            }
        case ADD_EXPENSE_SUCCESS:
            return {
                ...state,
                loading: false
            }
        case ADD_EXPENSE_FAILURE:
            const { expenseError } = action.payload;
            return {
                ...state,
                expenseError
            }
        case DELETE_EXPENSE_STARTED:
            return {
                ...state,
                loading: true
            }
        case DELETE_EXPENSE_SUCCESS:
            return {
                ...state,
                data: state.data.filter(expense => expense.id !== action.payload.data),
                loading: false
            }
        case DELETE_EXPENSE_FAILURE:
            const { deleteError } = action.payload;
            return {
                ...state,
                deleteError
            }
        default:
            return state
    }
}
```

Ici, nous avons mis à jour l'état du magasin redux pour chaque type d'action.

Ensuite, ouvrez le fichier index.js dans le dossier src et incluez le composant Provider pour que tous les composants puissent se connecter et travailler avec le magasin redux.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import { createStore, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';
import { Provider } from 'react-redux';
import rootReducer from './reducers';
import App from './components/App';

const store = createStore(rootReducer, applyMiddleware(thunk));

ReactDOM.render(
    <Provider store={store}>
        <App />
    </Provider>,
    document.getElementById('root')
    );
```

Ici,

- Importation de createStore et applyMiddleware
- Importation de thunk de la bibliothèque redux-thunk (pour l'api async fetch)
- Fournisseur importé de la bibliothèque redux
- Création d'un nouveau magasin à l'aide de createStore en configurant le reducer et le thunk middleware.
- Attachement du composant Provider comme composant de premier niveau avec redux store