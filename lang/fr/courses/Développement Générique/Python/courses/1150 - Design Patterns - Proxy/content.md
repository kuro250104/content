Le design pattern proxy inclut un nouvel objet, qui est appelé "Proxy" à la place d'un objet existant qui est appelé "Real Subject". L'objet proxy créé du sujet réel doit être sur la même interface de telle sorte que le client ne puisse pas se douter que le proxy est utilisé à la place de l'objet réel. Les requêtes générées par le client vers le proxy sont transmises par le sujet réel.

## Comment mettre en œuvre le modèle proxy ?

Voyons maintenant comment mettre en œuvre le modèle proxy.

```python
class Image:
    def __init__( self, filename ):
        self._filename = filename
    
    def load_image_from_disk( self ):
        print("loading " + self._filename)
    
    def display_image( self ):
        print("display " + self._filename)

class Proxy:
    def __init__( self, subject ):
        self._subject = subject
        self._proxystate = None

class ProxyImage( Proxy ):
    def display_image( self ):
        if self._proxystate == None:
            self._subject.load_image_from_disk()
            self._proxystate = 1
        print("display " + self._subject._filename)

proxy_image1 = ProxyImage(Image("HiRes_10Mb_Photo1"))
proxy_image2 = ProxyImage(Image("HiRes_10Mb_Photo2"))

proxy_image1.display_image() # loading necessary
proxy_image1.display_image() # loading unnecessary
proxy_image2.display_image() # loading necessary
proxy_image2.display_image() # loading unnecessary
proxy_image1.display_image() # loading unnecessary
```

## Résultat

Le programme ci-dessus génère le résultat suivant :

```bash
loading HiRes_10Mb_Photo1
display HiRes_10Mb_Photo1
display HiRes_10Mb_Photo1
loading HiRes_10Mb_Photo2
display HiRes_10Mb_Photo2
display HiRes_10Mb_Photo2
display HiRes_10Mb_Photo1
```

La conception du modèle proxy permet de reproduire les images que nous avons créées. La fonction ```display_image()``` permet de vérifier si les valeurs sont imprimées dans l'invite de commande.
