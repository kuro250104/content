AJAX est également utilisé afin de créer du contenu encore plus interactif.

L’exemple du cours précédent est réutilisé, mais avec ASP, cette fois-ci.

## Exemple

```js
<p>Commencez par saisir un nom dans le champ ci-dessous :</p>
<p>Suggestions : <span id="txtHint"></span></p>

<form>
Prénom : <input type="text" onkeyup="showHint(this.value)">
</form>

<script>
function showHint(str) {
    if (str.length == 0) {
        document.getElementById("txtHint").innerHTML = "";
        return;
    } else {
        const xmlhttp = new XMLHttpRequest();
        xmlhttp.onload = function() {
            document.getElementById("txtHint").innerHTML = this.responseText;
        }
    xmlhttp.open("GET", "gethint.asp?q=" + str);
    xmlhttp.send();
  }
}
</script>
```

Dans cet exemple, lorsque l’utilisateur saisit le nom d’un personnage dans le champ de texte, la fonction ```showHint()``` est exécutée.

Cette fonction est en fait déclenchée par l’événement ```onkeyup```.

Pour ce qui est du code en lui-même, voici le code décrit en détail. Dans un premier temps, une vérification est effectuée sur le champ de saisie, afin de s’assurer qu’il n’est pas vide. Le cas échéant, le code effectue les étapes suivantes :

- Création d’un objet ```XMLHttpRequest```
- Création de la fonction à exécuter lorsque la réponse du serveur est prête
- La réponse est envoyée à un fichier PHP sur le serveur : le fichier gethint.php
- La variable str retient le contenu du champ de texte