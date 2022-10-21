Comme pour beaucoup de langages de programmation, les variables JavaScript ont des règles de portée. 

En informatique, une portée désigne la “visibilité” d’une variable.

## La portée dans les blocs

Avant 2015, le JavaScript n’avait pas la portée “bloc”, juste la portée globale et la portée dans les fonctions. 

Depuis 2015, le langage met à disposition 2 nouveaux types de variables : ```const``` et ```let```.

Ces deux mot-clés permettent au JavaScript d’avoir une portée dans les blocs. Cela signifie que les variables déclarées avec let et const dans les blocs, ne peuvent pas être utilisées à l’extérieur du bloc au sein duquel elles ont été déclarées. 

Exemple : 

```js
{
    let x = 2; // x est utilisable seulement au sein de ce bloc
}
// x n'est pas utilisable ici
```

En revanche, le mot-clé var ne souffre pas de la portée dans les blocs. En d’autres termes, une variable déclarée avec var peut-être utilisée à l’extérieur dudit bloc.

Exemple :

```js
{
    var x = 2; // x est utilisable ici
}
// x est également utilisable ici
```

## La portée locale

Les variables déclarées dans les fonctions JavaScript ne peuvent pas être réutilisées à l'extérieur de la fonction. Les variables ayant une portée **locale** se voit également appliquer une portée **fonction** ne leur permettant pas d’être utilisées à nouveau ailleurs dans le code.

Exemple :

```js
// Ici, la variable carName n'est pas utilisable

function myFunction() {
  let carName = "Volvo";
  // Ici, le code peut utilisercarName
}

// Ici, le code ne peut pas utiliser carName
```

Puisque les variables locales sont, comme leur nom l’indique, seulement reconnues localement au sein d’une fonction, le même nom de variable peut être réutilisé dans plusieurs fonctions différentes. 

En fait, avec une fonction, la variable est créée au début de la fonction et effacée à la fin.

## La portée fonction

Avec cette portée, chaque fonction crée une nouvelle portée. Cela signifie qu’une variable créée au sein d’une fonction n’est pas visible à l’extérieur de celle-ci. Cette règle s’applique même pour les variables créées avec le mot-clé ```var```.

Exemple :

```js
function myFunction() {
    var carName = "Volvo"; // Portée fonction, la variable n'est visible qu'au sein de cette fonction.
}
```

## Variables globales

Un variable déclarée hors d’une fonction est dite **globale**. Cela veut dire que l’ensemble du programme, fonctions y compris, peuvent y accéder.

De plus, les variables déclarées avec ```var```, ```let``` et ```const``` sont similaires lorsqu’elles sont déclarées en dehors d’une fonction.

### Les variables

Les objets et fonctions, en Javascript, sont aussi des variables. La portée permet de définir lors visibilité et leur utilisation au sein d’un programme. 

### Portée globale automatique

Lorsqu’une valeur est assignée à une variable qui n’a pas été préalablement déclarée, cette variable est considérée par Javascript comme globale - quand bien même elle se trouve au sein d’une fonction.

Exemple :

```js
myFunction();
// Ici, le code peut aussi utiliser carName

function myFunction() {
    carName = "Volvo";
}
```

### Mode strict

La plupart des navigateurs modernes permettent d’exécuter le JavaScript en mode strict. Lorsque ce mode est activé, les variables ayant reçu une valeur sans avoir été préalablement déclarées ne sont plus considérées comme globales.

### Variables globales en HTML

En JavaScript, la portée globale concerne l’environnement JavaScript. En revanche, en HTML, la portée globale concerne l’objet ```window```. 

Les variables globales déclarées avec le mot-clé var appartiennent à l’objet ```window```.

Exemple :

```js
var carName = "Volvo";
// Ici, window.carName est utilisable
```

À contrario, les variables déclarées avec ```let``` n’appartiennent pas à l’objet window.

Exemple :

```js
let carName = "Volvo";
// Ici, window.carName n'est pas utilisable
```

### Avertissement

Il ne faut créer des variables globales que s’il y en a réellement besoin. En effet, les variables ou fonctions globales peuvent écraser les variables ou fonctions ```window```, et n’importe quelle fonction, incluant les objets ```window``` peuvent écraser les variables et fonctions globales.

## Durée de vie d’une variable

La durée de vie d’une variable, en JavaScript, commence lorsque ladite variable est déclarée. 

Les variables locales - au sein des fonctions - sont effacées lorsque la fonction est terminée. 

Concernant les variables globales, celles-ci sont effacées lorsque la fenêtre ou l’onglet du navigateur est fermé.

## Arguments des fonctions

Les arguments - ou paramètres - d’une fonction fonctionnent comme des variables locales au sein de la fonction. 