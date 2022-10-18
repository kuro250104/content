Lors du développement d'un site Web, le concepteur doit être en mesure de voir ses pages Web de la même manière que l'utilisateur final. Parfois, le simple fait de cliquer sur vos fichiers HTML et de les visualiser dans le navigateur Web est suffisant, mais si vous voulez tester du contenu dynamique, vous devrez configurer un serveur Web local. Cette opération est assez simple et peut être réalisée facilement sous Windows, macOS et Linux. Il existe de nombreux types de serveurs Web, mais nous utilisons Apache dans ce tutoriel, car il s'agit du serveur le plus courant, très facile à configurer et compatible avec tous les principaux systèmes d'exploitation.

## Installation sous Windows

Téléchargez la version Windows de XAMPP sur le site officiel https://www.apachefriends.org/index.html et commencez l'installation. Suivez les instructions de l'installateur.

## Installation sous Linux

Apache a été conçu pour les systèmes d'exploitation de type Unix. Linux fait partie de cette catégorie, et l'installation et la configuration d'un serveur web Apache peuvent se faire en une seule étape.

Nous traiterons ici de la ligne de commande. La plupart des distributions populaires vous permettent d'installer Apache sans le compiler à partir des sources en utilisant une simple commande.

**Pour Debian, Ubuntu :**

``` 
sudo apt install apache2
```

**Pour CentOS :**

```
sudo dnf install httpd
```

"127.0.0.1" ou "localhost" dans votre navigateur web permet de voir la page par défaut de Apache.
Les fichiers sont à mettre dans ce dossier “cd /var/www/html”.

## Installation sous macOS

L'avantage de macOS est qu'Apache y est installé par défaut. Tout ce que vous avez à faire est de l'activer.

Dans le Finder, allez dans "Applications -> Utilitaires", puis double-cliquez sur Terminal pour l'ouvrir.

```
sudo apachectl start
```

"127.0.0.1" ou "localhost" dans votre navigateur web permet de voir la page par défaut de Apache.

Les fichiers sont à mettre dans ce dossier “cd /Library/WebServer/Documents/”.