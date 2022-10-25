Bien que JSON soit similaire au JavaScript, ce format n’accepte qu’un nombre restreint de type de données.

## Types de données valides

En JSON, les valeurs doivent être l’un des types suivants :

- ```string```
- ```number```
- ```objet (objet JSON)```
- ```array```
- ```booléen```
- ```null```

En revanche, JSON n’accepte **PAS** les types de valeurs suivants :

- ```fonction```
- ```date```
- ```undefined```

### Chaînes de caractères en JSON

Avec le format JSON, les chaînes de caractères doivent être écrites entre doubles guillemets.

Exemple :

```js
{"name":"John"}
```

### Nombres en JSON

En JSON, les nombres doivent être entiers ou décimaux. Comme en JavaScript, les nombres ne sont pas écrits entre guillemets.

Exemple :

```js
{"age":30}
```

### Objets JSON

Les valeurs, en JSON, peuvent également être des objets. 

Exemple :

```json
{
"employee":{"name":"John", "age":30, "city":"New York"}
}
```

__Remarque__ : Les objets en tant que valeurs, en JSON, doivent respecter la syntaxe JSON.

## Arrays en JSON

Les valeurs JSON peuvent aussi être des ```arrays```.

Exemple :

```json
{
"employees":["John", "Anna", "Peter"]
}
```

### Booléens en JSON

En JSON, les valeurs peuvent également être vraies ou fausses. Pour cela, le type ```booléen``` est utilisé.

Exemple :

```json
{"sale":true}
```

### Null en JSON

De même, les valeurs peuvent être de type ```null```.

Exemple :

```json
{"middlename":null}
```