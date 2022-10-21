L’une des principales utilisations de JavaScript est la manipulation des éléments HTML. Pour ce faire, il faut d’abord trouver l’élément en question. Il existe plusieurs moyens de faire cela.

## Trouver un élément HTML par son ID

Le moyen le plus simple de trouver un élément HTML dans le DOM est de le faire grâce à son Id. Pour ce faire, la méthode ```document.getElementById(*id*)``` est utilisée. 

Ensuite, si l’élément est trouvé, il est retourné sous forme d’objet. Sinon, null est renvoyé.

Exemple :

```js
const element = document.getElementById("intro");
```

Dans cet exemple, l’élément HTML portant l’Id intro est recherché. S’il est trouvé, la variable ```element``` contient l’élément sous forme d’objet. Sinon, elle se voit attribuer la valeur ```null```.

## Trouver un élément HTML par le nom de sa classe

Un autre moyen de trouver un élément HTML est de le rechercher par le nom de sa classe. Cette fois, c’est la méthode ```document.getElementsByClassName(nom_de_la_classe)``` qui est utilisée.

L’utilisation et le fonctionnement de cette méthode est la même que pour ```document.getElementById(id)```.

Exemple :

```js
const x = document.getElementsByClassName("intro");
```

## Trouver un élément HTML par le tag

En HTML, le tag est la balise qui entoure un élément. Ainsi, en JavaScript, est-il possible de rechercher un élément par sa balise. 

Cette fois, c’est la méthode ```document.getElementsByTagName(tag)``` qui est utilisée.

Exemple :

```js
const element = document.getElementsByTagName("p");
```

Exemple :

```js
const x = document.getElementById("main");
const y = x.getElementsByTagName("p");
```

Dans ce second exemple, l’élément portant l’id ```main``` est d’abord recherché. Puis, tous les éléments ```<p>``` contenus dans cet élément ```#main``` sont recherchés.

## Trouver un élément HTML grâce aux sélecteurs CSS

Il est possible de trouver tous les éléments HTML qui correspondent à un sélecteur CSS (id, classe, types, attributs, valeur d’attribut, etc.). Pour cela, il faut utiliser la méthode ```document.querySelectorAll(selecteur)```.

Exemple :

```js
const x = document.querySelectorAll("p.intro");
```

Cet exemple retourne tous les paragraphes contenus dans les éléments ayant la classe ```intro```.

## Trouver des éléments HTML par la collection d’objets HTML

La liste ci-dessous dresse les objets HTML accessibles en HTML :

- ```document.anchors```
- ```document.body```
- ```document.documentElement```
- ```document.embeds```
- ```document.forms```
- ```document.head```
- ```document.images```
- ```document.links```
- ```document.scripts```
- ```document.title```
- ```document.form```

Exemple :

```js
const x = document.forms["frm1"];
let text = "";
for (let i = 0; i < x.length; i++) {
    text += x.elements[i].value + "<br>";
}
document.getElementById("demo").innerHTML = text;
```

Dans cet exemple, le formulaire ```frm1``` est recherché parmi tous les formulaires du document. Ensuite, les valeurs des éléments sont affichées.