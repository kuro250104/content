Le JavaScript permet d’afficher des données à l’utilisateur. Pour ce faire, JavaScript propose 4 possibilités d’affichage de ces données. 

## Possibilités d’affichage en JavaScript

Voici les 4 moyens d’afficher des données en JavaScript :

- ```innerHTML``` : permet d’écrire dans un élément HTML
- ```document.write()``` : permet d’écrire dans le flux de sortie HTML
- ```alert()``` : permet d’afficher une fenêtre d’alerte
- ```console.log()``` : permet d’afficher des données dans la console du navigateur. 

## innerHTML

Pour accéder à un élément HTML, JavaScript met à disposition ```document.getElementById(‘id’)```, qui permet de sélectionner un élément HTML par rapport à son attribut “id”. 

La propriété innerHTML permet de définir le contenu à afficher au sein de l’élément désigné par son id. 

L’avantage de la propriété innerHTML est qu’elle permet d’utiliser des balises HTML.

Exemple : 

``` js
<!DOCTYPE html>
<html>
    <head>
	<meta charset="utf-8" />
	<title>Afficher du texte dans un élément HTML</title>
	<script type="text/javascript">
	    document.getElementById('message').innerHTML='<h1>Hello World</h1>';
	</script>
    </head>

    <body>
	<div id="message">

        </div>
    </body>
</html>
```

Dans cet exemple, le script affiche un ```<h1>``` Hello World dans l’élément HTML portant l’id message.

## document.write()

Pour tester une partie de code, il est parfois utile d’utiliser la propriété ```document.write()```.

Exemple :

``` js
<html>
    <head>
	<meta charset="utf-8" />
	<title>Afficher du texte dans un élément HTML</title>
    </head>

    <body>
        <script>
            document.write('Hello World');
        </script>
    </body>
</html>
```

*Remarque : La propriété document.write ne devrait être utilisée que pour effectuer des tests. En effet, utiliser cette propriété efface tout le HTML présent au sein d’un document.*

## window.alert()

Le langage JavaScript permet également de générer des boîtes de dialogue. Pour ce faire, il faut utiliser la propriété ```window.alert()```.

*Remarque : Étant donné que le préfixe window désigne le document global, ce préfixe est optionnel. Ainsi est-il plus courant de voir écrit, dans un code, alert().*

Exemple :

``` js
<html>
    <head>
	<meta charset="utf-8" />
	<title>Afficher du texte dans un élément HTML</title>
    </head>

    <body>
        <script>
            alert('Hello World !');
        </script>
    </body>
</html>
```

## console.log()

Ce mode d’affichage permet d’afficher du texte dans la console du navigateur. Pour ouvrir la console, il suffit de faire un clic droit sur la page web, puis de cliquer sur “inspecter”. Un panel développeur s’ouvre et donne la possibilité d’afficher la console. 

Cette méthode d’affichage est principalement utilisée pour faire des tests, s’assurer qu’un programme entre bien dans une fonction ou encore qu’une variable contient bien la valeur qu’elle devrait. 

Exemple :

``` js
<html>
    <head>
	<meta charset="utf-8" />
	<title>Afficher du texte dans un élément HTML</title>
    </head>

    <body>
	    <script>
            var nombre = 2;
            console.log(nombre);
        </script>
    </body>
</html>
```

Dans l’exemple ci-dessus, la console affichera le chiffre 2, car c’est le contenu de la variable nombre.

*Remarque : Attention, la console permet d’interagir avec la page javascript sur laquelle vous vous trouvez. Aussi elle peut être utilisée pour simplement interagir avec une page.*