## Introduction

React Hooks fournit un Hook spécial, ```useEffect()``` pour exécuter certaines fonctionnalités pendant le cycle de vie du composant. ```useEffect()``` combine le cycle de vie de componentDidMount, componentDidUpdate, et componentWillUnmount en une seule api.

La signature de l'api ```useEffect()``` est la suivante -

```js
useEffect(
    <executeFn>, 
    <values>
);
```

Ici,

- **executeFn** − Fonction à exécuter lorsqu'un effet se produit, avec une fonction de retour facultative. La fonction de retour sera exécutée lorsqu'un nettoyage est nécessaire (similaire à componentWillUnmount).
- **values** − tableau de valeurs dont dépend l'effet. Les React Hooks exécutent le executeFn uniquement lorsque les valeurs sont modifiées. Cela permet de réduire les appels inutiles de l'executeFn.

Ajoutons les crochets useEffect() dans notre application react-clock-hook-app.

Ouvrez react-clock-hook-app dans votre éditeur préféré.

Ensuite, ouvrez le fichier src/components/Clock.js et commencez à le modifier.

Ensuite, importez l'api useEffect.

```js
import React, { useState, useEffect } from 'react';
```

Ensuite, appelez useEffect avec une fonction pour définir la date et l'heure toutes les secondes à l'aide de setInterval et renvoyez une fonction pour arrêter la mise à jour de la date et de l'heure à l'aide de clearInterval.

```js
useEffect(
    () => {
        let setTime = () => {
            console.log("setTime is called");
            setCurrentDateTime(new Date());
        }
        let interval = setInterval(setTime, 1000);
        return () => {
            clearInterval(interval);
        }
    },
    []
);
```

Ici,

- Création d'une fonction, setTime, pour définir l'heure actuelle dans l'état du composant.
- Appel de l'api JavaScript setInterval pour exécuter setTime toutes les secondes et stocker la référence de setInterval dans la variable interval.
- Création d'une fonction de retour, qui appelle l'api clearInterval pour arrêter l'exécution de setTime chaque seconde en passant la référence de l'intervalle.

Maintenant, nous avons mis à jour le composant Horloge et le code source complet du composant est le suivant -

```js
import React, { useState, useEffect } from 'react';

function Clock() {
    const [currentDateTime, setCurrentDateTime] = useState(new Date());
    useEffect(
        () => {
            let setTime = () => {
                console.log("setTime is called");
                setCurrentDateTime(new Date());
            }
            let interval = setInterval(setTime, 1000);
            return () => {
                clearInterval(interval);
            }
        },
        []
    );
    return (
        <div>
            <p>The current time is {currentDateTime.toString()}</p>
        </div>
    );
}
export default Clock;
```

Ensuite, ouvrez index.js et utilisez setTimeout pour supprimer l'horloge du DOM après 5 secondes.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import Clock from './components/Clock';

ReactDOM.render(
    <React.StrictMode>
        <Clock />
    </React.StrictMode>,
    document.getElementById('root')
);
setTimeout(() => {
    ReactDOM.render(
        <React.StrictMode>
            <div><p>Clock is removed from the DOM.</p></div>
        </React.StrictMode>,
        document.getElementById('root')
    );
}, 5000);
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

L'horloge sera affichée pendant 5 secondes et ensuite, elle sera supprimée du DOM. En vérifiant le journal de la console, nous pouvons constater que le code de nettoyage est correctement exécuté.

## Propriété des enfants React aka Containment

React permet d'inclure un contenu d'interface utilisateur enfant arbitraire à l'intérieur du composant. Les enfants d'un composant sont accessibles via this.props.children. L'ajout d'enfants à l'intérieur d'un composant s'appelle le confinement. Le confinement est utilisé dans les situations où certaines sections du composant sont dynamiques par nature.

Par exemple, une boîte de message en texte riche peut ne pas connaître son contenu avant d'être appelée. Nous allons créer le composant RichTextMessage pour présenter la fonctionnalité de la propriété enfant de React dans ce chapitre.

Tout d'abord, créez une nouvelle application React, react-message-app en utilisant le bundler Create React App ou Rollup en suivant les instructions du chapitre Création d'une application React.

Ensuite, ouvrez l'application dans votre éditeur préféré.

Ensuite, créez le dossier src sous le répertoire racine de l'application.

Ensuite, créez un dossier de composants sous le dossier src.

Ensuite, créez un fichier, RichTextMessage.js, dans le dossier src/components et commencez à le modifier.

Ensuite, importez la bibliothèque React.

```js
import React from 'react';
```

Ensuite, créez une classe, RichTextMessage et appelez le constructeur avec les props.

```js
class RichTextMessage extends React.Component {
    constructor(props) { 
        super(props); 
    } 
}
```

Ensuite, ajoutez la méthode ```render()``` et affichez l'interface utilisateur du composant avec ses enfants.

```js
render() { 
    return ( 
        <div>{this.props.children}</div> 
    ) 
}
```

Ici,

- props.children renvoie les enfants du composant.
- Enveloppe les enfants dans une balise div.

Enfin, exportez le composant.

```js
export default RichTextMessage;
```

Le code source complet du composant RichTextMessage est donné ci-dessous -.

```js
import React from 'react';

class RichTextMessage extends React.Component {
    constructor(props) {
        super(props);
    }
    render() {
        return (
            <div>{this.props.children}</div>
        )
    }
}
export default RichTextMessage;
```

Ensuite, créez un fichier, index.js, dans le dossier src et utilisez le composant RichTextMessage.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import RichTextMessage from './components/RichTextMessage';

ReactDOM.render(
    <React.StrictMode>
        <RichTextMessage>
            <h1>Containment is really a cool feature.</h1>
        </RichTextMessage>
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

Le navigateur émet les enfants du composant enveloppés dans une balise div, comme indiqué ci-dessous.

```html
<div id="root">
    <div>
        <div>
            <h1>Containment is really a cool feature.</h1>
        </div>
    </div>
</div>
```

Ensuite, changez la propriété enfant du composant RichTextMessage dans index.js.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import Clock from './components/Clock';

ReactDOM.render(
    <React.StrictMode>
            <RichTextMessage>
                <h1>Containment is really an excellent feature.</h1>
            </RichTextMessage>
    </React.StrictMode>,
    document.getElementById('root')
);
```

Maintenant, le navigateur met à jour le contenu des enfants du composant et émet comme montré ci-dessous -

```html
<div id="root">
    <div>
        <div>
            <h1>Containment is really an excellent feature.</h1>
        </div>
    </div>
</div>
```

En bref, le confinement est une excellente fonctionnalité pour transmettre un contenu arbitraire de l'interface utilisateur au composant.