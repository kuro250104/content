L’attribut ```id``` est le deuxième attribut permettant de donner un nom à un élément HTML. ```Id``` est le raccourci anglais pour “identifiant”. Sa différence avec l’attribut ```class```, est qu’il n’y a qu’**un seul élément par page** qui peut porter un nom particulier d’```id```, contrairement à ```class``` qui permet à plusieurs éléments de porter le même nom.

## Attribut id

L’attribut ```id``` permet de définir un nom (identifiant) unique pour un élément HTML. Il n’autorise pas d’autres éléments à porter le même nom au sein d’une même page web.

L’```id``` est principalement utilisé pour les liens d’ancres, et, plus tard, lors de la phase de design, pour pouvoir styliser l’élément portant l’identifiant défini. Il est également couramment utilisé pour fonctionner avec JavaScript.

__Remarque__ : Contrairement à ```class```, un élément HTML ne peut pas porter plusieurs noms d’id. L’attribut ```id``` doit recevoir au minimum 1 caractère et n’autorise pas les espaces, tabulations, etc.

Exemple :

```html
<body>
    <!-- Le paragraphe ci-dessous sera le seul à avoir l'identifiant "important"  -->
    <p id="important">Je suis un paragraphe avec un l'id important</p>
</body>
```

Il est bon de savoir que la valeur de l’attribut est sensible à la casse. Aussi, il ne peut contenir au minimum un seul caractère et ne peut contenir des espaces, tabulations, etc.
