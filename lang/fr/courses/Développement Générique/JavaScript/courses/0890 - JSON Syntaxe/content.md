Le JSON est un sous-ensemble de l’écriture JavaScript.

## Règles de syntaxe en JSON

JSON est dérivé de la notation objet de JavaScript :

- Les données sont en paire clé/valeurs.
- Les données sont séparées par des virgules,
- Des accolades entourent l’objet.
- Des crochets entourent les arrays

## Données JSON - Une clé et une valeur

JSON est écrit en paire clé/valeur. Cette notation consiste en un nom de champ (le nom de la donnée qui va être saisie) entre doubles guillemets, suivi de deux points, suivi de la valeur. 

Exemple :

```js
"name":"John"
```

__Remarque__ : Le JSON utilise seulement les doubles guillemets.

## JSON comparé aux objets JavaScript

Le format JSON est quasiment identique aux objets JavaScript.

En JSON, les clés doivent être écrites entre doubles guillemets :

```json
{"name":"John"}
```

Tandis qu’en JavaScript, les clés peuvent être de n’importe quel type (string, number, etc.) :

```js
{name:"John"}
```

## Les valeurs en JSON

En JSON, les valeurs doivent être d’un des types suivants :

- ```string```
- ```number```
- ```objet```
- ```array```
- ```booléen```
- ```null```

En JavaScript, les valeurs peuvent être des types ci-dessus, en ajoutant :

- ```fonction```
- ```date```
- ```undefined```

De plus, en JSON, les valeurs peuvent seulement être écrites entre doubles guillemets - alors que le JavaScript autorise également les guillemets simples.

Exemple :

```json
{"name":"John"}
```

## Les arrays JavaScript en JSON

De la même manière que les objets JavaScript peuvent être écrits en JSON, il en va de même pour les arrays JavaScript. 

## Les fichiers JSON

L’extension d’un fichier JSON est : ```.json```.