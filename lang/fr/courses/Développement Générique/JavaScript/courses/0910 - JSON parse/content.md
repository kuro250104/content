Une utilisation commune du JSON est pour échanger des données vers où depuis un serveur. Lorsque ces données sont reçues depuis le serveur, elles sont toujours sous forme de chaîne de caractères. 

Par conséquent, en utilisant une fonction intégrée en JavaScript, cela permet de transformer cette chaîne de caractères en objet.

## Exemple de parsage

Le fichier JSON suivant a été reçu depuis le serveur :

```json
'{"name":"John", "age":30, "city":"New York"}'
```

Ce fichier peut être converti en objet JavaScript, grâce à la fonction ```JSON.parse()```.

Exemple :

```js
const obj = JSON.parse('{"name":"John", "age":30, "city":"New York"}');
```

__Remarque__ : Si le fichier parsé n’est pas au format JSON, une ```syntaxError``` sera retournée.

Ensuite, il est possible d’utiliser les données du JSON comme un objet JavaScript.

Exemple :

```js
<p id="demo"></p>

<script>
    document.getElementById("demo").innerHTML = obj.name;
</script>
```

## Arrays en tant que JSON

Lorsque ```JSON.parse()``` est utilisée avec des arrays JSON, la méthode retourne un array JavaScript plutôt qu’un objet. 

Exemple :

```js
const text = '["Ford", "BMW", "Audi", "Fiat"]';
const myArr = JSON.parse(text);
```

## Exceptions

### Parser des dates

Les objets de type date ne sont pas autorisés en JSON. Si une date doit être utilisée dans un fichier JSON, il est recommandé de la mettre sous forme de chaîne de caractères. Par la suite, il sera possible de la re-convertir en objet. 

Exemple :

```js
const text = '{"name":"John", "birth":"1986-12-14", "city":"New York"}';
const obj = JSON.parse(text);
obj.birth = new Date(obj.birth);

document.getElementById("demo").innerHTML = obj.name + ", " + obj.birth;
```

Dans cet exemple, la clé ```birth```, une fois récupérée du fichier parsé, est convertie au format date. 

Une autre solution envisageable est d’utiliser le second paramètre de la fonction ```JSON.parse()``` : *surviver*. Ce paramètre est une fonction qui vérifie chaque propriété avant de retourner leurs valeurs.

Exemple :

```js
const text = '{"name":"John", "birth":"1986-12-14", "city":"New York"}';
const obj = JSON.parse(text, function (key, value) {
    if (key == "birth") {
        return new Date(value);
    } else {
        return value;
    }
});

document.getElementById("demo").innerHTML = obj.name + ", " + obj.birth;
```

Dans cet exemple, en plus du nom du fichier à parser, la fonction ```JSON.parse()``` prend également en paramètre une fonction anonyme permettant de vérifier si la clé vaut ```birth```. Si tel est le cas, la valeur est convertie en objet date. Sinon, la valeur est simplement retournée. 

### Parser des fonctions

Les fonctions ne sont pas autorisées en JSON. Si, malgré tout, une fonction doit être utilisée en JSON, il faut l’écrire sous forme de chaîne de caractères. Plus tard, il sera possible de la convertir à nouveau comme une fonction.

Exemple :

```js
const text = '{"name":"John", "age":"function () {return 30;}", "city":"New York"}';
const obj = JSON.parse(text);
obj.age = eval("(" + obj.age + ")");

document.getElementById("demo").innerHTML = obj.name + ", " + obj.age();
```

__Remarque__ : Bien que l’exemple ci-dessus fonctionne parfaitement, il est malgré tout recommandé d’éviter d’utiliser des fonctions en JSON. En effet, ces dernières perdent leur portée et la fonction ```eval()``` doit être utilisée pour la reconvertir en fonction JavaScript.