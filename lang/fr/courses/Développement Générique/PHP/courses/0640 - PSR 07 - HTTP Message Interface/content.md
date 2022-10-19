Les messages HTTP sont à la base du développement Web. Les navigateurs Web et les clients HTTP tels que cURL créent des messages de requête HTTP qui sont envoyés à un serveur Web, qui fournit un message de réponse HTTP. Le code côté serveur reçoit un message de requête HTTP et renvoie un message de réponse HTTP.

Les messages HTTP sont généralement extraits du consommateur final, mais en tant que développeurs, nous avons généralement besoin de savoir comment ils sont structurés et comment y accéder ou les manipuler afin d'effectuer nos tâches, qu'il s'agisse de faire une demande à une API HTTP. , ou le traitement d'une demande entrante.

Chaque message de requête HTTP a une forme spécifique :

``` http
POST /path HTTP/1.1
Host: example.com

foo=bar&baz=bat
```

La première ligne d'une requête est la « ligne de requête » et contient, dans l'ordre, la méthode de requête HTTP, la cible de la requête (généralement un URI absolu ou un chemin sur le serveur Web) et la version du protocole HTTP. Ceci est suivi d'un ou plusieurs en-têtes HTTP, d'une ligne vide et du corps du message.

Les messages de réponse HTTP ont une structure similaire :

``` http
HTTP/1.1 200 OK
Content-Type: text/plain
```

La première ligne est la “ligne d'état” et contient, dans l'ordre, la version du protocole HTTP, le code d'état HTTP et une "phrase de raison", une description lisible par l'homme du code d'état. Comme le message de requête, il est ensuite suivi d'un ou plusieurs en-têtes HTTP, d'une ligne vide et du corps du message.

Les interfaces décrites dans ce document sont des abstractions autour des messages HTTP et des éléments qui les composent.

## Les messages

Un message HTTP est soit une requête d'un client à un serveur, soit une réponse d'un serveur à un client. Cette spécification définit les interfaces pour les messages HTTP ```Psr\Http\Message\RequestInterface``` et ```Psr\Http\Message\ResponseInterface``` respectivement.

Les deux ```Psr\Http\Message\RequestInterface``` et ```Psr\Http\Message\ResponseInterface``` étendent ```Psr\Http\Message\MessageInterface```. Bien que ```Psr\Http\Message\MessageInterface``` peuvent être implémentés directement, les implémenteurs doivent être implémenter ```Psr\Http\Message\RequestInterface``` et ```Psr\Http\Message\ResponseInterface```.

À partir de maintenant, l'espace de noms ```Psr\Http\Message``` sera omis lors de la référence à ces interfaces.

## Les en-têtes

Les messages HTTP incluent des noms de champs d'en-tête insensibles à la casse. Les en-têtes sont récupérés par nom à partir des classes implémentant le ```MessageInterface``` d'une manière insensible à la casse. Par exemple, la récupération de l'en-tête ```Foo``` renverra le même résultat que la récupération de l'en-tête ```Foo```. De même, la définition de l'en-tête ```Foo``` écrasera toute valeur d'en-tête précédemment définie.

exemple :

``` php
$message = $message->withHeader('foo', 'bar');

echo $message->getHeaderLine('foo');

echo $message->getHeaderLine('FOO');

$message = $message->withHeader('fOO', 'baz');
echo $message->getHeaderLine('foo');
```

Bien que les en-têtes puissent être récupérés sans tenir compte de la casse, la casse d'origine doit être préservée par la mise en œuvre, en particulier lorsqu'elle est récupérée avec ```getHeaders()```.

Les applications HTTP non conformes peuvent dépendre d'un certain cas, il est donc utile pour un utilisateur de pouvoir dicter la casse des en-têtes HTTP lors de la création d'une demande ou d'une réponse.

Afin de prendre en charge les en-têtes avec plusieurs valeurs tout en offrant la commodité de travailler avec des en-têtes sous forme de chaînes, les en-têtes peuvent être récupérés à partir d'une instance de a ```MessageInterface``` sous forme de tableau ou de chaîne. Utilisez la ```getHeaderLine()``` méthode pour récupérer une valeur d'en-tête sous forme de chaîne contenant toutes les valeurs d'en-tête d'un en-tête insensible à la casse par nom concaténé avec une virgule. Utilisez ```getHeader()``` pour récupérer un tableau de toutes les valeurs d'en-tête pour un en-tête particulier insensible à la casse par nom.

exemple :

``` php
$message = $message
    ->withHeader('foo', 'bar')
    ->withAddedHeader('foo', 'baz');

$header = $message->getHeaderLine('foo');

$header = $message->getHeader('foo');
```

Remarque : toutes les valeurs d'en-tête ne peuvent pas être concaténées à l'aide d'une virgule (par exemple, ```Set-Cookie```). Lorsqu'ils travaillent avec de tels en-têtes, les consommateurs des classes basées sur ```MessageInterface``` devraient s'appuyer sur la méthode ```getHeader()``` pour récupérer ces en-têtes à valeurs multiples.

Dans les requêtes, l'en-tête reflète généralement le composant hôte de l'URI, ainsi que l'hôte utilisé lors de l'établissement de la connexion TCP. Cependant, la spécification HTTP permet à l'en-tête de différer de chacun des deux.

Pendant la construction, les mises en œuvre doivent tenter de définir l'en-tête à partir d'un URI fourni si aucun en-tête n'est fourni.

```RequestInterface::withUri()``` remplacera, par défaut, l'en-tête de la requête envoyée par un en-tête correspondant au composant hôte du fichier ```UriInterface```.

Vous pouvez choisir de conserver l'état d'origine de l'en-tête en passant ```true``` en deuxième argument (```$preserveHost```). Lorsque cet argument est défini à “true”, la demande renvoyée ne mettra pas à jour l'en-tête du message renvoyé, à moins que le message ne contient aucun en-tête.

Les messages HTTP se composent d'une ligne de départ, d'en-têtes et d'un corps. Le corps d'un message HTTP peut être très petit ou extrêmement grand. Tenter de représenter le corps d'un message sous forme de chaîne peut facilement consommer plus de mémoire que prévu, car le corps doit être entièrement stocké en mémoire. Tenter de stocker le corps d'une demande ou d'une réponse en mémoire empêcherait l'utilisation de cette implémentation de pouvoir travailler avec des corps de message volumineux. ```StreamInterface``` est utilisé afin de masquer les détails de l'implémentation lorsqu'un flux de données est lu ou écrit. Pour les situations où une chaîne serait une implémentation de messages appropriés, des flux intégrés tels que ```php://memory``` et ```php://temp``` peuvent être utilisés.

```StreamInterface``` expose plusieurs méthodes qui permettent de lire, d'écrire et de traverser efficacement les flux.

Les flux exposent leurs capacités à l'aide de trois méthodes : ```isReadable()```, ```isWritable()```, et ```isSeekable()```. Ces méthodes peuvent être utilisées par les collaborateurs du flux pour déterminer si un flux est capable de répondre à leurs besoins.

Chaque instance de flux aura différentes capacités : elle peut être en lecture seule, en écriture seule ou en lecture-écriture. Il peut également autoriser un accès aléatoire arbitraire (recherche vers l'avant ou l'arrière vers n'importe quel emplacement), ou uniquement un accès séquentiel (par exemple dans le cas d'un socket, d'un tuyau ou d'un flux basé sur un rappel).

Enfin, ```StreamInterface``` définit une ```__toString()``` méthode pour simplifier la récupération ou l'émission de tout le contenu du corps à la fois.

Contrairement aux interfaces de requête et de réponse, ```StreamInterface``` ne modélise pas l'immuabilité. Dans les situations où un flux PHP réel est encapsulé, l'immuabilité est impossible à appliquer, car tout code qui interagit avec la ressource peut potentiellement changer son état (y compris la position du curseur, le contenu, etc.). Notre recommandation est que les implémentations utilisent des flux en lecture seule pour les demandes côté serveur et les réponses côté client. Les consommateurs doivent être conscients du fait que l'instance de flux peut être modifiable et, en tant que telle, pourrait modifier l'état du message ; en cas de doute, créez une nouvelle instance de flux et attachez-la à un message pour appliquer l'état.

## Les cibles de requête et URI

Selon la RFC 7230, les messages de demande contiennent une « cible de demande » comme deuxième segment de la ligne de demande. La cible de la demande peut être l'une des formes suivantes :

- **origin-form**, qui se compose du chemin et, le cas échéant, de la chaîne de requête ; c'est ce qu'on appelle souvent une URL relative. Les messages tels qu'ils sont transmis sur TCP sont généralement de la forme d'origine ; les données de schéma et d'autorité ne sont généralement présentes que via les variables CGI.
- **absolute-form**, qui comprend le schéma, l'autorité (```[user-info@]host[:port]```, où les éléments entre crochets sont facultatifs), le chemin (le cas échéant), la chaîne de requête (le cas échéant) et le fragment ( si présent). Il s'agit souvent d'un URI absolu, et c'est le seul formulaire permettant de spécifier un URI tel que détaillé dans la RFC 3986. Ce formulaire est couramment utilisé lors des demandes de proxy HTTP.
- **author-form**, qui se compose uniquement de l'autorité. Ceci est généralement utilisé dans les requêtes CONNECT uniquement, pour établir une connexion entre un client HTTP et un serveur proxy.
- **asterisk-form**, qui se compose uniquement de la chaîne ```*```, et qui est utilisé avec la méthode OPTIONS pour déterminer les capacités générales d'un serveur Web.

En dehors de ces cibles de requête, il existe souvent une « URL effective » qui est distincte de la cible de la requête. L'URL effective n'est pas transmise dans un message HTTP, mais elle est utilisée pour déterminer le protocole (http / https), le port et le nom d'hôte pour effectuer la demande.

L'URL effective est représentée par” UriInterface”. “UriInterface” modélise les URI HTTP et HTTPS comme spécifié dans la RFC 3986 (le cas d'utilisation principal). L'interface fournit des méthodes pour interagir avec les différentes parties d'URI, ce qui évitera le besoin d'analyses répétées de l'URI. Il spécifie également une ```__toString()``` méthode pour convertir l'URI modélisé en sa représentation sous forme de chaîne.

Lors de la récupération de la cible de la requête avec ```getRequestTarget()```, cette méthode utilisera par défaut l'objet URI et ensuite il extrait tous les composants nécessaires pour construire la forme d'origine . Le formulaire d'origine est de loin la cible de requête la plus courante.

Si un utilisateur final souhaite utiliser l'une des trois autres formes, ou si l'utilisateur souhaite explicitement écraser la cible de la requête, il est possible de le faire avec ```withRequestTarget()```.

L'appel de cette méthode n'affecte pas l'URI, car il est renvoyé par ```getUri()```.

Par exemple, un utilisateur peut souhaiter envoyer une requête sous forme d'astérisque à un serveur :

``` php
$request = $request
    ->withMethod('OPTIONS')
    ->withRequestTarget('*')
    ->withUri(new Uri('https://example.org/'));
```

Cet exemple peut finalement aboutir à une requête HTTP qui ressemble à ceci :

``` http
OPTIONS * HTTP/1.1
```

Mais le client HTTP pourra utiliser l'URL effective (de “getUri()”), pour déterminer le protocole, le nom d'hôte et le port TCP.

Un client HTTP soit ignorer les valeurs de ```Uri::getPath()``` et ```Uri::getQuery()```, et utiliser à la place la valeur renvoyée par ```getRequestTarget()```, qui par défaut concaténera ces deux valeurs.

Les clients qui choisissent de ne pas implémenter 1 ou plusieurs des 4 formulaires cible de demande, doivent toujours utiliser ```getRequestTarget()```. Ces clients doivent rejeter les cibles de demande qu'ils ne prennent pas en charge, et ne doivent pas se rabattre sur les valeurs de ```getUri()```.

```RequestInterface``` fournit des méthodes pour récupérer la cible de requête ou créer une nouvelle instance avec la cible de requête fournie. Par défaut, si aucune requête-cible n'est spécifiquement composée dans l'instance, ```getRequestTarget()``` renverra la forme d'origine de l'URI composé (ou "/" si aucun URI n'est composé). ```withRequestTarget($requestTarget)``` crée une nouvelle instance avec la cible de demande spécifiée et permet ainsi aux développeurs de créer des messages de demande qui représentent les trois autres formes de cible de demande (forme absolue, forme d'autorité et forme astérisque). Lorsqu'elle est utilisée, l'instance d'URI composée peut toujours être utile, en particulier chez les clients, où elle peut être utilisée pour créer la connexion au serveur.

## Les requêtes côté serveur

```RequestInterface``` fournit la représentation générale d'un message de requête HTTP. Cependant, les demandes côté serveur nécessitent un traitement supplémentaire, en raison de la nature de l'environnement côté serveur. Le traitement côté serveur doit prendre en compte la Common Gateway Interface (CGI) et, plus précisément, l'abstraction et l'extension de CGI par PHP via ses API de serveur (SAPI). PHP a fourni une simplification autour du marshaling d'entrée via des superglobaux tels que :

- ```$_COOKIE```, qui désérialise et fournit un accès simplifié aux cookies HTTP.
- ```$_GET```, qui désérialise et fournit un accès simplifié aux arguments de chaîne de requête.
- ```$_POST```, qui désérialise et fournit un accès simplifié pour les paramètres codés en URL soumis via HTTP POST ; de manière générique, il peut être considéré comme le résultat de l'analyse du corps du message.
- ```$_FILES```, qui fournit des métadonnées sérialisées autour des téléchargements de fichiers.
- ```$_SERVER```, qui permet d'accéder aux variables d'environnement CGI/SAPI, qui incluent généralement la méthode de requête, le schéma de requête, l'URI de requête et les en-têtes.

```ServerRequestInterface``` s'étend ```RequestInterface``` pour fournir une abstraction autour de ces différents superglobaux. Cette pratique permet de réduire le couplage aux superglobales par les consommateurs et encourage et promeut la capacité de tester les consommateurs à la demande.

La demande du serveur fournit une propriété supplémentaire, "attributs", pour permettre aux consommateurs de décomposer et de faire correspondre la demande à des règles spécifiques à l'application (telles que la correspondance de chemin, la correspondance de schéma, la correspondance d'hôte, etc.). En tant que telle, la demande de serveur peut également fournir une messagerie entre plusieurs consommateurs de demande.

## Les fichiers téléchargés

```ServerRequestInterface``` spécifie une méthode pour récupérer une arborescence de fichiers de téléchargement dans une structure normalisée, avec chaque feuille une instance de ```UploadedFileInterface```.

Le ```$_FILES``` superglobal a des problèmes bien connus lorsqu'il traite des tableaux d'entrées de fichiers. Par exemple, si vous avez un formulaire qui soumet un tableau de fichiers - par exemple, le nom d'entrée "files", soumettre ```files[0]``` et ```files[1]``` - PHP le représentera comme :

``` php
array(
    'files' => array(
        'name' => array(
            0 => 'file0.txt',
            1 => 'file1.html',
        ),
        'type' => array(
            0 => 'text/plain',
            1 => 'text/html',
        ),
    ),
)
```

Au lieu de l’attendu :

``` php
array(
    'files' => array(
        0 => array(
            'name' => 'file0.txt',
            'type' => 'text/plain',
        ),
        1 => array(
            'name' => 'file1.html',
            'type' => 'text/html',
        ),
    ),
)
```

Le résultat est que les consommateurs ont besoin de connaître ces détails d'implémentation du langage et d'écrire du code pour collecter les données pour un téléchargement donné.

De plus, il existe des scénarios où ```$_FILES``` n'est pas renseigné lorsque des téléchargements de fichiers se produisent :

- Lorsque la méthode HTTP n'est pas “POST”.
- Lors des tests unitaires.
- Lorsque vous travaillez dans un environnement non SAPI, tel que ReactPHP.

Dans de tels cas, les données devront être ensemencées différemment. A titre d'exemples :

- Un processus peut analyser le corps du message pour découvrir les téléchargements de fichiers. Dans de tels cas, l'implémentation peut choisir de ne pas écrire les téléchargements de fichiers dans le système de fichiers, mais de les envelopper dans un flux afin de réduire la mémoire, les E/S et la surcharge de stockage.
- Dans les scénarios de test unitaire, les développeurs doivent être en mesure de stub et/ou de simuler les métadonnées de téléchargement de fichier afin de valider et de vérifier différents scénarios.

```getUploadedFiles()``` fournit la structure normalisée pour les consommateurs. Les implémentations devraient :

- Regroupez toutes les informations pour un téléchargement de fichier donné et utilisez-les pour remplir une ```Psr\Http\Message\UploadedFileInterface``` instance.
- Recréez la structure arborescente soumise, chaque feuille étant l' ```Psr\Http\Message\UploadedFileInterface``` instance appropriée pour l'emplacement donné dans l'arborescence.

L'arborescence référencée doit imiter la structure de nommage dans laquelle les fichiers ont été soumis.

Dans l'exemple le plus simple, il peut s'agir d'un seul élément de formulaire nommé soumis en tant que :

``` html
<input type="file" name="avatar" />
```

Dans ce cas, la structure dans ```$_FILES``` ressemblerait à :

``` php
array(
    'avatar' => array(
        'tmp_name' => 'phpUxcOty',
        'name' => 'my-avatar.png',
        'size' => 90996,
        'type' => 'image/png',
        'error' => 0,
    ),
)
```

La forme normalisée renvoyée par ```getUploadedFiles()``` serait :

``` php
array(
    'avatar' => /* UploadedFileInterface instance */
)
```

Dans le cas d'une entrée utilisant la notation matricielle pour le nom :

``` html
<input type="file" name="my-form[details][avatar]" />
```

```$_FILES``` finit par ressembler à ça :

``` php
array (
    'my-form' => array (
        'name' => array (
            'details' => array (
                'avatar' => 'my-avatar.png',
            ),
        ),
        'type' => array (
            'details' => array (
                'avatar' => 'image/png',
            ),
        ),
        'tmp_name' => array (
            'details' => array (
                'avatar' => 'phpmFLrzD',
            ),
        ),
        'error' => array (
            'details' => array (
                'avatar' => 0,
            ),
        ),
        'size' => array (
            'details' => array (
                'avatar' => 90996,
            ),
        ),
    ),
)
```

Et l'arbre correspondant renvoyé par ```getUploadedFiles()``` devrait être :

``` php
array(
    'my-form' => array(
        'details' => array(
            'avatar' => /* UploadedFileInterface instance */
        ),
    ),
)
```

Dans certains cas, vous pouvez spécifier un tableau de fichiers :

``` html
<input type="file" name="my-form[details][avatars][]" />
<input type="file" name="my-form[details][avatars][]" />
```

(Par exemple, les contrôles JavaScript peuvent générer des entrées de téléchargement de fichiers supplémentaires pour permettre le téléchargement de plusieurs fichiers à la fois.)

Dans un tel cas, l'implémentation de la spécification doit agréger toutes les informations relatives au fichier à l'index donné. La raison en est que ```$_FILES``` s'écarte de sa structure normale dans de tels cas :

``` php
array (
    'my-form' => array (
        'name' => array (
            'details' => array (
                'avatars' => array (
                    0 => 'my-avatar.png',
                    1 => 'my-avatar2.png',
                    2 => 'my-avatar3.png',
                ),
            ),
        ),
        'type' => array (
            'details' => array (
                'avatars' => array (
                    0 => 'image/png',
                    1 => 'image/png',
                    2 => 'image/png',
                ),
            ),
        ),
        'tmp_name' => array (
            'details' => array (
                'avatars' => array (
                    0 => 'phpmFLrzD',
                    1 => 'phpV2pBil',
                    2 => 'php8RUG8v',
                ),
            ),
        ),
        'error' => array (
            'details' => array (
                'avatars' => array (
                    0 => 0,
                    1 => 0,
                    2 => 0,
                ),
            ),
        ),
        'size' => array (
            'details' => array (
                'avatars' => array (
                    0 => 90996,
                    1 => 90996,
                    3 => 90996,
                ),
            ),
        ),
    ),
)
```

Le ```$_FILES``` tableau ci-dessus correspond à la structure suivante telle que renvoyée par ```getUploadedFiles()``` :

``` php
array(
    'my-form' => array(
        'details' => array(
            'avatars' => array(
                0 => /* UploadedFileInterface instance */,
                1 => /* UploadedFileInterface instance */,
                2 => /* UploadedFileInterface instance */,
            ),
        ),
    ),
)
```

Les consommateurs accéderont à l'index 1 du tableau imbriqué en utilisant :

``` php
$request->getUploadedFiles()['my-form']['details']['avatars'][1];
```

Étant donné que les données des fichiers téléchargés sont dérivées (dérivées de ```$_FILES``` ou du corps de la requête), une méthode de mutateur, ```withUploadedFiles()```, est également présente dans l'interface, permettant la délégation de la normalisation à un autre processus.

Dans le cas des exemples originaux, la consommation ressemble à ce qui suit :

``` php
$file0 = $request->getUploadedFiles()['files'][0];
$file1 = $request->getUploadedFiles()['files'][1];

printf(
    $file0->getClientFilename(),
    $file1->getClientFilename()
);
```

Cette proposition reconnaît également que les mises en œuvre peuvent fonctionner dans des environnements non SAPI. En tant que tel, “UploadedFileInterface” fournit des méthodes pour garantir que les opérations fonctionnent quel que soit l'environnement. En particulier :

- ```moveTo($targetPath)``` est fourni comme une alternative sûre et recommandée à l'appel ```move_uploaded_file()``` direct sur le fichier de téléchargement temporaire. Les implémentations détectent l'opération correcte à utiliser en fonction de l'environnement.
- ```getStream()``` retournera une instance de ```StreamInterface```. Dans les environnements non SAPI, une possibilité proposée est d'analyser les fichiers de téléchargement individuels dans des flux ```php://temp``` au lieu de directement dans des fichiers ; dans de tels cas, aucun fichier de téléchargement n'est présent. ```getStream()``` est donc garanti de fonctionner quel que soit l'environnement.

A titre d'exemple :

``` php
$filename = sprintf(
    '%s.%s',
    create_uuid(),
    pathinfo($file0->getClientFilename(), PATHINFO_EXTENSION)
);
$file0->moveTo(DATA_DIR . '/' . $filename);

$stream = new Psr7StreamWrapper($file1->getStream());
stream_copy_to_stream($stream, $s3wrapper);
```

## Les interfaces

“MessageInterface” :

``` php
<?php
namespace Psr\Http\Message;

interface MessageInterface
{
    /**
     * @return string
     */
    public function getProtocolVersion();

    /**
     * @param string
     * @return static
     */
    public function withProtocolVersion($version);

    /**
     * @return string[]
     */
    public function getHeaders();

    /**
     * @param string $name
     * @return bool
     */
    public function hasHeader($name);

    /**
     * @param string $name 
     * @return string[]
     */
    public function getHeader($name);

    /**
     * @param string $name 
     * @return string
     */
    public function getHeaderLine($name);

    /**
     * @param string $name
     * @param string|string[]
     * @return static
     * @throws \InvalidArgumentException
     */
    public function withHeader($name, $value);

    /**
     * @param string $name
     * @param string|string[] 
     * @return static
     * @throws \InvalidArgumentException
     * @throws \InvalidArgumentException
     */
    public function withAddedHeader($name, $value);

    /**
     * @param string $name
     * @return static
     */
    public function withoutHeader($name);

    /**
     * @return StreamInterface Returns the body as a stream.
     */
    public function getBody();

    /**
     * @param StreamInterface $body Body.
     * @return static
     * @throws \InvalidArgumentException
     */
    public function withBody(StreamInterface $body);
}
```

“RequestInterface” :

``` php
<?php
namespace Psr\Http\Message;

interface RequestInterface extends MessageInterface
{
    /**
     * @return string
     */
    public function getRequestTarget();

    /**
     * @param mixed $requestTarget
     * @return static
     */
    public function withRequestTarget($requestTarget);

    /**
     * @return string
     */
    public function getMethod();

    /**
     * @param string $method
     * @return static
     * @throws \InvalidArgumentException
     */
    public function withMethod($method);

    /**
     * @return UriInterface 
     */
    public function getUri();

    /**
     * @param UriInterface $uri
     * @param bool $preserveHost
     * @return static
     */
    public function withUri(UriInterface $uri, $preserveHost = false);
}
```

“ServerRequestInterface” :

``` php
<?php
namespace Psr\Http\Message;

interface ServerRequestInterface extends RequestInterface
{
    /**
     * @return array
     */
    public function getServerParams();

    /**
     * @return array
     */
    public function getCookieParams();

    /**
     * @param array $cookies
     * @return static
     */
    public function withCookieParams(array $cookies);

    /**
     * @return array
     */
    public function getQueryParams();

    /**
     * @param array $query
     * @return static
     */
    public function withQueryParams(array $query);

    /**
     * @return array
     */
    public function getUploadedFiles();

    /**
     * @param array
     * @return static
     * @throws \InvalidArgumentException
     */
    public function withUploadedFiles(array $uploadedFiles);

    /**
     * @return null|array|object
     */
    public function getParsedBody();

    /**
     * @param null|array|object
     * @return static
     * @throws \InvalidArgumentException
     */
    public function withParsedBody($data);

    /**
     * @return mixed[] 
     */
    public function getAttributes();

    /**
     * @param string $name
     * @param mixed $default
     * @return mixed
     */
    public function getAttribute($name, $default = null);

    /**
     * @param string $name
     * @param mixed $value
     * @return static
     */
    public function withAttribute($name, $value);

    /**
     * @param string $name
     * @return static
     */
    public function withoutAttribute($name);
}
```

“ResponseInterface” :

``` php
<?php
namespace Psr\Http\Message;

interface ResponseInterface extends MessageInterface
{
    /**
     * @return int
     */
    public function getStatusCode();

    /**
     * @param int $code
     * @param string $reasonPhrase
     * @return static
     * @throws \InvalidArgumentException
     */
    public function withStatus($code, $reasonPhrase = '');

    /**
     * @return string
     */
    public function getReasonPhrase();
}
```

“StreamInterface” :

``` php
<?php
namespace Psr\Http\Message;

interface StreamInterface
{
    /**
     * @return string
     */
    public function __toString();

    /**
     * @return void
     */
    public function close();

    /**
     * @return resource|null
     */
    public function detach();

    /**
     * @return int|null
     */
    public function getSize();

    /**
     * @return int
     * @throws \RuntimeException
     */
    public function tell();

    /**
     * @return bool
     */
    public function eof();

    /**
     * @return bool
     */
    public function isSeekable();

    /**
     * @param int $offset
     * @param int $whence
     * @throws \RuntimeException
     */
    public function seek($offset, $whence = SEEK_SET);

    /**
     * @throws \RuntimeException
     */
    public function rewind();

    /**
     * @return bool
     */
    public function isWritable();

    /**
     * @param string $string
     * @return int
     * @throws \RuntimeException
     */
    public function write($string);

    /**
     * @return bool
     */
    public function isReadable();

    /**
     * @param int $length
     * @return string
     * @throws \RuntimeException
     */
    public function read($length);

    /**
     * @return string
     * @throws \RuntimeException
     * @throws \RuntimeException 
     */
    public function getContents();

    /**
     * @param string $key
     * @return array|mixed|null
     */
    public function getMetadata($key = null);
}
```

“UriInterface” :

``` php
<?php
namespace Psr\Http\Message;

interface UriInterface
{
    /**
     * @return string
     */
    public function getScheme();

    /**
     * @return string
     */
    public function getAuthority();

    /**
     * @return string
     */
    public function getUserInfo();

    /**
     * @return string
     */
    public function getHost();

    /**
     * @return null|int
     */
    public function getPort();

    /**
     * @return string
     */
    public function getPath();

    /**
     * @return string
     */
    public function getQuery();

    /**
     * @return string
     */
    public function getFragment();

    /**
     * @param string $scheme
     * @return static
     * @throws \InvalidArgumentException
     * @throws \InvalidArgumentException
     */
    public function withScheme($scheme);

    /**
     * @param string $user
     * @param null|string $password
     * @return static
     */
    public function withUserInfo($user, $password = null);

    /**
     * @param string $host
     * @return static
     * @throws \InvalidArgumentException
     */
    public function withHost($host);

    /**
     * @param null|int $port
     * @return static
     * @throws \InvalidArgumentException
     */
    public function withPort($port);

    /**
     * @param string $path
     * @return static
     * @throws \InvalidArgumentException
     */
    public function withPath($path);

    /**
     * @param string $query
     * @return static
     * @throws \InvalidArgumentException
     */
    public function withQuery($query);

    /**
     * @param string $fragment
     * @return static 
     */
    public function withFragment($fragment);

    /**
     * @return string
     */
    public function __toString();
}
```

“UploadedFileInterface” :

``` php
<?php
namespace Psr\Http\Message;

interface UploadedFileInterface
{
    /**
     * @return StreamInterface
     * @throws \RuntimeException
     * @throws \RuntimeException
     */
    public function getStream();

    /**
     * @param string $targetPath
     * @throws \InvalidArgumentException
     * @throws \RuntimeException 
     * @throws \RuntimeException
     */
    public function moveTo($targetPath);

    /**
     * @return int|null
     */
    public function getSize();

    /**
     * @return int
     */
    public function getError();

    /**
     * @return string|null
     */
    public function getClientFilename();

    /**
     * @return string|null
     */
    public function getClientMediaType();
}
```