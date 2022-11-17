La superglobale ```$_REQUEST``` est une variable qui est utilisée pour récupérer les données provenant d’un formulaire HTML qui a été soumis.

Exemple :

```php
<form method="post" action="<?php echo $_SERVER['PHP_SELF'];?>">
  Prenom: <input type="text" name="name">
  <input type="submit">
</form>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
  // récupérer les données fournis par le formulaire
  $prenom = $_REQUEST['name'];
  if (empty($name)) {
    echo("Le champ prénom est vide");
  } else {
    echo($prenom);
  }
}
?>
```

Dans cet exemple, on y retrouve un formulaire avec un champ prénom et un bouton de soumission. Lorsqu’un utilisateur soumet le formulaire les données du formulaire sont envoyées au fichier lui-même, ceci est précisé dans l’attribut ```action``` de la balise ```<form>``` grâce à la superglobale ```$_SERVER[‘PHP_SELF’]``` qui retourne le fichier actuel. Une fois le formulaire soumis, on vérifie si le champ prénom est vide. Si le champ est vide, on renvoie un message “Le champ prénom est vide” sinon, on renvoie la valeur contenue dans le champ.