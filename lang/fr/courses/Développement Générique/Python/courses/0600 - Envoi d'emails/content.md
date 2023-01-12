Le protocole SMTP (Simple Mail Transfer Protocol) est un protocole qui permet d'envoyer des courriers électroniques et de les acheminer entre les serveurs de messagerie.

Python fournit le module ```smtplib```, qui définit un objet de session client SMTP pouvant être utilisé pour envoyer des courriels à toute machine Internet dotée d'un démon d'écoute SMTP ou ESMTP.

Voici une syntaxe simple pour créer un objet SMTP, qui peut ensuite être utilisé pour envoyer un courriel :

```python
import smtplib

smtpObj = smtplib.SMTP( [host [, port [, local_hostname]]] )
```

Voici le détail des paramètres :

- ```host``` - Il s'agit de l'hôte qui exécute votre serveur SMTP. Vous pouvez spécifier l'adresse IP de l'hôte ou un nom de domaine comme microlead.fr. Il s'agit d'un argument facultatif.
- ```port``` - Si vous fournissez l'argument host, vous devez spécifier le port sur lequel le serveur SMTP écoute. En général, ce port est 25.
- ```local_hostname``` - Si votre serveur SMTP est exécuté sur votre machine locale, vous pouvez spécifier simplement localhost l'option.

Un objet SMTP possède une méthode d'instance appelée sendmail, qui est typiquement utilisée pour effectuer le travail d'envoi d'un message. Elle prend trois paramètres :

- ```The sender``` : Une chaîne de caractères avec l'adresse de l'expéditeur.
- ```The receivers``` : Une liste de chaînes de caractères, une pour chaque destinataire.
- ```The message``` : Un message sous forme de chaîne de caractères formatée comme spécifié dans les différents RFC.

## Exemple

Voici un moyen simple d'envoyer un e-mail en utilisant un script Python :

```python
#!/usr/bin/python3

import smtplib

sender = 'from@fromdomain.com'
receivers = ['to@todomain.com']

message = """From: From Person <from@fromdomain.com>
To: To Person <to@todomain.com>
Subject: SMTP e-mail test

This is a test e-mail message.
"""

try:
    smtpObj = smtplib.SMTP('localhost')
    smtpObj.sendmail(sender, receivers, message)         
    print(Successfully sent email)
except SMTPException:
    print(Error: unable to send email)
```

Ici, vous avez placé un e-mail de base dans un message, en utilisant un guillemet triple, en prenant soin de formater correctement les en-têtes. Un e-mail nécessite un en-tête ```From```, ```To```, et un ```Subject```, séparés du corps de l'e-mail par une ligne blanche.

Pour envoyer le courrier, vous utilisez ```smtpObj``` pour vous connecter au serveur SMTP sur la machine locale. Utilisez ensuite la méthode sendmail avec le message, l'adresse de départ et l'adresse de destination comme paramètres (même si les adresses de départ et d'arrivée se trouvent dans l'e-mail lui-même, elles ne sont pas toujours utilisées pour acheminer le courrier).

Si vous ne faites pas tourner un serveur SMTP sur votre machine locale, vous pouvez utiliser le client smtplib pour communiquer avec un serveur SMTP distant. À moins que vous n'utilisiez un service de messagerie Web (tel que gmail ou Yahoo ! Mail), votre fournisseur de messagerie doit vous avoir fourni les détails du serveur de courrier sortant que vous pouvez leur fournir, comme suit :

```python
mail = smtplib.SMTP('smtp.gmail.com', 587)
```

## Envoi d'un email HTML à l'aide de Python

Lorsque vous envoyez un message texte en utilisant Python, tout le contenu est traité comme du texte simple. Même si vous incluez des balises HTML dans un message texte, celui-ci est affiché comme du texte simple et les balises HTML ne seront pas formatées selon la syntaxe HTML. Toutefois, Python offre la possibilité d'envoyer un message HTML en tant que message HTML réel.

Lors de l'envoi d'un message électronique, vous pouvez spécifier une version Mime, un type de contenu et le jeu de caractères pour envoyer un e-mail HTML.

### Exemple

L'exemple suivant permet d'envoyer le contenu HTML sous forme de courrier électronique :

```python
#!/usr/bin/python3

import smtplib

message = """From: From Person <from@fromdomain.com>
To: To Person <to@todomain.com>
MIME-Version: 1.0
Content-type: text/html
Subject: SMTP HTML e-mail test

This is an e-mail message to be sent in HTML format

<b>This is HTML message.</b>
<h1>This is headline.</h1>
"""

try:
    smtpObj = smtplib.SMTP('localhost')
    smtpObj.sendmail(sender, receivers, message)         
    print("Successfully sent email")
except SMTPException:
    print("Error: unable to send email")
```

## Envoi de pièces jointes dans un email

Pour envoyer un e-mail avec un contenu mixte, il faut définir l'en-tête ```Content-type``` sur ```multipart/mixed```. Ensuite, les sections texte et pièce jointe peuvent être spécifiées dans des limites.

Une limite commence par deux traits d'union suivis d'un numéro unique, qui ne peut pas figurer dans la partie message de l'e-mail. Une dernière limite indiquant la section finale de l'e-mail doit également se terminer par deux traits d'union.

Les fichiers joints doivent être codés à l'aide de la fonction ```pack("m")``` pour avoir un codage en base 64 avant la transmission.

### Exemple

Voici un exemple qui envoie un fichier ```/tmp/test.txt``` en pièce jointe :

```python
#!/usr/bin/python3

import smtplib
import base64

filename = "/tmp/test.txt"

# Read a file and encode it into base64 format
fo = open(filename, "rb")
filecontent = fo.read()
encodedcontent = base64.b64encode(filecontent)  # base64

sender = "webmaster@microlead.fr"
reciever = "admin@gmail.com"

marker = "AUNIQUEMARKER"

body ="""
This is a test email to send an attachement.
"""
# Define the main headers.
part1 = """From: From Person <me@fromdomain.net>
To: To Person <admin@gmail.com>
Subject: Sending Attachement
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary=%s
--%s
""" % (marker, marker)

# Define the message action
part2 = """Content-Type: text/plain
Content-Transfer-Encoding:8bit

%s
--%s
""" % (body,marker)

# Define the attachment section
part3 = """Content-Type: multipart/mixed; name=\"%s\"
Content-Transfer-Encoding:base64
Content-Disposition: attachment; filename=%s

%s
--%s--
""" %(filename, filename, encodedcontent, marker)
message = part1 + part2 + part3

try:
    smtpObj = smtplib.SMTP('localhost')
    smtpObj.sendmail(sender, reciever, message)
    print("Successfully sent email"
except Exception:
    print("Error: unable to send email")
```
