Une HTTP factory est une méthode par laquelle un nouvel objet HTTP, tel que défini par PSR-7, est créé. Les factory HTTP doivent implémenter ces interfaces pour chaque type d'objet fourni par le package.

## Les interfaces

Les interfaces suivantes peuvent être mises en œuvre ensemble au sein d'une même classe ou dans des classes distinctes.

“RequestFactoryInterface” :

```php
namespace Psr\Http\Message;

use Psr\Http\Message\RequestInterface;
use Psr\Http\Message\UriInterface;

interface RequestFactoryInterface
{
    /**
     * Créer une nouvelle requête
     *
     * @param string $method la méthode Http est associé à la requête 
     * @param UriInterface|string $uri Uri associé à la requête
     */
    public function createRequest(string $method, $uri): RequestInterface;
}
```

“ResponseFactoryInterface” :

```php
namespace Psr\Http\Message;

use Psr\Http\Message\ResponseInterface;

interface ResponseFactoryInterface
{
    /**
     * créer une nouvelle réponse
     *
     * @param int $code le status code Http est par défaut 200
     * @param string $reasonPhrase phrase associé avec le status code              qui génère une réponse 
     */
    public function createResponse(int $code = 200, string $reasonPhrase = ''): ResponseInterface;
}
```

“ServerRequestFactoryInterface” :

```php
namespace Psr\Http\Message;

use Psr\Http\Message\ServerRequestInterface;
use Psr\Http\Message\UriInterface;

interface ServerRequestFactoryInterface
{
    /**
     * @param string $method méthode Http associé à la requête
     * @param UriInterface|string $uri Uri associé à la requête
     * @param array $serverParams
     */
    public function createServerRequest(string $method, $uri, array $serverParams = []): ServerRequestInterface;
}
```

“StreamFactoryInterface” :

```php
namespace Psr\Http\Message;

use Psr\Http\Message\StreamInterface;

interface StreamFactoryInterface
{
    /**
     * @param string $content
     */
    public function createStream(string $content = ''): StreamInterface;

    /**
     * @param string $filename
     * @param string $mode
     * @throws \RuntimeException
     * @throws \InvalidArgumentException
     */
    public function createStreamFromFile(string $filename, string $mode = 'r'): StreamInterface;

    /**
     * @param resource $resource
     */
    public function createStreamFromResource($resource): StreamInterface;
}
```

“UploadedFileFactoryInterface” :

```php
namespace Psr\Http\Message;

use Psr\Http\Message\StreamInterface;
use Psr\Http\Message\UploadedFileInterface;

interface UploadedFileFactoryInterface
{
    /**
     * @param StreamInterface $stream
     * @param int $size
     * @param int $error
     * @param string $clientFilename
     * @param string $clientMediaType
     * @throws \InvalidArgumentException
     */
    public function createUploadedFile(
        StreamInterface $stream,
        int $size = null,
        int $error = \UPLOAD_ERR_OK,
        string $clientFilename = null,
        string $clientMediaType = null
    ): UploadedFileInterface;
}
```

“UriFactoryInterface” :

```php
namespace Psr\Http\Message;

use Psr\Http\Message\UriInterface;

interface UriFactoryInterface
{
    /**
     * @param string $uri
     * @throws \InvalidArgumentException
     */
    public function createUri(string $uri = '') : UriInterface;
}
```