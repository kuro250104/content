Le langage HTML donne la possibilité au développeur de donner des noms à des éléments. Cela permet notamment, plus tard, lors de la phase de design, de pouvoir styliser les éléments portant un nom particulier.

## Attribut class

L’attribut ```class``` est un des deux attributs permettant de donner un nom à un élément. Il permet, en fait, de pouvoir donner **le même nom à plusieurs éléments**.

__Remarque__ : L’attribut ```class``` peut être utilisé avec n’importe quel élément HTML. De plus, des éléments de type différents peuvent avoir un même nom de classe. Par exemple, un élément ```<p>``` peut avoir une classe main, aussi bien qu’un élément ```<div>```.

Exemple :

``` html
<body>
    <!-- Applique la classe background sur la div -->
    <div class="background">
        <p>Je suis le paragraphe 1</p>
    </div>
 
    <!-- Applique la classe background sur la div -->
    <div class="background">
        <p>Je suis le paragraphe 2</p>
    </div>
</body>
```

Dans cet exemple, les deux ```<div>``` se sont vues attribuer la même classe, **background**, grâce à l’attribut ```class```.

## Classes multiples

Le langage HTML permet de donner plusieurs noms de classe à un même élément. Pour ce faire, il suffit simplement de mettre un espace entre les deux noms, dans l’attribut ```class``` :

``` html
<body>
    <!-- La div ci-dessous appartient à la fois à la classe background et à la class main -->
    <div class="background main">
        <p>Je suis le paragraphe 1</p>
    </div>
</body>
```