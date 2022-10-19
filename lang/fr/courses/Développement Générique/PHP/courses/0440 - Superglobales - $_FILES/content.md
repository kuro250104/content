La superglobale ```$_FILES``` est une variable qui est utilisée pour le téléchargement de fichier via HTTP. ```$_FILES``` est un tableau associatif des valeurs téléchargées via le protocole HTTP et à la ```method=”post”```. ```$HTTP_POST_FILES``` contient les mêmes informations, mais il ne s'agit pas d’une superglobale. PHP traite ```$_FILES``` et ```$HTTP_POST_FILES``` comme des variables différentes.

Exemple :

``` php
<?php
if(isset($_FILES['image']))
{ 
     $dossier = 'upload/';
     $fichier = basename($_FILES['image']['name']);
	 //on utilise la fonction move_uploaded_file() 
     if(move_uploaded_file($_FILES['image']['tmp_name'], $dossier . $fichier))
	 //Si la fonction renvoie TRUE
     {
          echo 'Upload effectué avec succès !';
     }
     else 
	 //Sinon, la fonction renvoie FALSE
     {
          echo 'Echec de l\'upload !';
     }
}
?>
```

Il ne faut pas mettre ce script en ligne, car un utilisateur pourrait vouloir supprimer la base de données à la place d’effectuer un upload. Il faudra donc sécuriser le script avant de l’utiliser.