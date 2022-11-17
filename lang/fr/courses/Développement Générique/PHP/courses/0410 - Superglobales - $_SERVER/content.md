La superglobale ```$_SERVER``` est une variable qui contient des informations sur les en-têtes, les chemins et les emplacements des fichiers.

Exemple :

``` php
<?php
echo($_SERVER['SCRIPT_NAME']);
echo($_SERVER['HTTP_USER_AGENT']);
echo($_SERVER['SERVER_NAME']);
echo($_SERVER['PHP_SELF']);
echo($_SERVER['HTTP_HOST']);
?> 
```

La liste ci-dessus répertorie les éléments pouvant être intégrés à ```$_SERVER``` :

- ```$_SERVER[‘PHP_SELF’]``` : renvoie le nom du fichier en cours d’exécution,
- ```$_SERVER[‘GATEWAY_INTERFACE’]``` : renvoie l’interface commune que le serveur utilise,
- ```$_SERVER[‘SERVER_ADDR’]``` : renvoie l’adresse IP du serveur hôte,
- ```$_SERVER[‘SERVER_NAME’]``` : renvoie le nom du serveur hôte,
- ```$_SERVER[‘SERVER_PROTOCOL’]``` : renvoie le nom et la révision du protocole d’information,
- ```$_SERVER[‘REQUEST_METHOD’]``` : renvoie la méthode de requête utilisée pour accéder à la page,
- ```$_SERVER[‘REQUEST_TIME’]``` : renvoie la date du début de la requête,
- ```$_SERVER[‘QUERY_STRING’]``` : renvoie la chaîne de requête de la page,
- ```$_SERVER[‘HTTP_ACCEPT’]``` : renvoie l’en-tête Accept de la requête en cours,
- ```$_SERVER[‘HTTP_ACCEPT_CHARSET’]``` : renvoie l’en-tête Accept_Charset de la requête actuelle,
- ```$_SERVER[‘HTTP_HOST’]``` : renvoie l’en-tête Host de la requête actuelle,
- ```$_SERVER[‘HTTP_REFERER’]``` : renvoie l’URL complète de la page actuelle,
- ```$_SERVER[‘HTTPS’]``` : renvoie un boolean (true) si le script est interrogé via un protocole HTTP sécurisé, 
- ```$_SERVER[‘REMOTE_ADDR’]``` : renvoie l’adresse IP à partir de laquelle l’utilisateur consulte la page actuelle,
- ```$_SERVER[‘REMOTE_HOST’]``` : renvoie le nom d’hôte à partir duquel l’utilisateur affiche la page actuelle,
- ```$_SERVER[‘REMOTE_PORT’]``` : renvoie le port utilisé sur la machine de l’utilisateur pour communiquer avec le serveur,
- ```$_SERVER['SCRIPT_FILENAME']``` : renvoie le chemin d'accès absolu du script en cours d’exécution,
- ```$_SERVER['SERVER_ADMIN’']``` : renvoie la valeur donnée à la directive SERVER_ADMIN dans le fichier de configuration du serveur,
- ```$_SERVER[‘SERVER_PORT’]``` : renvoie le port sur la machine serveur utilisé par le serveur pour la communication (exemple: port 80),
- ```$_SERVER[‘SERVER_SIGNATURE’]``` : renvoie la version du serveur et le nom d’hôte virtuelle qui sont ajoutés aux pages générées par le serveur,
- ```$_SERVER['PATH_TRANSLATED']``` : renvoie le chemin basé sur le système de fichiers vers le script actuel,
- ```$_SERVER[‘SCRIPT_NAME’]``` : renvoie le chemin du script actuel,
- ```$_SERVER[‘SCRIPT_URI’]``` : renvoie l’uri de la page en cours.