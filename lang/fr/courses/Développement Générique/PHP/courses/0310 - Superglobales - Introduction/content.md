Les variables superglobales en PHP sont des variables globales prédéfinies. Les variables globales sont des variables de portée globale, ce qui signifie qu'elles peuvent être utilisées partout où cela est nécessaire - elles n'ont pas besoin d'être déclarées, ni d'être marquées comme globales dans les fonctions. Toutes les variables superglobales sont écrites en majuscules, comme ```$_GLOBALS```.

## Liste des variables superglobales

Toutes les variables superglobales agissent comme des tableaux associatifs qui utilisent une valeur de chaîne comme clé pour accéder aux valeurs. Voici la liste des variables superglobales en PHP :

- ```$_GLOBALS``` est la variable superglobale qui stocke toutes les variables globales définies par l'utilisateur. Les noms des variables globales agissent comme des clés pour accéder à leurs valeurs.
- ```$_SERVER``` contient des données sur les en-têtes, les scripts et les chemins. Les clés des valeurs de ce tableau sont prédéfinies.
- ```$_REQUEST``` stocke les données saisies sous la forme de HTTP POST, GET et Cookies. Les clés de ce tableau sont définies dans les requêtes HTTP.
- ```$_POST``` stocke les données saisies sous la forme de demandes POST. Les clés de ce tableau sont définies dans la demande HTTP POST.
- ```$_GET``` contient des données saisies sous la forme de requêtes GET. Les clés de ce tableau sont définies dans la requête HTTP GET.
- ```$_FILES``` est un tableau associatif bidimensionnel qui contient une liste de fichiers téléchargés vers le script à l'aide de la méthode POST. Les clés de ce tableau sont les noms des champs qui ont téléchargé les fichiers et les données auxquelles on accède. Par exemple, ```$_FILES[fileUploaded][name]``` permet d'accéder au nom du fichier téléchargé à partir du champ fileUploaded.
- ```$_COOKIES``` conserve les données saisies via les cookies HTTP. Les clés de ce tableau sont définies lorsque les cookies sont définis.
- ```$_SESSION``` contient les variables de session. Les variables de session sont accessibles sur plusieurs pages. Les clés de ce tableau sont définies par les utilisateurs lorsqu'ils définissent les variables de session.
- ```$_ENV``` contient des informations sur l'environnement dans lequel PHP est exécuté. Les clés des valeurs de ce tableau sont prédéfinies.