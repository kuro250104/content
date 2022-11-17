## Introduction

Comme nous l'avons appris précédemment, le composant React est le bloc de construction d'une application React. Un composant React est constitué de plusieurs composants individuels. React permet de combiner plusieurs composants pour créer des composants plus grands. En outre, les composants React peuvent être imbriqués à n'importe quel niveau arbitraire. Voyons comment les composants React peuvent être composés dans ce chapitre.

## Composant argent formaté

Créons un composant, FormattedMoney, pour formater le montant à deux décimales avant le rendu.

Ouvrez notre application de gestion des dépenses dans votre éditeur préféré.

Ensuite, créez un fichier FormattedMoney.js dans le dossier src/components et importez la bibliothèque React.

```js
import React from 'react';
```

Ensuite, créez une classe, FormattedMoney en étendant React.Component.

```js
class FormattedMoney extends React.Component { 
}
```

Ensuite, introduisez la fonction de construction avec les arguments props comme indiqué ci-dessous -

```js
constructor(props) { 
    super(props); 
}
```

Ensuite, créez un format de méthode pour mettre en forme le montant.

```js
format(amount) { 
    return parseFloat(amount).toFixed(2) 
}
```

Ensuite, créez une méthode render pour émettre le montant formaté.

```js
render() {
    return (
        <span>{this.format(this.props.value)}</span> 
    ); 
}
```

Ici, nous avons utilisé la méthode de formatage en passant l'attribut valeur à travers this.props.

Ensuite, spécifiez le composant comme classe d'exportation par défaut.

```js
export default FormattedMoney;
```

Maintenant, nous avons créé avec succès notre composant React FormattedMoney.

```js
import React from 'react';

class FormattedMoney extends React.Component {
    constructor(props) {
        super(props)
    }
    format(amount) {
        return parseFloat(amount).toFixed(2)
    }
    render() {
        return (
            <span>{this.format(this.props.value)}</span>
        );
    }
}
export default FormattedMoney;
```

## Composant FormattedDate

Créons un autre composant, FormattedDate, pour formater et afficher la date et l'heure de la dépense.

Ouvrez notre application de gestion des dépenses dans votre éditeur préféré.

Ensuite, créez un fichier, FormattedDate.js, dans le dossier src/components.

Ensuite, importez la bibliothèque React.

```js
import React from 'react';
```

Ensuite, créez une classe en étendant React.Component.

```js
class FormattedDate extends React.Component { 
}
```

Ensuite, introduisez la fonction de construction avec les arguments props comme indiqué ci-dessous -

```js
constructor(props) { 
    super(props); 
}
```

Ensuite, créez un format de méthode pour formater la date.

```js
format(val) {
    const months = ["JAN", "FEB", "MAR","APR", "MAY", "JUN", "JUL", "AUG", "SEP", "OCT", "NOV", "DEC"];
    let parsed_date = new Date(Date.parse(val));
    let formatted_date = parsed_date.getDate() + 
        "-" + months[parsed_date.getMonth()] + 
        "-" + parsed_date.getFullYear()
    return formatted_date;
}
```

Créez une méthode render pour émettre la date formatée.

```js
render() { return ( <span>{this.format(this.props.value)}</span> ); }
```

Ici, nous avons utilisé la méthode de formatage en passant l'attribut valeur à travers this.props.

Ensuite, spécifiez le composant comme classe d'exportation par défaut.

```js
export default FormattedDate;
```

Maintenant, nous avons créé avec succès notre composant React FormattedDate. Le code complet est le suivant -

```js
import React from 'react';
class FormattedDate extends React.Component {
    constructor(props) {
        super(props)
    }
    format(val) {
        const months = ["JAN", "FEB", "MAR","APR", "MAY", "JUN", "JUL", "AUG", "SEP", "OCT", "NOV", "DEC"];
        let parsed_date = new Date(Date.parse(val));
        let formatted_date = parsed_date.getDate() + 
            "-" + months[parsed_date.getMonth()] + 
            "-" + parsed_date.getFullYear()
        return formatted_date;
    }
    render() {
        return (
            <span>{this.format(this.props.value)}</span>
        );
    }
}
export default FormattedDate;
```