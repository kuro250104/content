## Introduction

La bibliothèque React est construite sur des bases solides. Elle est simple, flexible et extensible. Comme nous l'avons appris précédemment, React est une bibliothèque permettant de créer une interface utilisateur dans une application web. L'objectif principal de React est de permettre au développeur de créer une interface utilisateur en utilisant du JavaScript pur. Normalement, chaque bibliothèque d'interface utilisateur introduit un nouveau langage de modèle (que nous devons apprendre) pour concevoir l'interface utilisateur et offre une option pour écrire la logique, soit dans le modèle, soit séparément.

Au lieu d'introduire un nouveau langage de gabarits, React introduit trois concepts simples, comme indiqué ci-dessous.

### React elements

Représentation JavaScript du DOM HTML. React fournit une API, React.createElement pour créer un élément React.

### JSX

Une extension JavaScript pour concevoir l'interface utilisateur. JSX est un langage extensible basé sur XML, qui supporte la syntaxe HTML avec peu de modifications. JSX peut être compilé en éléments React et utilisé pour créer une interface utilisateur.

### React component

Le composant React est le principal élément constitutif de l'application React. Il utilise des éléments React et JSX pour concevoir son interface utilisateur. Le composant React est essentiellement une classe JavaScript (qui étend la classe React.component) ou une fonction JavaScript pure. Le composant React possède des propriétés, une gestion d'état, un cycle de vie et un gestionnaire d'événements. Un composant React peut être capable d'effectuer une logique simple ou avancée.

Apprenons-en plus sur les composants dans le chapitre React Component.

## Workflow d'une application React

Comprenons le flux de travail d'une application React dans ce chapitre en créant et en analysant une application React simple.

Ouvrez une invite de commande et allez dans votre espace de travail.

```bash
cd /go/to/your/workspace
```

Ensuite, créez un dossier, static_site et changez de répertoire pour le dossier nouvellement créé.

```bash
mkdir static_site 
cd static_site
```

### Exemple

Ensuite, créez un fichier, hello.html et écrivez une application React simple.

```html
<!DOCTYPE html> 
<html> 
    <head> 
        <meta charset="UTF-8" /> 
        <title>React Application</title> 
    </head> 
    <body> 
        <div id="react-app"></div> 

        <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script> 
        <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script> 
        <script language="JavaScript"> 
            element = React.createElement('h1', {}, 'Hello React!') 
            ReactDOM.render(element, document.getElementById('react-app')); 
        </script> 
    </body>
</html>
```

Ensuite, servez l'application à l'aide du serveur web serve.

```bash
serve ./hello.html
```

Analysons le code et faisons quelques modifications pour mieux comprendre l'application React.

Ici, nous utilisons deux API fournies par la bibliothèque React.

#### React.createElement

Utilisé pour créer des éléments React. Il attend trois paramètres :

- Balise élémentaire ;
- Attributs de l'élément en tant qu'objet ;
- Element content - Il peut également contenir des éléments React imbriqués.

#### ReactDOM.render

Utilisé pour rendre l'élément dans le conteneur. Il attend deux paramètres :

- Élément React OU JSX ;
- Élément racine de la page web.

## Élément React imbriqué

Comme ```React.createElement``` permet l'imbrication d'éléments React, ajoutons un élément imbriqué comme indiqué ci-dessous.

### Exemple

```js
<script language="JavaScript">
    element = React.createElement('div', {}, React.createElement('h1', {}, 'Hello React!'));
    ReactDOM.render(element, document.getElementById('react-app')); 
</script>
```

### Sortie

Il générera le contenu ci-dessous :

```html
<div><h1> Hello React!</h1></div> 
```

## Utilisation de JSX

Ensuite, supprimons entièrement l'élément React et introduisons la syntaxe JSX comme indiqué ci-dessous :

```html
<!DOCTYPE html> 
<html> 
    <head> 
        <meta charset="UTF-8" /> 
        <title>React Application</title> 
    </head> 
    <body> 
        <div id="react-app"></div> 
        <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script> 
        <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script> 
        <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script> 
        <script type="text/babel"> 
            ReactDOM.render(
                <div><h1>Hello React!</h1></div>, 
                document.getElementById('react-app') 
            ); 
        </script> 
    </body>
</html>
```

Ici, nous avons inclus babel pour convertir JSX en JavaScript et ajouté type="text/babel" dans la balise script.

```html
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script> 
<script type="text/babel"> 
    ... 
    ... 
</script>
```

Ensuite, créons un nouveau composant React, Greeting, puis essayons de l'utiliser dans la page Web.

```html
<script type="text/babel"> 
    function Greeting() {
        return <div><h1>Hello JSX!</h1></div> 
    } 
    ReactDOM.render(<Greeting />, document.getElementById('react-app') ); 
</script>
```

L'application React appelle la méthode ```ReactDOM.render``` en passant l'interface utilisateur créée à l'aide du composant React (codé au format JSX ou élément React) et le conteneur pour rendre l'interface utilisateur.

```ReactDOM.render``` traite l'élément JSX ou React et émet le DOM virtuel.

Le DOM virtuel sera fusionné et rendu dans le conteneur.

## Architecture of the React Application

La bibliothèque React n'est qu'une bibliothèque d'interface utilisateur et n'impose aucun modèle particulier pour écrire une application complexe. Les développeurs sont libres de choisir le design pattern de leur choix. La communauté React préconise certains modèles de conception. L'un de ces modèles est le modèle Flux. La bibliothèque React fournit également de nombreux concepts comme Higher Order component, Context, Render props, Refs etc. pour écrire un meilleur code. React Hooks est un concept évolutif qui permet de gérer l'état des projets de grande envergure.

- Une application React commence avec un seul composant racine.
- Le composant racine est construit en utilisant un ou plusieurs composants.
- Chaque composant peut être imbriqué avec d'autres composants à n'importe quel niveau.
- La composition est l'un des concepts fondamentaux de la bibliothèque React. Ainsi, chaque composant est construit en composant des composants plus petits au lieu d'hériter d'un composant d'un autre composant.
- La plupart des composants sont des composants d'interface utilisateur.
- L'application React peut inclure des composants tiers à des fins spécifiques telles que le routage, l'animation, la gestion des états, etc.
