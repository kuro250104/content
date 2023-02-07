## Introduction

En général, React permet au composant d'être stylé en utilisant une classe CSS à travers l'attribut className. Étant donné que React JSX prend en charge les expressions JavaScript, un grand nombre de méthodes CSS courantes peuvent être utilisées. Certaines des principales options sont les suivantes

- **CSS stylesheet** − Styles CSS normaux avec className ;
- **Inline styling** − Les styles CSS en tant qu'objets JavaScript avec les propriétés camelCase ;
- **CSS Modules** − Styles CSS à portée locale ;
- **Styled component** − Styles au niveau des composants ;
- **Sass stylesheet** − Supporte les styles CSS basés sur Sass en convertissant les styles en css normal au moment de la construction ; 
- **Post processing stylesheet** − Supporte les styles de post-traitement en convertissant les styles en css normaux au moment de la construction.

Dans ce cours, nous allons apprendre à appliquer ces trois méthodes importantes pour styliser notre composant.

- CSS Stylesheet
- Inline Styling
- CSS Modules

## CSS Stylesheet

La feuille de style CSS est une méthode habituelle, courante et éprouvée. Il suffit de créer une feuille de style CSS pour un composant et de saisir tous vos styles pour ce composant particulier. Ensuite, dans le composant, utilisez className pour faire référence aux styles.

Stylisons notre composant ExpenseEntryItem.

Ouvrez l'application de gestion des dépenses dans votre éditeur préféré.

Ensuite, ouvrez le fichier ExpenseEntryItem.css et ajoutez quelques styles.

```css
div.itemStyle { 
    color: brown; 
    font-size: 14px; 
}
```

Ensuite, ouvrez ExpenseEntryItem.js et ajoutez className au conteneur principal.

```js
import React from 'react';
import './ExpenseEntryItem.css';

class ExpenseEntryItem extends React.Component {
    render() {
        return (
            <div className="itemStyle">
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

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

La feuille de style CSS est facile à comprendre et à utiliser. Mais, lorsque la taille du projet augmente, les styles CSS augmentent également et créent finalement beaucoup de conflits dans le nom des classes. De plus, le chargement direct du fichier CSS n'est pris en charge que par le bundler Webpack et peut ne pas l'être par d'autres outils.

## Inline Styling

Le stylisme en ligne est l'un des moyens les plus sûrs de styliser le composant React. Elle déclare tous les styles en tant qu'objets JavaScript à l'aide de propriétés css basées sur le DOM et les définit pour le composant par le biais d'attributs de style.

Ajoutons du style en ligne dans notre composant.

Ouvrez l'application expense-manager dans votre éditeur préféré et modifiez le fichier ExpenseEntryItem.js dans le dossier src. Déclarez une variable de type objet et définissez les styles.

```css
itemStyle = {
    color: 'brown', 
    fontSize: '14px' 
}
```

Ici, fontSize représente la propriété css, font-size. Toutes les propriétés css peuvent être utilisées en les représentant au format camelCase.

Ensuite, définissez le style itemStyle dans le composant en utilisant les accolades {} :

```js
render() {
    return (
        <div style={ this.itemStyle }>
            <div><b>Item:</b> <em>Mango Juice</em></div>
            <div><b>Amount:</b> <em>30.00</em></div>
            <div><b>Spend Date:</b> <em>2020-10-10</em></div>
            <div><b>Category:</b> <em>Food</em></div>
        </div>
    );
}
```

De plus, le style peut être défini directement dans le composant.

```js
render() {
    return (
        <div style={
            {
                color: 'brown',
                fontSize: '14px'
            }         
        }>
            <div><b>Item:</b> <em>Mango Juice</em></div>
            <div><b>Amount:</b> <em>30.00</em></div>
            <div><b>Spend Date:</b> <em>2020-10-10</em></div>
            <div><b>Category:</b> <em>Food</em></div>
        </div>
    );
}
```

Maintenant, nous avons réussi à utiliser le style en ligne dans notre application.

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

## CSS Modules

Css Modules offre le moyen le plus sûr et le plus simple de définir le style. Il utilise une feuille de style css normale avec une syntaxe normale. Lors de l'importation des styles, les modules CSS convertissent tous les styles en styles à portée locale afin d'éviter les conflits de noms. Changeons notre composant pour utiliser les modules CSS

Ouvrez l'application de gestion des dépenses dans votre éditeur préféré.

Ensuite, créez une nouvelle feuille de style, le fichier ExpenseEntryItem.module.css sous le dossier src/components et écrivez des styles css réguliers.

```css
div.itemStyle {
    color: 'brown'; 
    font-size: 14px; 
}
```

Ici, la convention de dénomination des fichiers est très importante. La chaîne d'outils React prétraitera les fichiers css se terminant par .module.css via le module CSS. Sinon, il sera considéré comme une feuille de style normale.

Ensuite, ouvrez le fichier ExpenseEntryItem.js dans le dossier src/component et importez les styles.

```js
import styles from './ExpenseEntryItem.module.css'
```

Ensuite, utilisez les styles comme expression JavaScript dans le composant.

```html
<div className={styles.itemStyle}>
```

Maintenant, nous avons utilisé avec succès les modules CSS dans notre application.

Le code final et complet est -

```js
import React from 'react';
import './ExpenseEntryItem.css';
import styles from './ExpenseEntryItem.module.css'

class ExpenseEntryItem extends React.Component {
   render() {
      return (
         <div className={styles.itemStyle} >
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

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

