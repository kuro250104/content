## Introduction

L'animation est une fonctionnalité intéressante des applications web modernes. Elle donne une sensation rafraîchissante à l'application. La communauté React fournit plusieurs excellentes bibliothèques d'animation basées sur React, comme React Motion, React Reveal, react-animations, etc. React lui-même fournit une bibliothèque d'animation, React Transition Group, en tant qu'option supplémentaire. Il s'agit d'une bibliothèque indépendante qui améliore la version précédente de la bibliothèque. Nous allons apprendre la bibliothèque d'animation React Transition Group dans ce chapitre.

## React Transition Group

La bibliothèque React Transition Group est une implémentation simple de l'animation. Elle ne fait pas d'animation à proprement parler. Au lieu de cela, elle expose les informations de base liées à l'animation. Chaque animation est fondamentalement la transition d'un élément d'un état à un autre. La bibliothèque expose le minimum d'états possibles pour chaque élément, comme indiqué ci-dessous.

- Entering
- Entered
- Exiting
- Exited

La bibliothèque offre des options permettant de définir un style CSS pour chaque état et d'animer l'élément en fonction de ce style lorsque l'élément passe d'un état à un autre. La bibliothèque fournit in props pour définir l'état actuel de l'élément. Si la valeur de in props est vraie, cela signifie que l'élément passe de l'état d'entrée à l'état de sortie. Si la valeur de in props est false, cela signifie que l'élément passe de l'état exiting à l'état exited.

## Transition

Transition est le composant de base fourni par le groupe React Transition pour animer un élément. Créons une application simple et essayons de faire apparaître ou disparaître un élément en utilisant l'élément Transition.

Tout d'abord, créez une nouvelle application React, react-animation-app en utilisant le bundler Create React App ou Rollup en suivant les instructions du chapitre Créer une application React.

Ensuite, installez la bibliothèque React Transition Group.

```bash
cd /go/to/project 
npm install react-transition-group --save
```

Ensuite, ouvrez l'application dans votre éditeur préféré.

Ensuite, créez le dossier src sous le répertoire racine de l'application.

Ensuite, créez un dossier de composants sous le dossier src.

Ensuite, créez un fichier, HelloWorld.js, dans le dossier src/components et commencez à le modifier.

Ensuite, importez React et la bibliothèque d'animation.

```js
import React from 'react'; 
import { Transition } from 'react-transition-group'
```

Ensuite, créez le composant HelloWorld.

```js
class HelloWorld extends React.Component {
    constructor(props) {
        super(props);
    }
}
```

Ensuite, définissez les styles liés à la transition en tant qu'objets JavaScript dans le constructeur.

```js
this.duration = 2000;
this.defaultStyle = {
    transition: `opacity ${this.duration}ms ease-in-out`,
    opacity: 0,
}
this.transitionStyles = {
    entering: { opacity: 1 },
    entered: { opacity: 1 },
    exiting: { opacity: 0 },
    exited: { opacity: 0 },
};
```

Ici,

- defaultStyles définit l'animation de la transition
- transitionStyles définir les styles pour les différents états

Ensuite, définissez l'état initial de l'élément dans le constructeur.

```js
this.state = { 
    inProp: true 
}
```

Ensuite, simulez l'animation en modifiant les valeurs inProp toutes les 3 secondes.

```js
setInterval(() => {
    this.setState((state, props) => {
        let newState = {
            inProp: !state.inProp
        };
        return newState;
    })
}, 3000);
```

Ensuite, créez une fonction de rendu.

```js
render() { 
    return ( 
    ); 
}
```

Ensuite, ajoutez le composant Transition. Utilisez this.state.inProp pour l'élément in et this.duration pour l'élément timeout. Le composant Transition attend une fonction, qui renvoie l'interface utilisateur. Il s'agit essentiellement d'un props Render.

```js
render() {
    return (
        <Transition in={this.state.inProp} timeout={this.duration}>
            {state => ({
                ... component's user interface.
            })
        </Transition>
    );
}
```

Ensuite, écrivez l'interface utilisateur des composants à l'intérieur d'un conteneur et définissez les styles defaultStyle et transitionStyles pour le conteneur.

```js
render() {
    return (
        <Transition in={this.state.inProp} timeout={this.duration}>
            {state => (
                <div style={{
                ...this.defaultStyle,
                ...this.transitionStyles[state]
                }}>
                <h1>Hello World!</h1>
                </div>
            )}
        </Transition>
    );
}
```

Finally, expose the component.

```js
export default HelloWorld
```

Le code source complet du composant est le suivant -

```js
import React from "react";
import { Transition } from 'react-transition-group';

class HelloWorld extends React.Component {
    constructor(props) {
        super(props);
        this.duration = 2000;
        this.defaultStyle = {
            transition: `opacity ${this.duration}ms ease-in-out`,
            opacity: 0,
        }
        this.transitionStyles = {
            entering: { opacity: 1 },
            entered: { opacity: 1 },
            exiting: { opacity: 0 },
            exited: { opacity: 0 },
        };
        this.state = {
            inProp: true
        }
        setInterval(() => {
            this.setState((state, props) => {
                let newState = {
                inProp: !state.inProp
                };
                return newState;
            })
        }, 3000);
    }
    render() {
        return (
            <Transition in={this.state.inProp} timeout={this.duration}>
                {state => (
                <div style={{
                    ...this.defaultStyle,
                    ...this.transitionStyles[state]
                }}>
                    <h1>Hello World!</h1>
                </div>
                )}
            </Transition>
        );
    }
}
export default HelloWorld;
```

Ensuite, créez un fichier, index.js, dans le dossier src et utilisez le composant HelloWorld.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import HelloWorld from './components/HelloWorld';

ReactDOM.render(
    <React.StrictMode>  
        <HelloWorld />
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
        <title>React Containment App</title>
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

En cliquant sur le lien de suppression, l'article sera retiré de la boutique redux.

## CSSTransition

CSSTransition est construit au-dessus du composant Transition et il améliore le composant Transition en introduisant la prop classNames. La prop classNames fait référence au nom de la classe css utilisée pour les différents états de l'élément.

Par exemple, classNames=hello prop fait référence aux classes css ci-dessous.

```css
.hello-enter {
    opacity: 0;
}
.hello-enter-active {
    opacity: 1;
    transition: opacity 200ms;
}
.hello-exit {
    opacity: 1;
}
.hello-exit-active {
    opacity: 0;
    transition: opacity 200ms;
}
```

Créons un nouveau composant HelloWorldCSSTransition en utilisant le composant CSSTransition.

Tout d'abord, ouvrez notre application react-animation-app dans votre éditeur préféré.

Ensuite, créez un nouveau fichier, HelloWorldCSSTransition.css sous le dossier src/components et entrez les classes de transition.

```css
.hello-enter {
    opacity: 1;
    transition: opacity 2000ms ease-in-out;
}
.hello-enter-active {
    opacity: 1;
    transition: opacity 2000ms ease-in-out;
}
.hello-exit {
    opacity: 0;
    transition: opacity 2000ms ease-in-out;
}
.hello-exit-active {
    opacity: 0;
    transition: opacity 2000ms ease-in-out;
}
```

Ensuite, créez un nouveau fichier, HelloWorldCSSTransition.js dans le dossier src/components et commencez à le modifier.

Ensuite, importez React et la bibliothèque d'animation.

```js
import React from 'react'; 
import { CSSTransition } from 'react-transition-group'
```

Ensuite, importez HelloWorldCSSTransition.css.

```js
import './HelloWorldCSSTransition.css'
```

Ensuite, créez le composant HelloWorld.

```js
class HelloWorldCSSTransition extends React.Component {
    constructor(props) {
        super(props);
    }
}
```

Ensuite, définissez la durée de la transition dans le constructeur.

```js
this.duration = 2000;
```

Ensuite, définissez l'état initial de l'élément dans le constructeur.

```js
this.state = { 
    inProp: true 
}
```

Ensuite, simulez l'animation en modifiant les valeurs inProp toutes les 3 secondes.

```js
setInterval(() => {
    this.setState((state, props) => {
        let newState = {
            inProp: !state.inProp
        };
        return newState;
    })
}, 3000);
```

Ensuite, créez une fonction de rendu.


```js
render() { 
   return (
   ); 
}
```

Ensuite, ajoutez le composant CSSTransition. Utilisez this.state.inProp pour la propriété in, this.duration pour la propriété timeout et hello pour la propriété classNames. Le composant CSSTransition attend l'interface utilisateur comme propriété enfant.

```js
render() {
    return (
        <CSSTransition in={this.state.inProp} timeout={this.duration} 
            classNames="hello">
            // ... user interface code ...   
        </CSSTransition>
    );
}
```

Ensuite, écrivez l'interface utilisateur des composants.

```js
render() {
    return (
        <CSSTransition in={this.state.inProp} timeout={this.duration} 
        classNames="hello">
        <div>
            <h1>Hello World!</h1>
        </div>
        </CSSTransition>
    );
}
```

Enfin, exposez le composant.

```js
export default HelloWorldCSSTransition;
```

Le code source complet du composant est donné ci-dessous -

```js
import React from 'react';
import { CSSTransition } from 'react-transition-group'
import './HelloWorldCSSTransition.css' 

class HelloWorldCSSTransition extends React.Component {
    constructor(props) {
        super(props);
        this.duration = 2000;
        this.state = {
            inProp: true
        }
        setInterval(() => {
            this.setState((state, props) => {
                let newState = {
                inProp: !state.inProp
                };
                return newState;
            })
        }, 3000);
    }
    render() {
        return (
            <CSSTransition in={this.state.inProp} timeout={this.duration} 
                classNames="hello">
                <div>
                <h1>Hello World!</h1>
                </div>
            </CSSTransition>
        );
    }
}
export default HelloWorldCSSTransition;
```

Ensuite, créez un fichier, index.js, dans le dossier src et utilisez le composant HelloWorld.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import HelloWorldCSSTransition from './components/HelloWorldCSSTransition';

ReactDOM.render(
    <React.StrictMode>
        <HelloWorldCSSTransition />
    </React.StrictMode>,
    document.getElementById('root')
);
```

Ensuite, servez l'application en utilisant la commande npm.

```js
npm start
```

Ensuite, ouvrez le navigateur et entrez ```http://localhost:3000``` dans la barre d'adresse et appuyez sur la touche Entrée.

Le message s'affiche et disparaît toutes les 3 secondes.

## TransitionGroup

TransitionGroup est un composant conteneur, qui gère plusieurs composants de transition dans une liste. Par exemple, alors que chaque élément d'une liste utilise CSSTransition, TransitionGroup peut être utilisé pour regrouper tous les éléments afin de les animer correctement.

```js
<TransitionGroup>
    {items.map(({ id, text }) => (
        <CSSTransition key={id} timeout={500} classNames="item" >
            <Button
                onClick={() =>
                setItems(items =>
                    items.filter(item => item.id !== id)
                )
                }
                >
                &times;
            </Button>
            {text}
        </CSSTransition>
    ))}
</TransitionGroup>
```