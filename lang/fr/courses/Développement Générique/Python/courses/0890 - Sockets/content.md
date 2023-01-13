Python offre deux niveaux d'accès aux services réseau. À un niveau inférieur, vous pouvez accéder à la prise en charge de base des sockets dans le système d'exploitation sous-jacent, ce qui vous permet d'implémenter des clients et des serveurs pour les protocoles orientés connexion et sans connexion.

Python dispose également de bibliothèques qui fournissent un accès de plus haut niveau à des protocoles réseau spécifiques au niveau des applications, tels que FTP, HTTP, etc.

Ce chapitre vous permet de comprendre le concept le plus célèbre de la mise en réseau - la programmation des sockets.

## Qu'est-ce que les Sockets ?

Les sockets sont les points d'extrémité d'un canal de communication bidirectionnel. Les sockets peuvent communiquer au sein d'un processus, entre des processus sur la même machine, ou entre des processus sur différents continents.

Les sockets peuvent être implémentés sur un certain nombre de types de canaux différents : sockets de domaine Unix, TCP, UDP, etc. La bibliothèque de sockets fournit des classes spécifiques pour gérer les transports courants ainsi qu'une interface générique pour gérer les autres.

Les sockets ont leur propre vocabulaire :

- ```domain``` : La famille de protocoles qui est utilisée comme mécanisme de transport. Ces valeurs sont des constantes telles que AF_INET, PF_INET, PF_UNIX, PF_X25, et ainsi de suite.
- ```type``` : Le type de communication entre les deux points d'extrémité, typiquement SOCK_STREAM pour les protocoles orientés connexion et SOCK_DGRAM pour les protocoles sans connexion.
- ```protocol``` : Généralement zéro, ceci peut être utilisé pour identifier une variante d'un protocole dans un domaine et un type.
- ```hostname``` : L'identifiant d'une interface réseau :
    - Une chaîne, qui peut être un nom d'hôte, une adresse en quart de point ou une adresse IPV6 en notation deux points (et éventuellement point).
    - Une chaîne ```<broadcast>```, qui spécifie une adresse INADDR_BROADCAST.
    - Une chaîne de longueur zéro, qui spécifie INADDR_ANY.
    - Un nombre entier, interprété comme une adresse binaire dans l'ordre des octets de l'hôte.
- ```port``` : Chaque serveur écoute les clients qui l'appellent sur un ou plusieurs ports. Un port peut être un numéro de port Fixnum, une chaîne contenant un numéro de port, ou le nom d'un service.

## Le module socket

Pour créer un socket, vous devez utiliser la fonction socket.socket() disponible dans le module socket, qui a la syntaxe générale :

```python
s = socket.socket(socket_family, socket_type, protocol = 0)
```

Voici la description des paramètres :

- **socket_family** - Il s'agit de AF_UNIX ou AF_INET, comme expliqué précédemment.
- **socket_type** - Il s'agit de SOCK_STREAM ou SOCK_DGRAM.
- **protocol** - Ce paramètre est généralement laissé de côté et prend la valeur 0 par défaut.

Une fois que vous avez l'objet socket, vous pouvez utiliser les fonctions requises pour créer votre programme client ou serveur. Voici la liste des fonctions requises :

## Méthodes pour les sockets de serveur

- ```s.bind()``` : Cette méthode lie l'adresse (nom d'hôte, numéro de port) au socket.
- ```s.listen()``` : Cette méthode configure et démarre l'écouteur TCP.
- ```s.accept()``` : Cette méthode accepte passivement la connexion du client TCP, en attendant que la connexion arrive (blocage).

## Méthodes pour les sockets clients

- ```s.connect()``` : Cette méthode initie activement la connexion au serveur TCP.

## Méthodes générales de prise en charge

- ```s.recv()``` : Cette méthode reçoit le message TCP.
- ```s.send()``` : Cette méthode transmet un message TCP.
- ```s.recvfrom()``` : Cette méthode reçoit un message UDP.
- ```s.sendto()``` : Cette méthode transmet un message UDP.
- ```s.close()``` : Cette méthode ferme le socket.
- ```s.gethostname()``` : Renvoie le nom d'hôte.

## Un simple serveur

Pour écrire des serveurs Internet, nous utilisons la fonction ```socket``` disponible dans le module socket pour créer un objet socket. Un objet socket est ensuite utilisé pour appeler d'autres fonctions afin de configurer un serveur de socket.

Appelez maintenant la fonction ```bind(hostname, port)``` pour spécifier un port pour votre service sur l'hôte donné.

Ensuite, appelez la méthode ```accept``` de l'objet retourné. Cette méthode attend qu'un client se connecte au port que vous avez spécifié, puis renvoie un objet de connexion qui représente la connexion à ce client.

```python
#!/usr/bin/python3           # This is server.py file
import socket                                         

# create a socket object
serversocket = socket.socket(
    socket.AF_INET, socket.SOCK_STREAM) 

# get local machine name
host = socket.gethostname()                           

port = 9999                                           

# bind to the port
serversocket.bind((host, port))                                  

# queue up to 5 requests
serversocket.listen(5)                                           

while True:
    # establish a connection
    clientsocket,addr = serversocket.accept()      

    print("Got a connection from %s" % str(addr))

    msg = 'Thank you for connecting' + "\r\n"
    clientsocket.send(msg.encode('ascii'))
    clientsocket.close()
```

## Un simple client

Écrivons un programme client très simple qui ouvre une connexion vers un port 12345 et un hôte donné. Il est très simple de créer un client socket en utilisant la fonction du module socket de Python.

La fonction ```socket.connect(hostname, port)``` ouvre une connexion TCP au nom d'hôte sur le port. Une fois que vous avez ouvert un socket, vous pouvez lire à partir de celui-ci comme n'importe quel objet IO. Lorsque vous avez terminé, n'oubliez pas de le fermer, comme vous fermeriez un fichier.

### Exemple

Le code suivant est un client très simple qui se connecte à un hôte et à un port donnés, lit toutes les données disponibles sur le socket, puis quitte :

```python
#!/usr/bin/python3           # This is client.py file

import socket

# create a socket object
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM) 

# get local machine name
host = socket.gethostname()                           

port = 9999

# connection to hostname on the port.
s.connect((host, port))                               

# Receive no more than 1024 bytes
msg = s.recv(1024)                                     

s.close()
print(msg.decode('ascii'))
```

Maintenant, exécutez ce ```server.py``` en arrière-plan et ensuite exécutez le client.py ci-dessus pour voir le résultat.

```bash
# Following would start a server in background.
$ python server.py & 

# Once server is started run client as follows:
$ python client.py
```

### Résultat

Le résultat serait le suivant :

```bash
on server terminal
Got a connection from ('192.168.1.10', 3747)
On client terminal
Thank you for connecting
```

## Python Internet Modules

Une liste de quelques modules importants en programmation réseau/Internet Python est donnée ci-dessous :

| **Protocole** | **Fonction commune** | **Port No** | **ModulePython** |
| --- | --- | --- | --- |
| HTTP | Pages web | 80 | httplib, urllib, xmlrpclib |
| NNTP | Nouvelles Usenet | 119 | nntplib |
| FTP | Transferts de fichiers | 20 | ftplib, urllib |
| SMTP | Envoi d'un email | 25 | smtplib |
| POP3 | Récupération d’un email | 110 | poplib |
| IMAP4 | Récupération d’un email | 143 | imaplib |
| Telnet | Lignes de commande | 23 | telnetlib |
| Gopher | Transferts de documents | 70 | gopherlib, urllib |

Veuillez vérifier toutes les bibliothèques mentionnées ci-dessus pour travailler avec les protocoles FTP, SMTP, POP et IMAP.
