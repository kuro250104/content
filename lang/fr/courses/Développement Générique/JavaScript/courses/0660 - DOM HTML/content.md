L’un des avantages du DOM, en JavaScript, est qu’il permet de modifier des éléments HTML.

## Changer le contenu HTML

Le moyen le plus simple de modifier le contenu HTML d’un élément est d’utiliser la propriété ```element.innerHTML```.

Cette propriété permet d’ajouter des balises HTML dans le contenu à modifier.

Voici la syntaxe à utiliser avec cette propriété :

```js
element.innerHTML = "Nouveau contenu"
```

Exemple :

```js
<html>
<body>

<p id="p1">Hello World!</p>

<script>
    document.getElementById("p1").innerHTML = "New text!";
</script>

</body>
</html>
```

Dans cet exemple, le contenu du paragraphe ayant l’id ```p1``` est modifié. Le texte “**New Text**” remplace “**Hello World !**”.

## Changer la valeur d’un attribut

Pour changer la valeur d’un attribut, la syntaxe suivante est utilisée :

```js
document.getElementById(id).attribute = nouvelle valeur
```

Exemple :

```js
<!DOCTYPE html>
<html>
<body>

<img id="myImage" src="smiley.gif">

<script>
    document.getElementById("myImage").src = "landscape.jpg";
</script>

</body>
</html>
```

Dans cet exemple, c’est l’attribut ```src``` de l’image qui est modifié. 

## La méthode document.write()

Cette méthode est utilisée pour écrire directement dans le flux html d’un document. Attention cependant, utiliser cette méthode pour écrire dans un document HTML **supprime tout le contenu HTML du document**.

Exemple :

```js
<!DOCTYPE html>
<html>
<body>

<p>Bla bla bla</p>

<script>
    document.write(Date());
</script>

<p>Bla bla bla</p>

</body>
</html>
```