## Introduction

Comme nous l'avons appris précédemment, React JSX est une extension de JavaScript. Elle permet au développeur de créer un DOM virtuel en utilisant la syntaxe XML. Il se compile en pur JavaScript (appels de fonction React.createElement). Puisqu'il se compile en JavaScript, il peut être utilisé dans n'importe quel code JavaScript valide. Par exemple, les codes ci-dessous sont parfaitement valides.

- Affecter à une variable.

```js
var greeting = <h1>Hello React!</h1>
```

- Affecter à une variable en fonction d'une condition.

```js
var canGreet = true; 
if(canGreet) { 
    greeting = <h1>Hello React!</h1> 
}
```

- Peut être utilisé comme valeur de retour d'une fonction.

```js
function Greeting() { 
    return <h1>Hello React!</h1>
} 
greeting = Greeting()
```

- Peut être utilisé comme argument d'une fonction.

```js
function Greet(message) { 
    ReactDOM.render(message, document.getElementById('react-app') 
} 
Greet(<h1>Hello React!</h1>)
```

## Expressions

JSX prend en charge les expressions en syntaxe JavaScript pure. L'expression doit être encadrée par des accolades, { }. L'expression peut contenir toutes les variables disponibles dans le contexte, où le JSX est défini. Créons un JSX simple avec une expression.

### Exemple

```html
<script type="text/babel">
    var cTime = new Date().toTimeString();
    ReactDOM.render(
        <div><p>The current time is {cTime}</p></div>, 
        document.getElementById('react-app')
    );
</script>
```

### Sortie

Ici, **cTime** est utilisé dans l'expression JSX using. Le résultat du code ci-dessus est le suivant,

```bash
The Current time is 21:19:56 GMT+0530(India Standard Time)
```

L'un des effets secondaires positifs de l'utilisation de l'expression en JSX est qu'elle empêche les attaques par injection, car elle convertit n'importe quelle chaîne en chaîne sûre pour le html.

## Fonctions

JSX prend en charge les fonctions JavaScript définies par l'utilisateur. L'utilisation des fonctions est similaire à celle des expressions. Créons une fonction simple et utilisons-la dans JSX.

### Exemple

```html
<script type="text/babel">
    var cTime = new Date().toTimeString();
    ReactDOM.render(
        <div><p>The current time is {cTime}</p></div>, 
        document.getElementById('react-app') 
    );
</script>
```

### Sortie

Ici, ```getCurrentTime()``` est utilisé pour obtenir l'heure actuelle et le résultat est similaire à celui spécifié ci-dessous.

```bash
The Current time is 21:19:56 GMT+0530(India Standard Time)
```

## Attributs

JSX prend en charge les attributs de type HTML. Toutes les balises HTML et leurs attributs sont supportés. Les attributs doivent être spécifiés en utilisant la convention camelCase (qui suit l'API DOM de JavaScript) au lieu du nom d'attribut HTML normal. Par exemple, l'attribut class en HTML doit être défini comme className. Voici quelques autres exemples

- **htmlFor** au lieu de **for**
- **tabIndex** au lieu de **tabindex**
- **onClick** au lieu de **onclick**

### Exemple

```html
<style>
    .red { color: red }
</style>
<script type="text/babel">
    function getCurrentTime() {
        return new Date().toTimeString();
    }
    ReactDOM.render(
        <div>
            <p>The current time is <span className="red">{getCurrentTime()}</span></p>
        </div>,
        document.getElementById('react-app') 
    );
</script>
```

### Sortie

Le résultat est le suivant :

```bash
The Current time is 22:36:55 GMT+0530(India Standard Time)
```

## Expression dans les attributs

JSX permet de spécifier des expressions à l'intérieur des attributs. Dans les attributs, les guillemets doubles ne doivent pas être utilisés avec l'expression. Il faut utiliser soit une expression, soit une chaîne de caractères avec des guillemets doubles. L'exemple ci-dessus peut être modifié pour utiliser l'expression dans les attributs.

```html
<style>
    .red { color: red }
</style>

<script type="text/babel">
    function getCurrentTime() {
        return new Date().toTimeString();
    }
    var class_name = "red";
    ReactDOM.render(
        <div>
            <p>The current time is <span className={class_name}>{getCurrentTime()}</span></p>
        </div>, 
        document.getElementById('react-app') 
    );
</script>
```
