Ce cours montre quelques applications HTML utilisant XML, HTTP, DOM et JavaScript.

## Afficher des données XML dans un tableau HTML

Exemple :

```js
<table id="demo"></table>

<script>
function loadXMLDoc() {
    const xmlhttp = new XMLHttpRequest();
    xmlhttp.onload = function() {
        const xmlDoc = xml.responseXML;
        const cd = xmlDoc.getElementsByTagName("CD");
        myFunction(cd);
    }
    xmlhttp.open("GET", "cd_catalog.xml");
    xmlhttp.send();
}

function myFunction(cd) {
    let table="<tr><th>Artist</th><th>Title</th></tr>";
    for (let i = 0; i < cd.length; i++) {
        table += "<tr><td>" +
        cd[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
        "</td><td>" +
        cd[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
        "</td></tr>";
    }
    document.getElementById("demo").innerHTML = table;
}
</script>

</body>
</html>
```

Cet exemple boucle sur chaque élément ```<CD>``` et affiche les valeurs de ```<ARTIST>``` et ```<TITLE>``` dans un tableau HTML.

## Afficher le premier CD dans un élément div

Exemple :

```js
const xhttp = new XMLHttpRequest();
xhttp.onload = function() {
    const xmlDoc = xhttp.responseXML;
    const cd = xmlDoc.getElementsByTagName("CD");
    myFunction(cd, 0);
}
xhttp.open("GET", "cd_catalog.xml");
xhttp.send();

function myFunction(cd, i) {
    document.getElementById("showCD").innerHTML =
    "Artist: " +
    cd[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
    "<br>Title: " +
    cd[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
    "<br>Year: " +
    cd[i].getElementsByTagName("YEAR")[0].childNodes[0].nodeValue;
}
```

Cet exemple utilise une fonction pour le premier CD dans un élément HTML portant l’id ```showCd```.

## Naviguer entre les CDs

Exemple :

```js
function next() {
    // display the next CD, unless you are on the last CD
    if (i < len-1) {
        i++;
        displayCD(i);
    }
}

function previous() {
    // display the previous CD, unless you are on the first CD
    if (i > 0) {
        i--;
        displayCD(i);
    }
}
```

Dans l’exemple du point précédent, il est possible de naviguer entre les CDs. Pour ce faire, deux fonctions - ```next()``` et ```previous()``` - sont créées.

## Montrer les informations d’un CD en cliquant dessus

Exemple :

```js
function displayCD(i) {
    document.getElementById("showCD").innerHTML =
    "Artist: " +
    cd[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
    "<br>Title: " +
    cd[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
    "<br>Year: " +
    cd[i].getElementsByTagName("YEAR")[0].childNodes[0].nodeValue;
}
```

Cet exemple montre comment afficher les informations d’un CD lorsque l’utilisateur clique sur ledit CD.