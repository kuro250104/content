JSON signifie **J**ava**S**cript **O**bject **N**otation. C’est un format très léger permettant d’échanger des données. Il s’agit de texte écrit en format Objet JavaScript. 

Le JSON, bien qu’inspiré de la notation objet JavaScript, est un langage indépendant. Il existe d’ailleurs dans beaucoup de langages de programmations, des outils permettant de lire ses données. 

## Exemple de JSON

Ci-dessous un exemple expliqué de chaîne de caractères JSON :

```json
'{"name":"John", "age":30, "car":null}'
```

Cet exemple définit un objet contenant 3 propriétés : ```name```, ```age``` et ```car```, et chacune de ces propriétés à une valeur. 

Par la suite, si ce code est parsé grâce à un programme JavaScript, il est possible d’accéder à chacune des propriétés comme s’il s’agissait d’un objet.

Exemple :

```js
let personName = obj.name;
let personAge = obj.age;
```

## Pourquoi utiliser JSON ?

Le format JSON est, de manière synthétique, similaire à la notation Objet en JavaScript. Grâce à cela, un programme JavaScript peut facilement convertir des données JSON est objet JavaScript. 

Puisqu’il s’agit d’un format texte, les données peuvent être envoyées d’un ordinateur à un autre et être interprétées par différents langages de programmation.

JavaScript a une fonction intégrée permettant de convertir un JSON en objet. Il s’agit de la fonction ```JSON.parse()```.

Il existe également une fonction JavaScript qui permet de convertir un objet en JSON : la fonction ```JSON.stringify()```.

## Stocker des données 

Lorsque des données sont stockées, celles-ci doivent être dans un certain format. Le format texte reste un format autorisé. 

JSON rend possible le fait de stocker des objets JavaScript en format texte.