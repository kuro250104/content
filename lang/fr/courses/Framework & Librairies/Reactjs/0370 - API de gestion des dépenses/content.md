## Introduction

Tout d'abord, créez une nouvelle application API Rest expense en suivant les instructions de Http Client Programming -> Expense Rest API Server et démarrez le serveur. Le serveur de dépenses sera exécuté à l'adresse http://localhost:8000.

## Create a skeleton application

Ouvrez un terminal et allez dans votre espace de travail.

```bash
> cd /go/to/your/workspace
```

Ensuite, créez une nouvelle application React à l'aide de l'outil Create React App.

```bash
> create-react-app react-expense-app
```

Il va créer un nouveau dossier react-expense-app avec le code du modèle de démarrage.

Ensuite, allez dans le dossier expense-manager et installez la bibliothèque nécessaire.

```bash
cd react-expense-app 
npm install
```

L'installation de npm installera la bibliothèque nécessaire dans le dossier node_modules.

Supprimez tous les fichiers sous src et le dossier public.

Ensuite, créez un dossier, components sous src pour inclure nos composants React. La structure finale de l'application sera la suivante :

```bash
|-- package-lock.json
|-- package.json
`-- public
   |-- index.html
`-- src
   |-- index.js
   `-- components
   |   |-- mycom.js
   |   |-- mycom.css
```

Créons notre composant racine, App, qui rendra l'application entière.

Créez un fichier, App.js, dans le dossier components et écrivez un composant simple pour émettre un message Hello World.

```js
import React from "react";

class App extends React.Component {
    render() {
        return (
            <div>
                <h1>Hello World!</h1>
            </div>
        );
    }
}
export default App;
```

Ensuite, créez notre fichier principal, index.js sous le dossier src et appelez notre composant nouvellement créé.

```js
import React from 'react';
import ReactDOM from 'react-dom';

import App from './components/App'

ReactDOM.render(
    <React.StrictMode>
        <App />
    </React.StrictMode>,
    document.getElementById('root')
);
```

Ensuite, créez un fichier html, index.html (sous le dossier public), qui sera notre point d'entrée dans l'application.

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>Expense App</title>
    </head>
    <body>
        <div id="root"></div>
    </body>
</html>
```

Ensuite, servez l'application en utilisant la commande npm.

```bash
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.
