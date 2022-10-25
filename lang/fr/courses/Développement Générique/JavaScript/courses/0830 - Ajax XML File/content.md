AJAX peut-être utilisé pour communiquer interactivement avec un fichier XML.

## Exemple

L’exemple ci-dessous est utilisé afin d’expliquer comment utiliser AJAX pour communiquer avec des fichiers XML :

```js
function loadDoc() {
    const xhttp = new XMLHttpRequest();
    xhttp.onload = function() {myFunction(this);}
    xhttp.open("GET", "cd_catalog.xml");
    xhttp.send();
}

function myFunction(xml) {
    const xmlDoc = xml.responseXML;
    const x = xmlDoc.getElementsByTagName("CD");
    let table="<tr><th>Artist</th><th>Title</th></tr>";
    for (let i = 0; i <x.length; i++) {
        table += "<tr><td>" +
        x[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
        "</td><td>" +
        x[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
        "</td></tr>";
    }
    document.getElementById("demo").innerHTML = table;
}
```

Lorsque l’utilisateur clique sur un bouton, la fonction ```loadDoc()``` est exécutée. Dans le programme, cette fonction crée un objet ```XMLHttpRequest```, ajoute la fonction à exécuter lorsque la réponse du serveur est reçue et envoie la requête au serveur. 

Lorsque la réponse du serveur est prête, le tableau HTML est créé, les nœuds - éléments - sont extraits du fichier XML et met à jour l’élément "démo" avec le tableau HTML rempli des données XML.