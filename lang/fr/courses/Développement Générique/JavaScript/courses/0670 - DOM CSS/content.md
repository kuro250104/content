Le DOM permet également de modifier le style des éléments HTML.

## Modifier le style

Voici, ci-dessous, la syntaxe à utiliser pour modifier le style d’un élément HTML :

```js
document.getElementById(id).style.property = new style
```

Exemple :

```js
<html>
<body>

<p id="p2">Hello World!</p>

<script>
    document.getElementById("p2").style.color = "blue";
</script>

</body>
</html>
```

Dans cet exemple, le style du paragraphe ```p2``` est modifié. Désormais, il est de couleur bleue.

## Utiliser les évènements

Le DOM permet d’exécuter seulement lorsqu’un événement se produit - comme le clique de l’utilisateur sur un lien, par exemple.

Exemple :

```js
<!DOCTYPE html>
<html>
<body>

<h1 id="id1">My Heading 1</h1>

<button type="button"
onclick="document.getElementById('id1').style.color = 'red'">
Click Me!</button>

</body>
</html>
```

Dans cet exemple, lorsque l’utilisateur clique sur le bouton, la couleur de la police change en rouge. 