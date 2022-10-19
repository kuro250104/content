La superglobale ```$_SESSION``` est un tableau associatif qui contient toutes les variables de session. ```$_SESSION``` permet de sauvegarder des données liées à une connexion utilisateur, c’est comme une petite base de données qui ne dure que le temps d’une navigation (déconnexion, fermeture d'onglet, …).

Exemple :

``` php
<?php
// On démarre la session AVANT d'écrire du code HTML
session_start();

// prenom est une variable de session dans $_SESSION
$_SESSION['prenom'] = 'Marc';

?>

<p>Hello <?php echo $_SESSION['prenom']; ?> !</p>
```

Dans cet exemple, on commence d’abord par lancer la session grâce à la fonction ```session_start()```, ensuite on définit une variable de session “prenom“. Maintenant le paragraphe renvoie “Hello Marc !”.