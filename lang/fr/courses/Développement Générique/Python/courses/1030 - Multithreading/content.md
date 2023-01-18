L'exécution de plusieurs threads est similaire à l'exécution simultanée de plusieurs programmes différents, mais avec les avantages suivants :

- Plusieurs threads au sein d'un processus partagent le même espace de données avec le thread principal et peuvent donc partager des informations ou communiquer entre eux plus facilement que s'il s'agissait de processus distincts.
- Les threads sont parfois appelés processus légers et ils ne nécessitent pas beaucoup de mémoire ; ils sont moins chers que les processus.

Un thread a un début, une séquence d'exécution et une conclusion. Il possède un pointeur d'instruction qui permet de savoir où, dans son contexte, il s'exécute actuellement.

- Il peut être préempté (interrompu).
- Il peut être temporairement mis en attente (aussi appelé "sleeping") pendant que d'autres threads sont en cours d'exécution - c'est ce qu'on appelle le yielding.

Il existe deux types de threads différents

- le thread du noyau
- thread utilisateur

Les threads du noyau font partie du système d'exploitation, tandis que les threads de l'espace utilisateur ne sont pas implémentés dans le noyau.

Il y a deux modules qui supportent l'utilisation des threads dans Python3 :

- _thread
- threading

Le module thread est "déprécié" depuis un certain temps. Les utilisateurs sont encouragés à utiliser le module threading à la place. Par conséquent, dans Python 3, le module "thread" n'est plus disponible. Cependant, il a été renommé en "_thread" pour des raisons de compatibilité avec Python 3.

## Démarrer un nouveau fil de discussion

Pour créer un autre thread, vous devez appeler la méthode suivante disponible dans le module thread :

```python
_thread.start_new_thread(function, args[, kwargs])
```

Cet appel de méthode constitue un moyen rapide et efficace de créer de nouveaux threads sous Linux et Windows.

L'appel de méthode revient immédiatement et le thread enfant démarre et appelle la fonction avec la liste d'arguments passée. Lorsque la fonction revient, le thread se termine.

Ici, args est un tuple d'arguments ; utilisez un tuple vide pour appeler la fonction sans passer d'arguments. kwargs est un dictionnaire optionnel d'arguments de mots-clés.

### Exemple

```python
#!/usr/bin/python3

import _thread
import time

# Define a function for the thread
def print_time(threadName, delay):
    count = 0
    while count < 5:
        time.sleep(delay)
        count += 1
        print("%s: %s" % (threadName, time.ctime(time.time())))

# Create two threads as follows
try:
    _thread.start_new_thread(print_time, ("Thread-1", 2, ))
    _thread.start_new_thread(print_time, ("Thread-2", 4, ))
except:
    print("Error: unable to start thread")

while 1:
    pass
```

### Résultat

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Thread-1: Fri Feb 19 09:41:39 2016
Thread-2: Fri Feb 19 09:41:41 2016
Thread-1: Fri Feb 19 09:41:41 2016
Thread-1: Fri Feb 19 09:41:43 2016
Thread-2: Fri Feb 19 09:41:45 2016
Thread-1: Fri Feb 19 09:41:45 2016
Thread-1: Fri Feb 19 09:41:47 2016
Thread-2: Fri Feb 19 09:41:49 2016
Thread-2: Fri Feb 19 09:41:53 2016
```

Le programme entre dans une boucle infinie. Vous devrez appuyer sur ctrl-c pour l'arrêter.

Bien qu'il soit très efficace pour le threading de bas niveau, le module thread est très limité par rapport au module de threading plus récent.

## Le module Threading

Le nouveau module threading inclus dans Python 2.4 offre une prise en charge de haut niveau des threads beaucoup plus puissante que le module thread présenté dans la section précédente.

Le module threading expose toutes les méthodes du module thread et fournit quelques méthodes supplémentaires :

- ```threading.activeCount()``` − Renvoie le nombre d'objets threads qui sont actifs.
- ```threading.currentThread()``` − Renvoie le nombre d'objets threads dans le contrôle de threads de l'appelant.
- ```threading.enumerate()``` − Renvoie une liste de tous les objets threads qui sont actuellement actifs.

En plus des méthodes, le module threading possède la classe Thread qui implémente le threading. Les méthodes fournies par la classe Thread sont les suivantes :

- ```run()``` - La méthode ```run()``` est le point d'entrée d'un thread.
- ```start()``` - La méthode ```start()``` démarre un thread en appelant la méthode run.
- ```join([time])``` - La méthode ```join()``` attend que les threads se terminent.
- ```isAlive()``` - La méthode ```isAlive()``` vérifie si un thread est toujours en cours d'exécution.
- ```getName()``` - La méthode ```getName()``` retourne le nom d'un thread.
- ```setName()``` - La méthode ```setName()``` définit le nom d'un thread.

## Création d'un fil à l'aide du module Threading

Pour implémenter un nouveau thread à l'aide du module threading, vous devez procéder comme suit :

- Définissez une nouvelle sous-classe de la classe Thread.
- Remplacez la méthode ```__init__(self [,args])``` pour ajouter des arguments supplémentaires.
- Ensuite, remplacez la méthode ```run(self [,args])``` pour implémenter ce que le thread doit faire lorsqu'il est lancé.

Une fois que vous avez créé la nouvelle sous-classe ```Thread```, vous pouvez créer une instance de celle-ci, puis démarrer un nouveau thread en invoquant la méthode ```start()```, qui à son tour appelle la méthode ```run()```.

### Example

```python
#!/usr/bin/python3

import threading
import time

exitFlag = 0

class myThread (threading.Thread):
    def __init__(self, threadID, name, counter):
        threading.Thread.__init__(self)
        self.threadID = threadID
        self.name = name
        self.counter = counter
    def run(self):
        print("Starting " + self.name)
        print_time(self.name, self.counter, 5)
        print("Exiting " + self.name)

def print_time(threadName, delay, counter):
    while counter:
        if exitFlag:
            threadName.exit()
        time.sleep(delay)
        print("%s: %s" % (threadName, time.ctime(time.time())))
        counter -= 1

# Create new threads
thread1 = myThread(1, "Thread-1", 1)
thread2 = myThread(2, "Thread-2", 2)

# Start new Threads
thread1.start()
thread2.start()
thread1.join()
thread2.join()
print("Exiting Main Thread")
```

### Résultat

Lorsque nous exécutons le programme ci-dessus, il produit le résultat suivant :

```bash
Starting Thread-1
Starting Thread-2
Thread-1: Fri Feb 19 10:00:21 2016
Thread-2: Fri Feb 19 10:00:22 2016
Thread-1: Fri Feb 19 10:00:22 2016
Thread-1: Fri Feb 19 10:00:23 2016
Thread-2: Fri Feb 19 10:00:24 2016
Thread-1: Fri Feb 19 10:00:24 2016
Thread-1: Fri Feb 19 10:00:25 2016
Exiting Thread-1
Thread-2: Fri Feb 19 10:00:26 2016
Thread-2: Fri Feb 19 10:00:28 2016
Thread-2: Fri Feb 19 10:00:30 2016
Exiting Thread-2
Exiting Main Thread
```

## Synchronizing Threads

Le module threading fourni avec Python comprend un mécanisme de verrouillage simple à mettre en œuvre qui permet de synchroniser les threads. Un nouveau verrou est créé en appelant la méthode ```Lock()```, qui renvoie le nouveau verrou.

La méthode ```acquire(blocking)``` du nouvel objet lock est utilisée pour forcer les threads à s'exécuter de manière synchrone. Le paramètre optionnel blocking vous permet de contrôler si le thread attend pour acquérir le verrou.

Si la valeur de blocking est 0, le thread revient immédiatement avec une valeur 0 si le verrou ne peut pas être acquis et avec une valeur 1 si le verrou a été acquis. Si la valeur 1 est attribuée au blocage, le thread se bloque et attend que le verrou soit libéré.

La méthode ```release()``` du nouvel objet verrou est utilisée pour libérer le verrou lorsqu'il n'est plus nécessaire.

### Exemple

```python
#!/usr/bin/python3

import threading
import time

class myThread (threading.Thread):
    def __init__(self, threadID, name, counter):
        threading.Thread.__init__(self)
        self.threadID = threadID
        self.name = name
        self.counter = counter
    def run(self):
        print("Starting " + self.name)
        # Get lock to synchronize threads
        threadLock.acquire()
        print_time(self.name, self.counter, 3)
        # Free lock to release next thread
        threadLock.release()

def print_time(threadName, delay, counter):
    while counter:
        time.sleep(delay)
        print("%s: %s" % (threadName, time.ctime(time.time())))
        counter -= 1

threadLock = threading.Lock()
threads = []

# Create new threads
thread1 = myThread(1, "Thread-1", 1)
thread2 = myThread(2, "Thread-2", 2)

# Start new Threads
thread1.start()
thread2.start()

# Add threads to thread list
threads.append(thread1)
threads.append(thread2)

# Wait for all threads to complete
for t in threads:
    t.join()
print("Exiting Main Thread")
```

### Résultat

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Starting Thread-1
Starting Thread-2
Thread-1: Fri Feb 19 10:04:14 2016
Thread-1: Fri Feb 19 10:04:15 2016
Thread-1: Fri Feb 19 10:04:16 2016
Thread-2: Fri Feb 19 10:04:18 2016
Thread-2: Fri Feb 19 10:04:20 2016
Thread-2: Fri Feb 19 10:04:22 2016
Exiting Main Thread
```

## File d'attente prioritaire multithread

Le module Queue vous permet de créer un nouvel objet queue qui peut contenir un nombre spécifique d'éléments. Les méthodes suivantes permettent de contrôler la file d'attente : 

- ```get()``` - La méthode ```get()``` supprime et renvoie un élément de la file d'attente.
- ```put()``` - La méthode ```put()``` ajoute un élément à la file d'attente.
- ```qsize()``` - La méthode ```qsize()``` retourne le nombre d'éléments qui sont actuellement dans la file d'attente.
- ```empty()``` - La fonction ```empty()``` retourne True si la file d'attente est vide ; sinon, False.
- ```full()``` - La fonction ```full()``` retourne True si la file d'attente est pleine ; sinon, False.

### Exemple

```python
#!/usr/bin/python3

import queue
import threading
import time

exitFlag = 0

class myThread (threading.Thread):
    def __init__(self, threadID, name, q):
        threading.Thread.__init__(self)
        self.threadID = threadID
        self.name = name
        self.q = q
    def run(self):
        print("Starting " + self.name)
        process_data(self.name, self.q)
        print("Exiting " + self.name)

def process_data(threadName, q):
    while not exitFlag:
        queueLock.acquire()
        if not workQueue.empty():
            data = q.get()
            queueLock.release()
            print("%s processing %s" % (threadName, data))
        else:
            queueLock.release()
            time.sleep(1)

threadList = ["Thread-1", "Thread-2", "Thread-3"]
nameList = ["One", "Two", "Three", "Four", "Five"]
queueLock = threading.Lock()
workQueue = queue.Queue(10)
threads = []
threadID = 1

# Create new threads
for tName in threadList:
    thread = myThread(threadID, tName, workQueue)
    thread.start()
    threads.append(thread)
    threadID += 1

# Fill the queue
queueLock.acquire()
for word in nameList:
    workQueue.put(word)
queueLock.release()

# Wait for queue to empty
while not workQueue.empty():
    pass

# Notify threads it's time to exit
exitFlag = 1

# Wait for all threads to complete
for t in threads:
    t.join()
print("Exiting Main Thread")
```

### Résultat

Lorsque le code ci-dessus est exécuté, il produit le résultat suivant :

```bash
Starting Thread-1
Starting Thread-2
Starting Thread-3
Thread-1 processing One
Thread-2 processing Two
Thread-3 processing Three
Thread-1 processing Four
Thread-2 processing Five
Exiting Thread-3
Exiting Thread-1
Exiting Thread-2
Exiting Main Thread
```
