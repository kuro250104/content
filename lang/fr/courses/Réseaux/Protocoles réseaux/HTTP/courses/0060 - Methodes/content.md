L'ensemble des méthodes communes pour HTTP/1.1 est défini ci-dessous et cet ensemble peut être étendu en fonction des besoins. Ces noms de méthodes sont sensibles à la casse et doivent être utilisés en majuscules :	

- **GET** : La méthode **GET** est utilisée pour récupérer des informations sur un serveur donné à l'aide d'un URI donné. Les requêtes utilisant **GET** doivent uniquement récupérer des données et ne doivent avoir aucun autre effet sur les données.
- **HEAD** : Identique à la méthode **GET**, mais elle transfère uniquement la ligne d'état et la section d'en-tête.
- **POST** : Une requête **POST** est utilisée pour envoyer des données au serveur, par exemple, des informations sur les clients, le téléchargement de fichiers, etc. à l'aide de formulaires HTML.
- **PUT** : Remplace toutes les représentations actuelles de la ressource cible par le contenu téléchargé.
- **DELETE** : Supprime toutes les représentations actuelles de la ressource cible indiquée par l'URI.
- **CONNECT** : Établit un tunnel vers le serveur identifié par un URI donné.
- **OPTIONS** : Décrit les options de communication pour la ressource cible.
- **TRACE** : Effectue un test de retour en boucle des messages ainsi que le chemin vers la ressource cible.

## Méthode GET

Une requête GET permet de récupérer des données sur un serveur web en spécifiant des paramètres dans la partie URL de la requête. Il s'agit de la principale méthode utilisée pour la récupération de documents. L'exemple suivant utilise la méthode GET pour récupérer ```hello.htm``` :

```http
GET /hello.htm HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
Host: www.microlead.fr
Accept-Language: en-us
Accept-Encoding: gzip, deflate
Connection: Keep-Alive
```

La réponse du serveur à la demande **GET** ci-dessus sera la suivante :

```http
HTTP/1.1 200 OK
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Wed, 22 Jul 2009 19:15:56 GMT
ETag: "34aa387-d-1568eb00"
Vary: Authorization,Accept
Accept-Ranges: bytes
Content-Length: 88
Content-Type: text/html
Connection: Closed
```

```html
<html>
    <body>
        <h1>Hello, World!</h1>
    </body>
</html>
```

## HEAD Method

La méthode **HEAD** est fonctionnellement similaire à **GET**, sauf que le serveur répond avec une ligne de réponse et des en-têtes, mais pas de corps d'entité. L'exemple suivant utilise la méthode HEAD pour récupérer les informations d'en-tête de hello.htm :

```http
HEAD /hello.htm HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
Host: www.microlead.fr
Accept-Language: en-us
Accept-Encoding: gzip, deflate
Connection: Keep-Alive
```

La réponse du serveur à la demande **HEAD** ci-dessus sera la suivante :

```http
HTTP/1.1 200 OK
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Wed, 22 Jul 2009 19:15:56 GMT
ETag: "34aa387-d-1568eb00"
Vary: Authorization,Accept
Accept-Ranges: bytes
Content-Length: 88
Content-Type: text/html
Connection: Closed
```

Vous pouvez remarquer qu'ici le serveur n'envoie pas de données après l'en-tête.

## Méthode POST

La méthode **POST** est utilisée lorsque vous souhaitez envoyer des données au serveur, par exemple, une mise à jour de fichier, des données de formulaire, etc. L'exemple suivant utilise la méthode **POST** pour envoyer les données d'un formulaire au serveur, qui seront traitées par un ```process.cgi``` et finalement une réponse sera renvoyée :

```http
POST /cgi-bin/process.cgi HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
Host: www.microlead.fr
Content-Type: text/xml; charset=utf-8
Content-Length: 88
Accept-Language: en-us
Accept-Encoding: gzip, deflate
Connection: Keep-Alive
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<string xmlns="http://clearforest.com/">string</string>
```

Le script côté serveur ```process.cgi``` traite les données transmises et envoie la réponse suivante :

```http
HTTP/1.1 200 OK
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Wed, 22 Jul 2009 19:15:56 GMT
ETag: "34aa387-d-1568eb00"
Vary: Authorization,Accept
Accept-Ranges: bytes
Content-Length: 88
Content-Type: text/html
Connection: Closed
```

```html
<html>
    <body>
        <h1>Request Processed Successfully</h1>
    </body>
</html>
```

## Méthode PUT

La méthode **PUT** est utilisée pour demander au serveur de stocker le corps d'entité inclus à un emplacement spécifié par l'URL donnée. L'exemple suivant demande au serveur d'enregistrer le corps d'entité donné dans ```hello.htm``` à la racine du serveur :

```http
PUT /hello.htm HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
Host: www.microlead.fr
Accept-Language: en-us
Connection: Keep-Alive
Content-type: text/html
Content-Length: 182
```

```html
<html>
    <body>
        <h1>Hello, World!</h1>
    </body>
</html>
```

Le serveur stockera le corps d'entité donné dans le fichier ```hello.htm``` et renverra la réponse suivante au client :

```http
HTTP/1.1 201 Created
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache/2.2.14 (Win32)
Content-type: text/html
Content-length: 30
Connection: Closed
```

```html
<html>
    <body>
        <h1>The file was created.</h1>
    </body>
</html>
```

## Méthode DELETE

La méthode **DELETE** est utilisée pour demander au serveur de supprimer un fichier à un emplacement spécifié par l'URL donnée. L'exemple suivant demande au serveur de supprimer le fichier ```hello.htm``` à la racine du serveur :

```http
DELETE /hello.htm HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
Host: www.microlead.fr
Accept-Language: en-us
Connection: Keep-Alive
```

Le serveur supprimera le fichier mentionné hello.htm et renverra la réponse suivante au client :

```http
HTTP/1.1 200 OK
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache/2.2.14 (Win32)
Content-type: text/html
Content-length: 30
Connection: Closed
```

```html
<html>
    <body>
        <h1>URL deleted.</h1>
    </body>
</html>
```

## Méthode CONNECT

La méthode **CONNECT** est utilisée par le client pour établir une connexion réseau avec un serveur Web via HTTP. L'exemple suivant demande une connexion avec un serveur web fonctionnant sur l'hôte microlead.fr :

```http
CONNECT www.microlead.fr HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
```

La connexion est établie avec le serveur et la réponse suivante est renvoyée au client :

```http
HTTP/1.1 200 Connection established
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache/2.2.14 (Win32)
```

## Méthode OPTIONS

La méthode **OPTIONS** est utilisée par le client pour connaître les méthodes HTTP et les autres options prises en charge par un serveur Web. Le client peut spécifier une URL pour la méthode **OPTIONS**, ou un astérisque (*) pour faire référence à l'ensemble du serveur. L'exemple suivant demande une liste des méthodes prises en charge par un serveur Web fonctionnant sur microlead.fr :

```http
OPTIONS * HTTP/1.1
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
```

Le serveur enverra une information basée sur la configuration actuelle du serveur, par exemple :

```http
HTTP/1.1 200 OK
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache/2.2.14 (Win32)
Allow: GET,HEAD,POST,OPTIONS,TRACE
Content-Type: httpd/unix-directory
```

## Méthode TRACE

La méthode **TRACE** est utilisée pour renvoyer le contenu d'une requête HTTP au demandeur, ce qui peut être utilisé à des fins de débogage au moment du développement. L'exemple suivant montre l'utilisation de la méthode **TRACE** :

```http
TRACE / HTTP/1.1
Host: www.microlead.fr
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
```

Le serveur enverra le message suivant en réponse à la demande ci-dessus :

```http
HTTP/1.1 200 OK
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache/2.2.14 (Win32)
Connection: close
Content-Type: message/http
Content-Length: 39

TRACE / HTTP/1.1
Host: www.microlead.fr
User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT)
```
