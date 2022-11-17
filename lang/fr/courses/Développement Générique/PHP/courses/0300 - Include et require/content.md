L'instruction ```include()``` ou ```require()``` prend tout le texte/code/balisage existant dans le fichier spécifié et le copie dans le fichier qui utilise l'instruction ```include()``` ou ```require()```. L'inclusion de fichiers est très utile lorsque vous souhaitez inclure le même PHP, HTML ou texte sur plusieurs pages d'un site Web.

Il est possible d'insérer le contenu d'un fichier PHP dans un autre fichier PHP (avant que le serveur ne l'exécute), avec l'instruction include ou require.

Les instructions include et require sont identiques, sauf en cas d'échec :

- ```require()``` : produira une erreur fatale (E_COMPILE_ERROR) et arrêtera le script
- ```include()``` : ne produira qu'un avertissement (E_WARNING) et le script continuera

Donc, si vous voulez que l'exécution se poursuive et montre aux utilisateurs la sortie, même si le fichier d'inclusion est manquant, utilisez l'instruction include. Sinon, dans le cas de FrameWork, CMS ou d'un codage d'application PHP complexe, utilisez toujours l'instruction require pour inclure un fichier clé dans le flux d'exécution. Cela aidera à éviter de compromettre la sécurité et l'intégrité de votre application, juste au cas où un fichier clé serait accidentellement manquant.

L'inclusion de fichiers permet d'économiser beaucoup de travail. Cela signifie que vous pouvez créer un en-tête, un pied de page ou un fichier de menu standard pour toutes vos pages Web. Ensuite, lorsque l'en-tête doit être mis à jour, vous ne pouvez mettre à jour que le fichier d'inclusion d'en-tête.

## Syntaxe

```php
include('filename');

require('filename');
```

## Include

### Exemples

Supposons que nous ayons un fichier de pied de page standard appelé "footer.php", qui ressemble à ceci :

```php
<?php
    echo("<p>Copyright &copy; " . date("Y") . " Microlead.fr</p>");
?>
```

Pour inclure le fichier de pied de page dans une page, utilisez l'instruction ```include()``` :

```php
<html>
<body>

    <h1>Bienvenue sur mon site.</h1>
    <p>Un peu de texte.</p>
    <p>Encore plus de texte.</p>

    <?php include('footer.php';) ?>

</body>
</html>
```

Supposons que nous ayons un fichier de menu standard appelé "menu.php":

```php
<?php
echo('<a href="/">Accueil</a> -
<a href="/html/index.php">HTML</a> -
<a href="/css/index.php">CSS</a> -
<a href="/js/index.php">JavaScript</a> -
<a href="/php/index.php">PHP</a>');
?>
```

Toutes les pages du site Web doivent utiliser ce fichier de menu. Voici comment cela peut être fait (nous utilisons un élément ```<div>``` pour que le menu puisse facilement être stylisé avec CSS plus tard):

```php
<html>
<body>

    <div class="menu">
        <?php include 'menu.php'; ?>
    </div>

    <h1>Bienvenue sur mon site.</h1>
    <p>Un peu de texte.</p>
    <p>Encore plus de texte.</p>

</body>
</html>
```

## Require vs include

L'instruction ```require()``` est également utilisée pour inclure un fichier dans le code PHP.

Cependant, il y a une grande différence entre ```include()``` et ```require()``` ; lorsqu'un fichier est inclus avec l'instruction include et que PHP ne le trouve pas, le script continuera à s'exécuter, exemple :

```php
<html>
<body>

    <h1>Bienvenue sur mon site.</h1>
    <?php 
        include('noFileExists.php');
        echo("J’ai une $car $color.");
    ?>

</body>
</html>
```

Si nous faisons le même exemple en utilisant l'instruction require, l'instruction echo ne sera pas exécutée car l'exécution du script meurt après que l'instruction require ait renvoyé une erreur fatale :

```php
<html>
<body>

    <h1>Bienvenue sur mon site.</h1>
    <?php
        require('noFileExists.php');
        echo("J’ai une $car $color.");
    ?>

</body>
</html>
```