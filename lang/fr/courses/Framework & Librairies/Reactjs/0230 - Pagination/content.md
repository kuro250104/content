## Introduction

La pagination est l'une des caractéristiques distinctes nécessitant une logique spéciale et, dans le même temps, le rendu de l'interface utilisateur peut varier radicalement. Par exemple, la pagination peut être effectuée pour un contenu tabulaire ou pour un contenu de galerie. Le composant de pagination se charge de la logique de pagination et délègue la logique de rendu à d'autres composants. Essayons de créer un composant de pagination (Pager) pour notre application de gestion des dépenses en utilisant les props de rendu.

Ouvrez l'application de gestion des dépenses dans votre éditeur préféré.

Ensuite, créez un fichier, Pager.css sous src/components pour ajouter des styles pour le composant de pagination.

```css
a{
   text-decoration: none;
}
p, li, a{
   font-size: 12px;
} 
.container{
    width: 720px;
    max-width: 340px;
    margin: 0 auto;
    position: relative;
    text-align: center;
}
.pagination{
    padding: 14px 0;
}
.pagination ul{
    margin: 0 auto; 
    padding: 0;
    list-style-type: none;
    text-align: left;
}
.pagination a{
    display: inline-block;
    padding: 10px 18px;
    color: #222;
}
.p1 a{
    width: 30px;
    height: 30px;
    line-height: 30px;
    padding: 0;
    text-align: center;
}
.p1 a.is-active{
    background-color: #887cb8;
    border-radius: 25%;
    color: #fff;
}
```

Ensuite, créez un fichier, Pager.js dans le dossier src/components pour créer le composant Pager et commencez à le modifier.

Ensuite, importez la bibliothèque React.

```js
import React from 'react';
```

Ensuite, importez la feuille de style de la pagination.

```js
import './Pager.css'
```

Ensuite, créez une classe, Pager et appelez le constructeur avec des props.

```js
class Pager extends React.Component { 
    constructor(props) { 
        super(props); 
    } 
}
```

Ensuite, initialiser l'état du composant avec les éléments de dépense (items) et le nombre d'éléments à afficher dans une page (pageCount).

```js
this.state = { 
    items: this.props.items, 
    pageCount: this.props.pageCount 
}
```

Écrivez une fonction, ```calculate()```, qui accepte l'état actuel et le numéro de page actuel. Elle calcule le total des pages disponibles en fonction du nombre de pages et des éléments à afficher dans la page actuelle (filteredItems). Enfin, elle renvoie les valeurs calculées.

```js
calculate(state, pageNo) {
    let currentPage = pageNo;
    let totalPages = Math.ceil(state.items.length / state.pageCount);
    if(currentPage > totalPages) currentPage = totalPages;
    let hasPreviousPage = currentPage == 1 ? false : true;
    let hasNextPage = currentPage == totalPages ? false : true;
    let first = (currentPage - 1) * state.pageCount
    let last = first + state.pageCount;
    let filteredItems = state.items.slice(first, last)

    let newState = {
        items: state.items,
        filteredItems: filteredItems,
        currentPage: currentPage,
        totalPages: totalPages,
        pageCount: state.pageCount
    }
    return newState;
}
```

Ensuite, appelez la méthode ```calculate()``` dans le constructeur pour obtenir les premiers détails sur la pagination.

```js
this.state = this.calculate(this.state, 1);
```

Ensuite, écrivez une méthode de gestion d'événement, handleClick, pour gérer l'événement de navigation de page du composant de pagination.

```js
handleClick(pageNo, e) { 
    e.preventDefault();
    this.setState((state, props) => {
        return this.calculate(state, pageNo);
    })
}
```

Ensuite, écrivez un gestionnaire d'événement pour supprimer l'élément de dépense. Puisque le composant pager gère tous les postes de dépenses, la fonction de suppression doit être déplacée ici.

```js
handleDelete = (id, e) => {
    e.preventDefault();
    console.log(id);
    this.setState((state, props) => {
        let items = [];

        state.items.forEach((item, idx) => {
            if (item.id != id)
                items.push(item)
        })
        let newState = {
            items: items
        }
        return newState;
    })
    this.setState((state, props) => {
        return this.calculate(state, this.state.currentPage);
    })
}
```

Ensuite, créez une méthode de rendu pour créer l'interface utilisateur de la pagination, puis appelez les props de rendu en passant les éléments nécessaires au rendu de la page actuelle.

```js
render() {
    let pageArray = new Array();
    let i = 1;
    for (i = 1; i <= this.state.totalPages; i++)
        pageArray.push(i)

    const pages = pageArray.map((idx) =>
        <a href="#" key={idx} onClick={this.handleClick.bind(this, idx)} className={idx == this.state.currentPage ? "is-active" : ""}><li>{idx}</li></a>
    );
    let propsToPass = {
        items: this.state.filteredItems,
        deleteHandler: this.handleDelete
    }
    return (
        <div>
            {this.props.render(propsToPass)}
            <div style={{ width: 720, margin: 0 }}>
                <div className="container">
                <div className="pagination p1">
                    <ul>
                        {this.state.currentPage != 1 ? <a href="#" onClick={this.handleClick.bind(this, this.state.currentPage - 1)}><li><</li></a> : <span> </span>}
                        {pages}
                        {this.state.currentPage != this.state.totalPages ?
                        <a href="#" onClick={this.handleClick.bind(this, this.state.currentPage + 1)}><li>></li></a> : <span> </span>}
                    </ul>
                </div>
                </div>
            </div>
        </div>
    )
}
```

Ici,

- Carte utilisée pour créer les boutons de pagination.
- Utilisation du rendu conditionnel pour afficher/masquer la première et la dernière page.
- Utilisation de this.props.render pour appeler et rendre le composant transmis.

Enfin, exportez le composant.

```js
export default Pager
```

Le code complet du composant Pager est le suivant :

```js
import React from 'react';
import './Pager.css'

class Pager extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            items: this.props.items,
            pageCount: this.props.pageCount,
        }
        this.state = this.calculate(this.state, 1);
    }
    calculate(state, pageNo) {
        let currentPage = pageNo;
        let totalPages = Math.ceil(state.items.length / state.pageCount);
        if(currentPage > totalPages) currentPage = totalPages;
        let hasPreviousPage = currentPage == 1 ? false : true;
        let hasNextPage = currentPage == totalPages ? false : true;
        let first = (currentPage - 1) * state.pageCount
        let last = first + state.pageCount;
        let filteredItems = state.items.slice(first, last)
        let newState = {
            items: state.items,
            filteredItems: filteredItems,
            currentPage: currentPage,
            totalPages: totalPages,
            pageCount: state.pageCount
        }
        return newState;
    }
    handleClick(pageNo, e) {
        e.preventDefault();
        this.setState((state, props) => {
            return this.calculate(state, pageNo);
        })
    }
    handleDelete = (id, e) => {
        e.preventDefault();
        console.log(id);

        this.setState((state, props) => {
            let items = [];
            state.items.forEach((item, idx) => {
                if (item.id != id)
                items.push(item)
            })
            let newState = {
                items: items
            }
            return newState;
        })
        this.setState((state, props) => {
            return this.calculate(state, this.state.currentPage);
        })
    }
    render() {
        let pageArray = new Array();
        let i = 1;
        for (i = 1; i <= this.state.totalPages; i++)pageArray.push(i)
        
        const pages = pageArray.map((idx) =>
            <a href="#" key={idx} onClick={this.handleClick.bind(this, idx)} className={idx == this.state.currentPage ? "is-active" : ""}><li>{idx}</li></a>
        );
        let propsToPass = {
            items: this.state.filteredItems,
            deleteHandler: this.handleDelete
        }
        return (
            <div>
                {this.props.render(propsToPass)}
    
                <div style={{ width: 720, margin: 0 }}>
                <div className="container">
                    <div className="pagination p1">
                        <ul>
                            {this.state.currentPage != 1 ? <a href="#" onClick={this.handleClick.bind(this, this.state.currentPage - 1)}><li><</li></a> : <span> </span>}
                            {pages}
                            {this.state.currentPage != this.state.totalPages ?
                            <a href="#" onClick={this.handleClick.bind(this, this.state.currentPage + 1)}><li>></li></a> : <span> </span>}
                        </ul>
                    </div>
                </div>
                </div>
            </div>
        )
    }
}
export default Pagerimport React from 'react';
import './Pager.css'

class Pager extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            items: this.props.items,
            pageCount: this.props.pageCount,
        }
        this.state = this.calculate(this.state, 1);
    }
    calculate(state, pageNo) {
        let currentPage = pageNo;
        let totalPages = Math.ceil(state.items.length / state.pageCount);

        if(currentPage > totalPages)currentPage = totalPages;
            
        let hasPreviousPage = currentPage == 1 ? false : true;
        let hasNextPage = currentPage == totalPages ? false : true;
        let first = (currentPage - 1) * state.pageCount
        let last = first + state.pageCount;
        let filteredItems = state.items.slice(first, last)
    
        let newState = {
            items: state.items,
            filteredItems: filteredItems,
            currentPage: currentPage,
            totalPages: totalPages,
            pageCount: state.pageCount
        }
        return newState;
    }
    handleClick(pageNo, e) {
        e.preventDefault();
    
        this.setState((state, props) => {
            return this.calculate(state, pageNo);
        })
    }
    handleDelete = (id, e) => {
        e.preventDefault();
        console.log(id);

        this.setState((state, props) => {
            let items = [];

            state.items.forEach((item, idx) => {
                if (item.id != id)
                items.push(item)
            })
            let newState = {
                items: items
            }
            return newState;
        })
        this.setState((state, props) => {
            return this.calculate(state, this.state.currentPage);
        })
    }
    render() {
        let pageArray = new Array();
        let i = 1;
        for (i = 1; i <= this.state.totalPages; i++)pageArray.push(i)
    
        const pages = pageArray.map((idx) =>
            <a href="#" key={idx} onClick={this.handleClick.bind(this, idx)} className={idx == this.state.currentPage ? "is-active" : ""}><li>{idx}</li></a>
        );

        let propsToPass = {
            items: this.state.filteredItems,
            deleteHandler: this.handleDelete
        }
        return (
            <div>
                {this.props.render(propsToPass)}
    
                <div style={{ width: 720, margin: 0 }}>
                <div className="container">
                    <div className="pagination p1">
                        <ul>
                            {this.state.currentPage != 1 ? <a href="#" onClick={this.handleClick.bind(this, this.state.currentPage - 1)}><li><</li></a> : <span> </span>}
                            {pages}
                            {this.state.currentPage != this.state.totalPages ?
                            <a href="#" onClick={this.handleClick.bind(this, this.state.currentPage + 1)}><li>></li></a> : <span> </span>}
                        </ul>
                    </div>
                </div>
                </div>
            </div>
        )
    }
}
export default Pager
```

Ensuite, ouvrez le fichier ExpenseEntryItemeList.js et mettez à jour la fonction getDerivedStateFromProps pour obtenir la liste actuelle des postes de dépenses en copiant les props transmis dans le nouvel état.

```js
static getDerivedStateFromProps(props, state) {
    let newState = {
        items: props.items
    }
    return newState;
}
```

Ensuite, mettez à jour la méthode handleDelete et appelez la méthode du gestionnaire d'événements passée dans le composant à partir du composant pager via la propriété onDelete.

```js
handleDelete = (id, e) => {
    e.preventDefault();

    if(this.props.onDelete != null)this.props.onDelete(id, e);
}
```

Ensuite, supprimez le rendu de l'en-tête et du pied de page, s'ils sont disponibles dans la méthode de rendu.

```js
return (
    <div>
        <div>{this.props.header}</div>
            ... existing code ...
        <div>{this.props.footer}</div>
    </div>
);
```

Le code source complet du composant ExpenseEntryItemList est donné ci-dessous

```js
import React from 'react';
import './ExpenseEntryItemList.css';

class ExpenseEntryItemList extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            items: this.props.items
        }
        this.handleMouseEnter = this.handleMouseEnter.bind();
        this.handleMouseLeave = this.handleMouseLeave.bind();
        this.handleMouseOver = this.handleMouseOver.bind();
    }
    handleMouseEnter(e) {
        e.target.parentNode.classList.add("highlight");
    }
        handleMouseLeave(e) {
        e.target.parentNode.classList.remove("highlight");
    }
    handleMouseOver(e) {
        console.log("The mouse is at (" + e.clientX + ", " + e.clientY + ")");
    }
    handleDelete = (id, e) => {
        e.preventDefault();

        if(this.props.onDelete != null)this.props.onDelete(id, e);
            
        /*console.log(id);

        this.setState((state, props) => {
            let items = [];
            state.items.forEach((item, idx) => {
                if (item.id != id)
                items.push(item)
            })
            let newState = {
                items: items
            }
            return newState;
        })*/
    }
    getTotal() {
        let total = 0;
        for (var i = 0; i < this.state.items.length; i++) {
            total += this.state.items[i].amount
        }
        return total;
    }
    static getDerivedStateFromProps(props, state) {
        let newState = {
            items: props.items
        }
        return newState;
    }
    render() {
        const lists = this.state.items.map((item) =>
            <tr key={item.id} onMouseEnter={this.handleMouseEnter} onMouseLeave={this.handleMouseLeave}>
                <td>{item.name}</td>
                <td>{item.amount}</td>
                <td>{new Date(item.spendDate).toDateString()}</td>
                <td>{item.category}</td>
                <td><a href="#"
                onClick={(e) => this.handleDelete(item.id, e)}>Remove</a></td>
            </tr>
        );
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
                    <tr>
                        <td colSpan="1" style={{ textAlign: "right" }}>Total Amount</td>
                        <td colSpan="4" style={{ textAlign: "left" }}>
                            {this.getTotal()}
                        </td>
                    </tr>
                </tbody>
                </table>
            </div>
        );
    }
}
export default ExpenseEntryItemList;
```

Ensuite, ouvrez index.js et appelez le composant Pager et passez la liste ExpenseEntryItemList comme render props.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import Pager from './components/Pager'
import ExpenseEntryItemList from './components/ExpenseEntryItemList'

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
const pageCount = 3;
ReactDOM.render(
    <React.StrictMode>
        <Pager
            items={items}
            pageCount={pageCount}
            render={
                pagerState => (
                <div>
                    <ExpenseEntryItemList items={pagerState.items} 
                            onDelete={pagerState.deleteHandler} />
                </div>
                )
            }
        />
    </React.StrictMode>,
    document.getElementById('root')
);
```

Comme nous le voyons, le composant Pager accepte n'importe quel props de rendu et ne calcule que la logique de pagination.

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.