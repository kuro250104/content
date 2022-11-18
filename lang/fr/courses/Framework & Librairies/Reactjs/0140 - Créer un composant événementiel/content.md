## Introduction

Créons un nouveau composant, MessageWithEvent, et gérons les événements dans ce composant pour mieux comprendre la gestion des événements dans une application React.

Ouvrez l'application de gestion des dépenses dans votre éditeur préféré.

Ensuite, créez un fichier, MessageWithEvent.js dans le dossier src/components pour créer le composant MessageWithEvent.

Importez la bibliothèque React.

```js
import React from 'react';
```

Ensuite, créez une classe, MessageWithEvent et appelez le constructeur avec les props.

```js
class MessageWithEvent extends React.Component {   
    constructor(props) { 
        super(props); 
    } 
}
```

Ensuite, créez une méthode de gestion des événements, logEventToConsole, qui enregistrera les détails de l'événement dans la console.

```js
logEventToConsole(e) { 
    console.log(e.target.innerHTML); 
}
```

Ensuite, créez une fonction de rendu.

```js
render() { 
}
```

Ensuite, créez un message d'accueil et renvoyez-le.

```js
render() {
    return (
        <div>
            <p>Hello {this.props.name}!</p>
        </div>
    );
}
```

Ensuite, définissez la méthode logEventToConsole comme gestionnaire d'événement pour l'événement de clic du conteneur racine (div).

```js
render() {
    return (
        <div onClick={this.logEventToConsole}>
            <p>Hello {this.props.name}!</p>
        </div>
    );
}
```

Ensuite, mettez à jour le constructeur en liant le gestionnaire d'événements.

```js
class MessageWithEvent extends React.Component { 
    constructor(props) { 
        super(props); 
        this.logEventToConsole = this.logEventToConsole.bind(); 
    } 
}
```

Enfin, exportez le composant.

```js
export default MessageWithEvent;
```

Le code complet du composant MessageWithEvent est donné ci-dessous -

```js
import React from 'react';

class MessageWithEvent extends React.Component {
    constructor(props) {
        super(props);

        this.logEventToConsole = this.logEventToConsole.bind();
    }
    logEventToConsole(e) {
        console.log(e.target.innerHTML);
    }
    render() {
        return (
            <div onClick={this.logEventToConsole}>
                <p>Hello {this.props.name}!</p>
            </div>
        );
    }
}
export default MessageWithEvent;
```

Ensuite, ouvrez index.js et importez MessageWithEvent.

```js
import MessageWithEvent from './components/MessageWithEvent'
```

Ensuite, construisez l'interface utilisateur de l'application en utilisant le composant MessageWithEvent.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import MessageWithEvent from './components/MessageWithEvent'

ReactDOM.render(
    <React.StrictMode>
        <div>
                <MessageWithEvent name="React" />
                <MessageWithEvent name="React developer" />
        </div>
    </React.StrictMode>,
    document.getElementById('root')
);
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

Maintenant, cliquez sur les deux composants MessageWithEvent et l'application émettra des messages dans la console.

Essayons de passer une information supplémentaire (par exemple, msgid) au gestionnaire d'événement.

Tout d'abord, mettez à jour le logEventToConsole pour accepter un argument supplémentaire, msgid.

```js
logEventToConsole(msgid, e) { 
    console.log(e.target.innerHTML); 
    console.log(msgid); 
}
```

Ensuite, transmettez l'identifiant du message au gestionnaire d'événements en liant l'identifiant du message dans la méthode de rendu.

```js
render() {
    return (
        <div onClick={this.logEventToConsole.bind(this, Math.floor(Math.random() * 10))}>
            <p>Hello {this.props.name}!</p>
        </div>
    );
}
```

Le code complet et mis à jour est le suivant -

```js
import React from 'react';

class MessageWithEvent extends React.Component {
    constructor(props) {
        super(props);

        this.logEventToConsole = this.logEventToConsole.bind();
    }
    logEventToConsole(msgid, e) {
        console.log(e.target.innerHTML);
        console.log(msgid);
    }
    render() {
        return (
            >div onClick={this.logEventToConsole.bind(this, Math.floor(Math.random() * 10))}>
                >p>Hello {this.props.name}!>/p>
            >/div>
        );
    }
}
export default MessageWithEvent;
```

Exécutez l'application et vous constaterez que l'événement émet le message id dans la console.