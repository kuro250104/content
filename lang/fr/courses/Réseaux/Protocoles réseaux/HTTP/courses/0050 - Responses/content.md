Après avoir reçu et interprété un message de demande, un serveur répond par un message de réponse HTTP :

- Une ligne d'état
- zéro ou plusieurs champs d'en-tête (Général|Réponse|Entité) suivis d'un CRLF
- Une ligne vide (c'est-à-dire une ligne où rien ne précède le CRLF) indiquant la fin des champs d'en-tête
- éventuellement, un corps de message.

Les sections suivantes expliquent chacune des entités utilisées dans un message de réponse HTTP.

## Ligne d'état des messages

Une ligne d'état se compose de la version du protocole suivie d'un code d'état numérique et de la phrase textuelle qui lui est associée. Les éléments sont séparés par des caractères d'espacement.

```http
Status-Line = HTTP-Version SP Status-Code SP Reason-Phrase CRLF
```

## Version de HTTP

Un serveur prenant en charge la version 1.1 du protocole HTTP renverra les informations suivantes sur la version :

```http
HTTP-Version = HTTP/1.1
```

## Code d'état

L'élément **Status-Code** est un nombre entier à 3 chiffres dont le premier définit la classe de la réponse et les deux derniers n'ont aucun rôle de catégorisation. Il existe 5 valeurs pour le premier chiffre :

- **1xx (Informatif)** - Cela signifie que la demande a été reçue et que le processus se poursuit.
- **2xx (Succès)** - Cela signifie que l'action a été reçue, comprise et acceptée avec succès.
- **3xx (Redirection)** - Cela signifie que d'autres actions doivent être entreprises afin de compléter la demande.
- **4xx (Erreur du client)** - Cela signifie que la demande contient une syntaxe incorrecte ou ne peut pas être satisfaite.
- **5xx (Erreur du serveur)** - Cela signifie que le serveur n'a pas réussi à répondre à une demande apparemment valide.

Les codes d'état HTTP sont extensibles et les applications HTTP ne sont pas tenues de comprendre la signification de tous les codes d'état enregistrés. Une liste de tous les codes d'état a été donnée dans un chapitre séparé pour votre référence.

## Champs d'en-tête de réponse

Nous étudierons General-header et Entity-header dans un chapitre séparé lorsque nous apprendrons les champs d'en-tête HTTP. Pour l'instant, vérifions ce que sont les champs d'en-tête de réponse.

Les champs d'en-tête de réponse permettent au serveur de transmettre des informations supplémentaires sur la réponse qui ne peuvent pas être placées dans la ligne d'état. Ces champs d'en-tête donnent des informations sur le serveur et sur l'accès ultérieur à la ressource identifiée par la Request-URI.

- Accept-Ranges
- Age
- ETag
- Location
- Proxy-Authenticate
- Retry-After
- Server
- Vary
- WWW-Authenticate

Vous pouvez introduire vos champs personnalisés dans le cas où vous allez écrire votre propre client et serveur Web personnalisé.

## Exemples de message de réponse

Maintenant, assemblons tout cela pour former une réponse HTTP pour une demande de récupération de la page **hello.htm** à partir du serveur web fonctionnant sur tutorialspoint.com.

```http
HTTP/1.1 200 OK
Date: Mon, 27 Jul 2009 12:28:53 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Wed, 22 Jul 2009 19:15:56 GMT
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

L'exemple suivant montre un message de réponse HTTP affichant une condition d'erreur lorsque le serveur web n'a pas pu trouver la page demandée :

```http
HTTP/1.1 404 Not Found
Date: Sun, 18 Oct 2012 10:36:20 GMT
Server: Apache/2.2.14 (Win32)
Content-Length: 230
Connection: Closed
Content-Type: text/html; charset=iso-8859-1
```

```html
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html>
<head>
    <title>404 Not Found</title>
</head>
<body>
    <h1>Not Found</h1>
    <p>The requested URL /t.html was not found on this server.</p>
</body>
</html>
```

Voici un exemple de message de réponse HTTP indiquant une condition d'erreur lorsque le serveur Web a rencontré une version HTTP incorrecte dans la demande HTTP donnée :

```http
HTTP/1.1 400 Bad Request
Date: Sun, 18 Oct 2012 10:36:20 GMT
Server: Apache/2.2.14 (Win32)
Content-Length: 230
Content-Type: text/html; charset=iso-8859-1
Connection: Closed
```

```html
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html>
<head>
    <title>400 Bad Request</title>
</head>
<body>
    <h1>Bad Request</h1>
    <p>Your browser sent a request that this server could not understand.</p>
    <p>The request line contained invalid characters following the protocol string.</p>
</body>
</html>
```