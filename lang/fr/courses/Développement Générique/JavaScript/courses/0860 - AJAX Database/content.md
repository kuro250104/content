AJAX peut également être utilisé pour communiquer avec une base de données.

## Exemple

Comme pour les cours précédents, un exemple est utilisé afin de démontrer l’utilisation d’une base de donnée avec AJAX :

```js
function showCustomer(str) {
    if (str == "") {
        document.getElementById("txtHint").innerHTML = "";
        return;
    }
    const xhttp = new XMLHttpRequest();
    xhttp.onload = function() {
        document.getElementById("txtHint").innerHTML = this.responseText;
    }
    xhttp.open("GET", "getcustomer.php?q="+str);
    xhttp.send();
}
```

Lorsqu’un utilisateur sélectionne un nom dans la liste d’options, la fonction ```showCustomer()``` est exécutée. La fonction est déclenchée par l’événement ```onchange```.

Ensuite, les étapes suivantes sont effectuées par le programme :

- Vérifie si un utilisateur est sélectionné
- Création d’un objet ```XMLHttpRequest```
- Création de la fonction à exécuter quand la réponse du serveur est prête
- Envoie la réponse à un fichier stocké sur le serveur