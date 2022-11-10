## Introduction

JQuery permet de sélectionner un ou plusieurs éléments à l'aide de sélecteurs CSS ou de pseudo-sélecteurs jQuery. A la suite de cette première sélection, il est possible de l’affiner en utilisant les méthodes décrites dans les cours précédents, de niveaux inférieurs.

Comme vu précédemment, il est possible de sélectionner des éléments en jQuery grâce aux sélecteurs CSS. Par exemple : 

```html
<body>
    <p class="first">Je suis un paragraphe</p>
    <p id="second">Je suis un autre paragraphe</p>
    <script type="text/javascript">
        $(document).ready(function(){
            // sélection de l'élément HTML possédant
            // la classe "first"
            $(".first");
            // sélection de l'élément HTML possédant
            // l'id "second"
            $("#second");
        });
    </script>
</body>
```

Cependant, ce n'est pas le seul moyen d'accéder aux éléments du DOM. Les sélections effectuées dans l’exemple ci-dessus constituent en réalité des sélections initiales. C’est-à-dire qu’il est possible d’appliquer d’autres méthodes jQuery qui permettent de “parcourir” le DOM en se basant sur cette sélection initiale.

## Accéder à l’élément parent ou aux ancêtres d’un élément en jQuery

Les méthodes ```parent()```, ```parents()```, ```parentsUntil()``` et ```closest()``` permettent d'accéder aux parents et ancêtres d'un élément ou d'une collection d'éléments.

La méthode ```parent()``` permet d'accéder à l'élément parent de notre sélection initiale, qu’elle soit constituée par un ou plusieurs éléments. Il est possible de lui passer un sélecteur en argument, ce qui filtrera la sélection et ne retournera son élément parent que si l'élément correspond audit sélecteur.

```html
<body>
    <ul id="parents">
        <li>Element</li>
        <li>Element</li>
        <li>element</li>
    </ul>
    <script type="text/javascript">
        $(document).ready(function(){
            // Cible l'élément parent direct de chaque élément
            // li et ajoute une bordure autour
            $("li").parent().css("border", "10px solid black");
            // Cible l'élément parent direct de chaque élément
            // li uniquement si il possède un id="parents" et
            // change la couleur de fond en rouge
            $("li").parent("#parents").css("background-color", "red");
        });
    </script>
</body>
```

La méthode ```parents()``` permet d'accéder à tous les ancêtres d'un élément ou d'un groupe d’éléments sélectionné. Cette méthode sera la même que ```parent()``` et accédera également au sélecteur pouvant être passé en tant qu’argument.

```html
<body>
    <div>
        <ul id="parents">
            <li>Element</li>
            <li>Element</li>
            <li>element</li>
        </ul>
    </div>
    <script type="text/javascript">
        $(document).ready(function(){
            // Sélectionne tous les ancêtres des éléments ul et ajoute
            // une bordure noire d'10px autour de chacun d'entre eux
            $("ul").parents().css("border", "10px solid black");
            // Ne cible que les ancêtres des éléments ul qui sont des
            // div et change leur couleur de fond en rouge
            $("ul").parents("div").css("background-color", "red");
        });
    </script>
</body>
```

La méthode ```parentUntil()``` permet également d'accéder aux ancêtres d'un élément ou d'un groupe d'éléments jusqu'à l'ancêtre correspondant au sélecteur passé en premier argument de la méthode.

Il est également possible de passer un second sélecteur en tant que deuxième argument, qui jouera le rôle de filtre pour la méthode ```parentUntil()```.

```html
<body>
    <div class="container">
        <ul id="child filter">
            <li>Element</li>
            <li>Element</li>
            <li>element</li>
        </ul>
    </div>
    <script type="text/javascript">
        $(document).ready(function(){
            // Sélectionne tous les ancêtres de l'élément qui possède l'id="child" 
            // jusqu'au premier ancêtre possédant une class="container" sans l'inclure
            $("#child").parentsUntil(".container").css("border", "10px solid black");
            // Sélectionne tous les ancêtres de l'élément qui possède l'id="child" 
            // jusqu'au premier ancêtre possédant une class="container" et la classe
            // "filter" en filtre sans l'inclure
            $("#child").parentsUntil(".container", ".filter").css("border", "10px solid red");
        });
    </script>
</body>
```

La méthode ```closest()``` permet de sélectionner le premier ancêtre correspondant au sélecteur qui lui est passé en argument.

```html
<body>
    <div>
        <ul id="parents" class="red">
            <li class="li">Element</li>
            <li>Element</li>
            <li>Element</li>
        </ul>
    </div>
    <script type="text/javascript">
        $(document).ready(function(){
            // Sélectionne l'ancêtre div le plus proche de l'élément
            // possédant l'id "parents"
            $("#parents").closest("div").css("border", "10px solid black");
            // Sélectionne l'ancêtre possédant une class="red" le plus
            // proche des éléments possédant une class="li"
            $(".li").closest(".blue").css("color", "red");
        });
    </script>
</body>
```

## Accéder aux enfants ou descendants d’un élément en jQuery

Les méthodes ```children()``` et ```find()``` permettent d'accéder aux enfants et aux descendants de l'élément ou de la collection d'éléments initialement sélectionnés dans jQuery.

La méthode ```children()``` permet d'accéder aux éléments enfants d'un ou de plusieurs éléments du DOM. Nous pourrons lui passer un sélecteur en argument, qui servira de filtre pour ne sélectionner que les enfants correspondant à celui-ci.

La méthode ```find()``` permet de sélectionner tous les descendants d'un élément ou d'une collection d'éléments. Pour l’utiliser, il faut lui préciser un sélecteur en argument, qui servira de filtre pour ne sélectionner que les descendants correspondant à celui-ci.

```html
<body>
    <div class="container">
        <div id="methods">
            <ul id="parents">
                <li class="background">Element</li>
                <li>Element</li>
                <li>Element</li>
            </ul>
        </div>
    </div>
    <script type="text/javascript">
        $(document).ready(function(){
            // Sélectionne tous les enfants (descendants directs) des
            // éléments possédant un attribut class="container"
            $(".container").children().css("border", "10px solid black");
            // Sélectionne uniquement les éléments h1 descendants directs
            // des éléments possédant un attribut classe "container"
            $(".container").children("h1").css("color", "red");
            // Cible tous les descendants de l'élément possédant l'id
            // "methods" qui possèdent un attribut class="background"
            $("#methods").find(".background").css("background-color", "orange");
        });
    </script>
</body>
```

## Accéder aux éléments frères d’un élément en jQuery

Nous allons ici étudier les méthodes ```siblings()```, ```next()```, ```nextAll()```, ```nextUntil()```, ```prev()```, ```prevAll()``` et ```prevUntil()```.

La méthode ```siblings()``` renvoie l’ensemble des éléments frères de la sélection initiale. Il est possible de passer un “filtre” en argument de cette méthode lors de son utilisation grâce aux sélecteurs CSS afin d’affiner le ciblage.

```html
<body>
    <ul>
        <li>Element</li>
        <li>Element</li>
        <li>Element</li>
        <li>Element</li>
    </ul>
    <script type="text/javascript">
        $(document).ready(function(){
            //Sélectionne les éléments li qui sont les premiers
            // enfants de leur parent puis récupère tous leurs
            // frères et leur  applique une couleur de texte rouge
            $("li:first-child").siblings().css("color", "red");
            // Sélectionne les éléments li qui sont les premiers enfants
            // de leur parent et ne récupère que les éléments frères qui
            // occupent une place impaire en comptant à partir de li:first-child
            $("li:first-child").siblings(":odd").css("text-decoration", "underline");
        });
    </script>
</body>
```

La méthode ```next()``` permet de récupérer l’élément frère immédiatement après la sélection initiale. Il est également possible lui passer un sélecteur CSS en argument, qui jouera le rôle de filtre : la méthode ne récupérera le prochain objet frère que s'il correspond au sélecteur.

La méthode ```nextAll()``` permet de récupérer tous les éléments frères après la sélection initiale. Il est possible de lui passer un sélecteur pour filtrer le résultat en argument.

La méthode ```nextUntil()``` récupère tous les éléments frères après une sélection initiale jusqu'à ce qu’un élément frère corresponde au sélecteur passé en premier argument. Il est également possible d’utiliser un second argument sur cette méthode afin de filtrer davantage la sélection.

```html
<body>
    <ul>
        <li>Element</li>
        <li>Element</li>
        <li>Element</li>
        <li>Element</li>
    </ul>
    <script type="text/javascript">
        $(document).ready(function(){
            //Sélectionne l'élément frère suivant li:first-child
            $("li:first-child").next().css("color", "red");
            // Sélectionne tous les éléments frères du 2è élément li
            // le suivant qui occupent une place impaire en comptant
            // à partir de li:nth-child(2)
            $("li:nth-child(2)").nextAll(":odd").css("text-decoration", "underline");
            // Sélectionne les éléments frères du 2è élément li le
            // suivant jusqu'au 5è élément li sans inclure celui-ci
            // dans la sélection et applique une police épaisse
            $("li:nth-child(2)").nextUntil("li:nth-child(5)").css("font-weight", "bold");
        });
    </script>
</body>
```

Les méthodes ```prev()```, ```prevAll()``` et ```prevUntil()``` fonctionnent de la même manière que les méthodes précédentes, à ceci près qu'elles agissent non plus sur les éléments suivants la sélection initiale, mais sur les précédents.

```html
<body>
    <ul>
        <li>Element</li>
        <li>Element</li>
        <li>Element</li>
        <li>Element</li>
        <li>Element</li>
        <li>Element</li>
        <li>Element</li>
    </ul>
    <script type="text/javascript">
        $(document).ready(function(){
            //Sélectionne l'élément frère précédant li:nth-child(4)
            $("li:nth-child(4)").prev().css("color", "red");
            //Sélectionne tous les éléments frères précédant li:nth-child(4)
            $("li:nth-child(4)").prevAll().css("text-decoration", "underline");
            //Sélectionne les éléments frères précédant #desc jusqu'à h1 sans l'inclure
            $("#desc").prevUntil("h1").css("border", "10px solid black");
        });
    </script>
</body>
```