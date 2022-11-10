## Introduction

Nous allons ici comprendre pourquoi jQuery est une bonne option pour les opérations de manipulation HTML DOM, et présenter les différents outils fournis par jQuery pour sélectionner, insérer, modifier ou supprimer des éléments ou des attributs.

## La sélection d’éléments en jQuery

Le moyen le plus simple de sélectionner des éléments HTML dans jQuery est d'utiliser des sélecteurs CSS.

Par exemple, nous pouvons sélectionner l’élément ayant la classe container de la manière suivante :

```js
$(document).ready(function () {
    /*
    Sélection des éléments du DOM ayant la classe “container”
    */
    $(".container");
});
```

JQuery fournit également la possibilité de sélectionner certains éléments spécifiques grâce aux "pseudo sélecteur".

Il en existe plusieurs, parmis lesquels :

- **:input** pour cibler les éléments input, textarea, select et button

```html
<body>
    <input type="text" value="Nom:" />
    <span id="count"></span>
    <script type="text/javascript">
    	$(document).ready(function () {
	        //Affiche le nombre d'élément checked
	        $("#count").text($(":input").length);
	    });
    </script>
</body>
```

- **:checked** pour cibler les éléments cochés pour les input de type checkbox, radio ou des éléments d’une liste select

```html
<body>
	<input type="checkbox" checked/>
	<input type="checkbox" />
	<span id="count"></span>
	<script type="text/javascript">
		$(document).ready(function () {
			//Affiche le nombre d'élément checked
			$("#count").text($("input:checked").length);
		});
	</script>
</body>
```

- **:selected** pour cibler les éléments option sélectionnés dans une liste select

```html
<body>
	<select>
		<option value="1">1</option>
		<option value="2" selected>2</option>
		<option value="3">3</option>
	</select>
	<span id="count"></span>
	<script type="text/javascript">
		$(document).ready(function () {
			//Affiche le nombre d'option selected
			$("#count").text($("select option:selected").length);
		});
	</script>
</body>
```

- **:disabled** pour cibler les éléments input qui ont comme attribut disabled

```html
<body>
	<input type="text" disabled>
	<input type="text">
	<span id="count"></span>
	<script type="text/javascript">
	$(document).ready(function () {
		//Affiche le nombre d'input disabled
		$("#count").text($("input:disabled").length);
	});
	</script>
</body>
```

- **:enabled** pour cibler les éléments qui ne possèdent pas l’attribut disabled

```html
<body>
	<input type="text" enabled>
	<input type="text">
	<span id="count"></span>
	<script type="text/javascript">
		$(document).ready(function () {
			//Affiche le nombre d'input enabled
			$("#count").text($("input:enabled").length);
		});
	</script>
</body>
```

### La méthode jQuery has()

La méthode ```has()``` de jQuery permet d'optimiser la sélection en ne sélectionnant que les éléments qui ont eux-même des éléments enfants correspondants au sélecteur passé en paramètre de la fonction.

Par exemple, nous pouvons sélectionner tous les éléments p d’une page qui contiennent des éléments span :

```html
<body>
    <p id="p1">Un paragraphe <span> écrit en HTML</span></p>
    <span>Un élément span non contenu dans un élément p</span>
    <p id="p2">Un deuxième paragraphe</p>
    <p>Un <span>troisième</span> paragraphe</p>
	<script type="text/javascript">
		$(document).ready(function(){
			// sélection de tous les éléments "<p>" qui contiennent
			// des balises "<span>"
		    $("p").has("span");
		});
	</script>
</body>
```

### La méthode jQuery filter()

La méthode jQuery ```filter()``` permet d'optimiser une sélection en éliminant tous les éléments qui ne satisfont le sélecteur passé en paramètre de la fonction.

Par exemple, pour ne sélectionner que les éléments span d’une page, qui possèdent la classe “myClass” :

```html
<body>
    <p id="p1">Un paragraphe <span class="myClass">écrit en HTML</span></p>
    <span>Un élément span non contenu dans un élément p</span>
    <p id="p2">Un deuxième paragraphe</p>
    <p>Un <span class="myClass">troisième</span> paragraphe</p>
	<script type="text/javascript">
		$(document).ready(function(){
			// On ne sélectionne que les éléments span qui possèdent
			// la classe "myClass"
		    $("span").filter(".myClass").css("color", "red");
		});
	</script>
</body>
```

### La méthode jQuery not()

La méthode ```not()``` permet de soustraire des éléments sélectionnés qui remplissent certaines conditions depuis le début.

Par exemple, nous pouvons supprimer d’une sélection les éléments span avec un attribut de class spécifique et appliquer une règle à tous les span sauf celles possédant une classe :

```html
<body>
    <p id="p1">Un paragraphe <span class="myClass">écrit en HTML</span></p>
    <span>Un élément span non contenu dans un élément p</span>
    <p id="p2">Un deuxième paragraphe</p>
    <p>Un <span class="myClass">troisième</span> paragraphe</p>
	<script type="text/javascript">
		$(document).ready(function(){
			// On ne sélectionne que les éléments span qui
                   // NE possèdent PAS de classe "myClass"
		    $("span").not(".myClass").css("color", "red");
		});
	</script>
</body>
```

### Les méthodes jQuery first(), last() et eq()

Les méthodes ```first()``` et ```last()``` nous permettront d'optimiser la sélection en sélectionnant respectivement le premier et le dernier élément.

La méthode ```eq()``` nous permettra de sélectionner un seul élément grâce à son index de la même manière que l’on ferait avec l’index d’un tableau. Par conséquent, il permet également de reproduire le comportement des méthodes ```first()``` ou ```last()```.

Pour sélectionner des éléments en fonction de leur position, nous devons fournir un index pour ```eq()```. Ici, il suffit de se rappeler que l'indice du premier élément de l'ensemble de départ est 0, l'indice du deuxième élément est 1, l'indice du troisième élément est 2, et ainsi de suite.

```html
<body>
    <p id="p1">Un paragraphe <span class="myClass">écrit en HTML</span></p>
    <span>Un élément span non contenu dans un élément p</span>
    <p id="p2">Un deuxième paragraphe</p>
    <p>Un <span class="myClass">troisième</span> paragraphe</p>
    <script type="text/javascript">
        $(document).ready(function(){
            //Le premier élément p sera de couleur rouge
            $("p").first().css("color", "red");
            //Le second élément p sera vert
            $("p").eq(1).css("color", "green");
            //Le dernier élément p sera bleu
            $("p").last().css("color", "blue");
        });
    </script>
</body>
```