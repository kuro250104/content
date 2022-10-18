En informatique, est appelée chaîne de caractères une séquence de caractères. En d’autres termes, il s’agit d’un mot ou d’un texte. Une chaîne de caractères est un type de données et est plus communément appelée par sa traduction anglaise, *string*. 

Une chaîne de caractères peut aussi ne rien contenir. Il s’agira, auquel cas, d’une chaîne vide. 

## Qu’est-ce qu’une chaîne de caractères ?

- Séquence de caractères (du texte)
- Traduit en anglais par “string”
- Est un type de données
- Peut contenir aucun caractère, c’est ce qu’on appelle une chaîne vide.

## Les chaînes de caractères dans du code PHP

Comme pour le langage JavaScript, les guillemets simples et doubles sont utilisables en PHP pour entourer une chaîne de caractères. 

Le langage PHP fait la différence entre ces deux types de guillemets.

### Les guillemets simples 

Les guillemets simples (‘’) sont utilisables en PHP. C’est d’ailleurs le type de guillemets le plus communément utilisé pour entourer une chaîne de caractères. 

Exemple :

``` php
'Ceci est une chaîne de caractères'
```

Lorsqu’une apostrophe doit être utilisée au sein d’une chaîne entourée de guillemets simples, il est nécessaire d’échapper l’apostrophe avec un antislash, afin que le navigateur ne confonde pas l’apostrophe avec un guillemet de fin de chaîne.

Exemple :

``` php
'J\'utilise une chaîne de caractères’
```

Cet exemple retourne bien la phrase : **J’utilise une chaîne de caractères**.

De même, si un antislash doit être utilisé comme caractère au sein d’une string, il doit également être échappé avec un antislash.

Exemple :

``` php
'Les fichiers se trouvent sur le disque C:\\'
```

Cet exemple donne le résultat suivant : **‘Les fichiers se trouvent sur le disque C:\’**

### Les guillemets doubles

Les guillemets doublent peuvent également être utilisés pour entourer une chaîne de caractères. L’avantage est que s’il y a besoin d’utiliser des caractères spéciaux tels qu’une apostrophe, il n’y aura pas besoin de l’échapper.

Exemple :

``` php
"J'utilise une chaîne de caractères"
```

L’utilisation des guillemets double rend moins compliqué l’affichage du contenu d’un variable. En effet, il n’y a pas besoin d’utiliser la concaténation. 

Exemple :

``` php
$var = "test";
"Ceci est un ${var}.";
```

L’exemple ci-dessus retourne bien la phrase **Ceci est un test**. Le contenu de la variable ```$var``` a donc été affiché correctement. 

Ce type de guillemets, comme évoqué dans l’introduction de ce point, rend aussi possible l’interprétation des caractères spéciaux tels que le ```\n```.

Exemple :

``` php
"Ceci est une\nchaîne de caractères"
```

Voici ce que retourne cet exemple :

```
Ceci est une
chaîne de caractères
```

### Concaténation

Qu’il s’agisse de guillemets simples ou doubles, le langage PHP permet la concaténation des strings. Cela est par exemple utile pour l’affichage du contenu d’une variable.

Exemple :

``` php
$var = "test";
"Ceci est un deuxième " . $test
```

Cet exemple retourne bien la phrase “**Ceci est un deuxième test**”.
