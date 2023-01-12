Dans ce modèle, les objets sont représentés comme des observateurs qui attendent le déclenchement d'un événement. Un observateur s'attache au sujet lorsque l'événement spécifié se produit. Lorsque l'événement se produit, le sujet informe les observateurs qu'il s'est produit.

## Comment mettre en œuvre le modèle observer ?

Voyons maintenant comment mettre en œuvre le modèle observer.

```python
import threading
import time
import pdb

class Downloader(threading.Thread):

    def run(self):
        print('downloading')
        for i in range(1,5):
            self.i = i
            time.sleep(2)
                print('unfunf')
            return 'hello world'

class Worker(threading.Thread):
    def run(self):
        for i in range(1,5):
            print('worker running: %i (%i)' % (i, t.i))
            time.sleep(1)
            t.join()

            print('done')

t = Downloader()
t.start()

time.sleep(1)

t1 = Worker()
t1.start()

t2 = Worker()
t2.start()

t3 = Worker()
t3.start()
```

## Résultat

Le programme ci-dessus génère le résultat suivant :

```bash
dowloading
worker running: 1 (1)worder running: 1(1)worker running: 1(1)

unfunf
worker running: 2 (4)worder running: 2(4)worker running: 2(4)

worker running: 3 (4)worder running: 3(4)worker running: 3(4)

worker running: 4 (4)worder running: 4(4)worker running: 4(4)

done
donedone
```

## Explication

Le code ci-dessus explique la procédure de téléchargement d'un résultat particulier. Selon la logique du modèle de l'observateur, chaque objet est traité comme un observateur. Il imprime la sortie lorsque l'événement est déclenché.
