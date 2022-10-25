Comme mentionné à plusieurs reprises, le JSON est basé sur la notation objet de JavaScript. Par conséquent, cela demande de respecter certaines règles, notamment sur la syntaxe. 

## Les expressions objets JSON

L’expression ci-dessous, écrite en JSON, est une chaîne de caractères :

```json
'{"name":"John", "age":30, "car":null}'
```

Dans cette chaîne de caractères, il y a une expression JSON objet :

```json
{"name":"John", "age":30, "car":null}
```

En JSON, les expressions objet sont entourées des accolades ouvrante et fermante et contiennent des paires clé/valeur. La clé est toujours entourée de guillemets doubles. La clé et la valeur sont séparés par les deux points. Les valeurs doivent toujours être d’un des types suivants :

- chaîne de caractères
- nombre
- objet
- array
- booléen
- null

De plus, chaque paire clé/valeur est séparée par une virgule. 

Il est important de comprendre que les données en JSON ne sont pas des objets ; ce sont des chaînes de caractères. Celles-ci deviennent des objets seulement lorsqu’elles sont converties grâce aux différentes méthodes JavaScript.

## Les objets JavaScript

En parsant une chaîne de caractères JSON, grâce à une méthode intégrée à JavaScript, il est possible de convertir cette string en objet JavaScript. Pour ce faire, c’est la méthode ```JSON.parse()``` qui est utilisée.

Exemple :

```js
myJSON = '{"name":"John", "age":30, "car":null}';
myObj = JSON.Parse(myJSON);
```

Dans cet exemple, ```myJSON``` est converti en objet JavaScript grâce à ```JSON.parse()```.

## Accéder aux valeurs des objets

Une fois la chaîne de caractères JSON parsée et transformée en objet JavaScript, il est possible d’accéder à la valeur de l’objet en utilisant la notation pointée. 

Exemple :

```js
const myJSON = '{"name":"John", "age":30, "car":null}';
const myObj = JSON.parse(myJSON);
x = myObj.name;
```

Ici, grâce à la notation pointée (```myObj.name```), la variable ```x``` contient désormais la valeur de la propriété name.

Il est également possible d’accéder aux valeurs en utilisant les crochets. 

Exemple :

```js
const myJSON = '{"name":"John", "age":30, "car":null}';
const myObj = JSON.parse(myJSON);
x = myObj["name"];
```

## Boucler sur un objet

Une fois l’objet JavaScript créé depuis le fichier JSON, il est possible de boucler sur les propriétés de cet objet grâce à une boucle ```for in```.

Exemple :

```js
const myJSON = '{"name":"John", "age":30, "car":null}';
const myObj = JSON.parse(myJSON);

let text = "";
for (let x in myObj) {
    text += x + ", ";
}
```

De plus, en utilisant les crochets avec une boucle ```for in```, il est possible d’accéder à la valeur des propriétés.

Exemple :

```js
const myJSON = '{"name":"John", "age":30, "car":null}';
const myObj = JSON.parse(myJSON);

let text = "";
for (let x in myObj) {
    text = += myObj[x] + ", ";
}
```