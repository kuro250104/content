Le DOM HTML est accessible avec JavaScript et d’autres langages de programmation. Dans le DOM, tous les éléments HTML sont définis comme des objets.

Lorsque le DOM est utilisé, une **propriété** est une valeur qui peut être obtenue ou modifiée - par exemple, changer le contenu d’un élément HTML.

Une **méthode** est une action qui peut être faite - comme ajouter ou effacer des éléments HTML.

## La méthode getElementById

La manière la plus commune pour accéder à un élément HTML est d’utiliser l’attribut **id** de cet élément.

Exemple :

```js
<html>
<body>

<p id="demo"></p>

<script>
    document.getElementById("demo").innerHTML = "Hello World!";
</script>

</body>
</html>
```

Dans cet exemple, l’élément portant l’**id** ```demo``` est sélectionné.

__Remarque__ : le JavaScript à par la suite inclu une nouvelle méthode qui à trouvé sa place et largement remplacer ```getElementById```: ```querySelector```.

## La propriété innerHTML

Le meilleur moyen d’obtenir le contenu d’un élément HTML est d’utiliser la propriété ```innerHTML```.

Cette propriété est utile pour obtenir ou modifier le contenu d’un élément HTML.

__Remarque__ : La propriété ```innerHTML``` peut être utilisée pour obtenir ou modifier le contenu de n’importe quel élément HTML, incluant ```<body>``` et ```<html>```.