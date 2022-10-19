La superglobale ```$_POST``` est une variable qui est utilisée pour récupérer les données provenant d’un formulaire HTML qui a été soumis avec la ```method=”post”```. ```$_POST``` est également utilisé pour passer des variables.

``` php
<form method="post" action="<?php echo $_SERVER['PHP_SELF'];?>">
  Prénom: <input type="text" name="name">
  <input type="submit">
</form>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
  // récupérer les données fournies par le formulaire
  $prenom = $_POST['name'];
  if (empty($name)) {
    echo "Le champ prénom est vide";
  } else {
    echo $prenom;
  }
}
?>
```

Dans cet exemple, on y retrouve un formulaire avec un champ prénom et un bouton de soumission. Lorsqu’un utilisateur soumet le formulaire les données du formulaire sont envoyées au fichier lui-même, ceci est précisé dans l’attribut ```action``` de la balise ```<form>``` grâce à la superglobale ```$_SERVER[‘PHP_SELF’]``` qui retourne le fichier actuel. Une fois le formulaire soumis avec la ```method=”post”```, on vérifie si le champ prénom est vide. Si le champ est vide, on renvoie un message “Le champ prénom est vide” sinon, on renvoie la valeur contenue dans le champ.
