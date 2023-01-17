L'interface de passerelle commune, ou CGI, est un ensemble de normes qui définissent la manière dont les informations sont échangées entre le serveur web et un script personnalisé. Les spécifications CGI sont actuellement maintenues par le NCSA.

## Qu'est-ce que la CGI ?

- L'interface de passerelle commune, (ou *CGI* en anglais), est un standard pour les programmes de passerelle externe pour l'interface avec les serveurs d'information tels que les serveurs HTTP.
- La version actuelle est CGI/1.1 et CGI/1.2 est en cours de développement.

## Navigation sur le Web

Pour comprendre le concept de CGI, voyons ce qui se passe lorsque nous cliquons sur un lien hypertexte pour parcourir une page web ou une URL particulière.

- Votre navigateur contacte le serveur Web HTTP et demande l'URL, c'est-à-dire le nom du fichier.
- Le serveur Web analyse l'URL et recherche le nom du fichier. S'il trouve ce fichier, il le renvoie au navigateur, sinon il envoie un message d'erreur indiquant que vous avez demandé un mauvais fichier.
- Le navigateur Web prend la réponse du serveur Web et affiche soit le fichier reçu, soit le message d'erreur.

Cependant, il est possible de configurer le serveur HTTP de telle sorte que chaque fois qu'un fichier dans un certain répertoire est demandé, ce fichier n'est pas renvoyé ; il est exécuté comme un programme, et tout ce que ce programme produit est renvoyé pour que votre navigateur l'affiche. Cette fonction est appelée Common Gateway Interface ou CGI et les programmes sont appelés scripts CGI. Ces programmes CGI peuvent être un script Python, un script PERL, un script Shell, un programme C ou C++, etc.

## Support et configuration du serveur Web

Avant de procéder à la programmation CGI, assurez-vous que votre serveur Web supporte les CGI et qu'il est configuré pour gérer les programmes CGI. Tous les programmes CGI qui seront exécutés par le serveur HTTP sont conservés dans un répertoire pré-configuré. Ce répertoire est appelé répertoire CGI et par convention, il est nommé /var/www/cgi-bin. Par convention, les fichiers CGI ont une extension .cgi, mais vous pouvez également conserver vos fichiers avec l'extension .py.

Par défaut, le serveur Linux est configuré pour exécuter uniquement les scripts du répertoire cgi-bin dans /var/www. Si vous voulez spécifier un autre répertoire pour exécuter vos scripts CGI, commentez les lignes suivantes dans le fichier httpd.conf :

```bash
<Directory "/var/www/cgi-bin">
    AllowOverride None
    Options ExecCGI
    Order allow,deny
    Allow from all
</Directory>

<Directory "/var/www/cgi-bin">
Options All
</Directory>
```

Ici, nous supposons que le serveur Web est installé et fonctionne correctement et que vous êtes en mesure d'exécuter tout autre programme CGI comme Perl ou Shell, etc.

## Premier programme CGI

Voici un lien simple, qui est lié à un script CGI appelé hello.py. Ce fichier est conservé dans le répertoire /var/www/cgi-bin et son contenu est le suivant. Avant de lancer votre programme CGI, assurez-vous d'avoir changé le mode du fichier en utilisant la commande UNIX chmod 755 hello.py pour rendre le fichier exécutable.

```python
#!/usr/bin/python

print("Content-type:text/html\r\n\r\n")
print("<html>")
print("<head>")
print("<title>Hello Word - First CGI Program</title>")
print("</head>")
print("<body>")
print("<h2>Hello Word! This is my first CGI program</h2>")
print("</body>")
print("</html>")
```

__Remarque__ : La première ligne du script doit être le chemin de l'exécutable Python. Sous Linux, il doit être #!/usr/bin/python3

Entrez l'URL suivante dans votre navigateur :

```bash
http://localhost:8080/cgi-bin/hello.py
```

## Hello Word! C'est mon premier programme CGI

Ce script hello.py est un simple script Python, qui écrit sa sortie sur le fichier STDOUT, c'est-à-dire sur l'écran. Il existe une fonctionnalité importante et supplémentaire qui est la première ligne à être imprimée ```Content-type:text/html\r\n\r\n```. Cette ligne est renvoyée au navigateur et spécifie le type de contenu à afficher sur l'écran du navigateur.

À présent, vous devez avoir compris le concept de base des CGI et vous pouvez écrire de nombreux programmes CGI compliqués en utilisant Python. Ce script peut interagir avec n'importe quel autre système externe pour échanger des informations, par exemple un SGBDR.

## En-tête HTTP

La ligne ```Content-type:text/html\r\n\r\n``` fait partie de l'en-tête HTTP qui est envoyé au navigateur pour comprendre le contenu. Tous les en-têtes HTTP se présentent sous la forme suivante :

```bash
HTTP Field Name: Field Content
```

Par exemple

```bash
Content-type: text/html\r\n\r\n
```

Il existe quelques autres en-têtes HTTP importants, que vous utiliserez fréquemment dans votre programmation CGI :

- ```Content-type``` : Un string MIME se définit le format du fichier qu'il retourne. Exemple : ```Content-type:text/html```.
- ```Expires: Date``` : La date à laquelle l'information devient invalide. Il est utilisé par le navigateur pour décider quand la page doit se rafraîchir. Un format de date valide est présenter comme ceci : ```01 Jan 1998 12:00:00 GMT```.
- ```Location: URL``` : L'URL qui est retournée ou lieu de l'URL demandée. Vous pouvez utilisez ce champs pour redirigé vers n'importe quel fichier.
- ```Last-modified: Date``` : La date de la derniere modification de la ressource.
- ```Content-length``` : La longueur, en octets, des données renvoyées. Le navigateur utilise cette valeur pour indiquer le temps de téléchargement estimé d'un fichier.
- ```Set-Cookie: String``` : Définissez le cookie transmis par le ```string```.

## Variables d'environnement CGI

Tous les programmes CGI ont accès aux variables d'environnement suivantes. Ces variables jouent un rôle important lors de l'écriture d'un programme CGI.

- ```CONTENT_TYPE``` : Le type de données du contenu. Utilisé lorsque le client envoie un contenu joint au serveur. Par exemple, le téléchargement de fichiers.
- ```CONTENT_LENGTH``` : La longueur des informations de la requête. Elle n'est disponible que pour les requêtes POST.
- ```HTTP_COOKIE``` : Renvoie les cookies définis sous la forme d'une paire clé/valeur.
- ```HTTP_USER_AGENT``` : Le champ d'en-tête User-Agent contient des informations sur l'agent utilisateur à l'origine de la demande. Il s'agit du nom du navigateur web.
- ```PATH_INFO``` : Le chemin du script CGI.
- ```QUERY_STRING``` : L'information codée en URL qui est envoyée avec la demande de la méthode GET.
- ```REMOTE_ADDR``` : L'adresse IP de l'hôte distant qui fait la demande. Ceci est utile pour la journalisation ou l'authentification.

Voici un petit programme CGI pour lister toutes les variables CGI.

```python
#!/usr/bin/python

import os

print("Content-type: text/html\r\n\r\n");
print("<font size=+1>Environment</font><\br>");
for param in os.environ.keys():
    print("<b>%20s</b>: %s<\br>" % (param, os.environ[param]))
```

## Méthodes GET et POST

Vous avez dû rencontrer de nombreuses situations dans lesquelles vous devez transmettre des informations de votre navigateur au serveur web et finalement à votre programme CGI. Le plus souvent, le navigateur utilise deux méthodes pour transmettre ces informations au serveur web. Ces méthodes sont la méthode GET et la méthode POST.

### Transmission d'informations à l'aide de la méthode GET

La méthode GET envoie les informations utilisateur codées jointes à la demande de page. La page et les informations codées sont séparées par le caractère ```?``` comme suit :

```bash
http://www.test.com/cgi-bin/hello.py?key1=value1&key2=value2
```

- La méthode GET est la méthode par défaut pour transmettre des informations du navigateur au serveur web. Elle produit une longue chaîne de caractères qui apparaît dans le champ "Emplacement" de votre navigateur.
- N'utilisez jamais la méthode GET si vous avez un mot de passe ou d'autres informations sensibles à transmettre au serveur.
- La méthode GET a une limite de taille : seulement 1024 caractères peuvent être envoyés dans une chaîne de requête.
- La méthode GET envoie des informations en utilisant l'en-tête QUERY_STRING et sera accessible dans votre programme CGI grâce à la variable d'environnement ```QUERY_STRING```.

Vous pouvez transmettre des informations en concaténant simplement des paires de clés et de valeurs avec n'importe quelle URL ou vous pouvez utiliser les balises HTML ```<FORM>``` pour transmettre des informations en utilisant la méthode GET.

### Exemple d'URL simple : méthode GET

Voici une URL simple, qui transmet deux valeurs au programme hello_get.py en utilisant la méthode GET.

```bash
/cgi-bin/hello_get.py?first_name=ZARA&last_name=ALI
```

Voici le script ```hello_get.py``` qui permet de gérer les données fournies par le navigateur web. Nous allons utiliser le module CGI, qui permet d'accéder très facilement aux informations transmises :

```python
#!/usr/bin/python

# Import modules for CGI handling 
import cgi, cgitb 

# Create instance of FieldStorage 
form = cgi.FieldStorage() 

# Get data from fields
first_name = form.getvalue('first_name')
last_name  = form.getvalue('last_name')

print("Content-type:text/html\r\n\r\n")
print("<html>")
print("<head>")
print("<title>Hello - Second CGI Program</title>")
print("</head>")
print("<body>")
print("<h2>Hello %s %s</h2>" % (first_name, last_name))
print("</body>")
print("</html>")
```

### Exemple de formulaire simple : méthode GET

Cet exemple transmet deux valeurs en utilisant le formulaire HTML et le bouton "submit". Nous utilisons le même script CGI hello_get.py pour gérer cette entrée.

```html
<form action="/cgi-bin/hello_get.py" method="get">
    First Name: <input type="text" name="first_name"><br/>

    Last Name: <input type="text" name="last_name"/>
    <input type="submit" value="Submit"/>
</form>
```

### Transmettre des informations en utilisant la méthode POST

Une méthode généralement plus fiable pour transmettre des informations à un programme CGI est la méthode POST. Cette méthode regroupe les informations exactement de la même manière que la méthode GET, mais au lieu de les envoyer sous forme de chaîne de texte après un ? Dans l'URL, elle les envoie sous forme de message séparé. Ce message arrive dans le script CGI sous la forme de l'entrée standard.

Voici le même script ```hello_get.py``` qui gère la méthode GET ainsi que la méthode POST.

```python
#!/usr/bin/python

# Import modules for CGI handling 
import cgi, cgitb 

# Create instance of FieldStorage 
form = cgi.FieldStorage() 

# Get data from fields
first_name = form.getvalue('first_name')
last_name = form.getvalue('last_name')

print("Content-type:text/html\r\n\r\n")
print("<html>")
print("<head>")
print("<title>Hello - Second CGI Program</title>")
print("</head>")
print("<body>")
print("<h2>Hello %s %s</h2>" % (first_name, last_name))
print("</body>")
print("</html>")
```

Reprenons le même exemple que ci-dessus qui transmet deux valeurs en utilisant le formulaire HTML et le bouton "submit". Nous utilisons le même script CGI ```hello_get.py``` pour gérer cette entrée.

```html
<form action="/cgi-bin/hello_get.py" method="post">
First Name: <input type="text" name="first_name"><br/>
Last Name: <input type="text" name="last_name"/>

<input type="submit" value="Submit"/>
</form>
```

### Passer les données de la case à cocher au programme CGI

Les cases à cocher sont utilisées lorsqu'il faut sélectionner plus d'une option.

Voici un exemple de code HTML pour un formulaire comportant deux cases à cocher :

```html
<form action="/cgi-bin/checkbox.cgi" method="POST" target="_blank">
    <input type="checkbox" name="maths" value="on"/> Maths
    <input type="checkbox" name="physics" value="on"/> Physics
    <input type="submit" value="Select Subject"/>
</form>
```

Le script ```checkbox.cgi``` ci-dessous permet de traiter les données fournies par le navigateur Web pour le bouton de la case à cocher.

```python
#!/usr/bin/python

# Import modules for CGI handling 
import cgi, cgitb 

# Create instance of FieldStorage 
form = cgi.FieldStorage() 

# Get data from fields
if form.getvalue('maths'):
   math_flag = "ON"
else:
   math_flag = "OFF"

if form.getvalue('physics'):
   physics_flag = "ON"
else:
   physics_flag = "OFF"

print("Content-type:text/html\r\n\r\n")
print("<html>")
print("<head>")
print("<title>Checkbox - Third CGI Program</title>")
print("</head>")
print("<body>")
print("<h2> CheckBox Maths is : %s</h2>" % math_flag)
print("<h2> CheckBox Physics is : %s</h2>" % physics_flag)
print("</body>")
print("</html>")
```

### Passer les données d'un bouton radio à un programme CGI

Les boutons radio sont utilisés lorsqu'une seule option doit être sélectionnée.

Voici un exemple de code HTML pour un formulaire avec deux boutons radio :

```html
<form action="/cgi-bin/radiobutton.py" method="post" target="_blank">
    <input type="radio" name="subject" value="maths"/> Maths
    <input type="radio" name="subject" value="physics"/> Physics
    <input type="submit" value="Select Subject"/>
</form>
```

Le script ```radiobutton.py``` ci-dessous permet de gérer les données fournies par le navigateur web pour un bouton radio :

```python
#!/usr/bin/python

# Import modules for CGI handling 
import cgi, cgitb 

# Create instance of FieldStorage 
form = cgi.FieldStorage() 

# Get data from fields
if form.getvalue('subject'):
    subject = form.getvalue('subject')
else:
    subject = "Not set"

print("Content-type:text/html\r\n\r\n")
print("<html>")
print("<head>")
print("<title>Radio - Fourth CGI Program</title>")
print("</head>")
print("<body>")
print("<h2> Selected Subject is %s</h2>" % subject)
print("</body>")
print("</html>")
```

### Passer les données de la zone de texte au programme CGI

L'élément TEXTAREA est utilisé lorsque du texte multiligne doit être transmis au programme CGI.

Voici un exemple de code HTML pour un formulaire avec une case TEXTAREA :

```html
<form action="/cgi-bin/textarea.py" method="post" target="_blank">
    <textarea name="textcontent" cols="40" rows="4">
        Tapez votre texte ici...
    </textarea>
    <input type="submit" value="Submit"/>
</form>
```

Voici le script ```textarea.cgi``` pour traiter les données fournies par le navigateur web :

```python
#!/usr/bin/python

# Import modules for CGI handling 
import cgi, cgitb 

# Create instance of FieldStorage 
form = cgi.FieldStorage() 

# Get data from fields
if form.getvalue('textcontent'):
    text_content = form.getvalue('textcontent')
else:
    text_content = "Not entered"

print("Content-type:text/html\r\n\r\n")
print("<html>")
print("<head>")
print("<title>Text Area - Fifth CGI Program</title>")
print("</head>")
print("<body>")
print("<h2> Entered Text Content is %s</h2>" % text_content)
print("</body>")
```

### Transmettre les données de la boîte de dépôt à un programme CGI

La liste déroulante est utilisée lorsque de nombreuses options sont disponibles mais que seules une ou deux seront sélectionnées.

Voici un exemple de code HTML pour un formulaire avec une seule liste déroulante :

```html
<form action="/cgi-bin/dropdown.py" method="post" target="_blank">
    <select name="dropdown">
        <option value="Maths" selected>Maths</option>
        <option value="Physics">Physics</option>
    </select>
    <input type="submit" value="Submit"/>
</form>
```

Voici le script ```dropdown.py``` qui permet de gérer les données fournies par le navigateur web.

```python
#!/usr/bin/python

# Import modules for CGI handling 
import cgi, cgitb 

# Create instance of FieldStorage 
form = cgi.FieldStorage() 

# Get data from fields
if form.getvalue('dropdown'):
    subject = form.getvalue('dropdown')
else:
    subject = "Not entered"

print("Content-type:text/html\r\n\r\n")
print("<html>")
print("<head>")
print("<title>Dropdown Box - Sixth CGI Program</title>")
print("</head>")
print("<body>")
print("<h2> Selected Subject is %s</h2>" % subject)
print("</body>")
print("</html>")
```

## Utilisation des cookies en CGI

Le protocole HTTP est un protocole sans état. Pour un site Web commercial, il est nécessaire de conserver les informations de session entre les différentes pages. Par exemple, l'inscription d'un utilisateur se termine après avoir rempli plusieurs pages. Comment conserver les informations de session de l'utilisateur sur toutes les pages Web ?

Dans de nombreuses situations, l'utilisation de cookies est la méthode la plus efficace pour mémoriser et suivre les préférences, les achats, les commissions et d'autres informations nécessaires pour améliorer l'expérience du visiteur ou les statistiques du site.

### Comment ça marche ?

Votre serveur envoie certaines données au navigateur du visiteur sous la forme d'un cookie. Le navigateur peut accepter le cookie. S'il l'accepte, il est stocké sous forme de texte brut sur le disque dur du visiteur. Désormais, lorsque le visiteur arrive sur une autre page de votre site, le cookie peut être récupéré. Une fois récupéré, votre serveur sait/se souvient de ce qui a été stocké.

Les cookies sont un enregistrement de données en texte clair composé de 5 champs de longueur variable :

- ```Expire``` - La date à laquelle le cookie expirera. Si ce champ est vide, le cookie expirera lorsque le visiteur quittera son navigateur.
- ```Domaine``` - Le nom de domaine de votre site.
- ```Chemin``` - Le chemin d'accès au répertoire ou à la page Web qui définit le cookie. Ce champ peut être vide si vous souhaitez récupérer le cookie à partir de n'importe quel répertoire ou page.
- ```Sécurisé``` - Si ce champ contient le mot "sécurisé", le cookie ne peut être récupéré qu'avec un serveur sécurisé. Si ce champ est vide, aucune restriction de ce type n'existe.
- ```Nom = Valeur``` - Les cookies sont définis et récupérés sous la forme de paires clé-valeur.

### Configuration des cookies

Il est très facile d'envoyer des cookies au navigateur. Ces cookies sont envoyés avec l'en-tête HTTP avant le champ Content-type. Supposons que vous vouliez définir UserID et Password comme cookies. La configuration des cookies se fait comme suit :

```python
#!/usr/bin/python
print("Set-Cookie:UserID = ABC;\r\n")
print("Set-Cookie:Password = ABC123;\r\n")
print("Set-Cookie:Expires = Monday, 13-Dec-2021 17:17:40 GMT;\r\n")
print("Set-Cookie:Domain = www.microlead.fr;\r\n")
print("Set-Cookie:Path = /perl;\n")
print("Content-type:text/html\r\n\r\n")
# ...........Rest of the HTML Content....
```

À partir de cet exemple, vous devez avoir compris comment définir les cookies. Nous utilisons l'en-tête HTTP ```Set-Cookie``` pour définir les cookies.

Il est facultatif de définir les attributs des cookies comme Expires, Domain et Path. Il est à noter que les cookies sont définis avant l'envoi de la ligne magique ```Content-type:text/html\r\n\r\n```.

### Récupération des cookies

Il est très facile de récupérer tous les cookies définis. Les cookies sont stockés dans la variable d'environnement CGI ```HTTP_COOKIE``` et ils ont la forme suivante :

```bash
key1 = value1;key2 = value2;key3 = value3....
```

Voici un exemple de la façon de récupérer les cookies.

```python
#!/usr/bin/python

# Import modules for CGI handling 
from os import environ
import cgi, cgitb

if environ.has_key('HTTP_COOKIE'):
    for cookie in map(strip, split(environ['HTTP_COOKIE'], ';')):
        (key, value) = split(cookie, '=');
        if key == "UserID":
            user_id = value

        if key == "Password":
            password = value

print("User ID  = %s" % user_id)
print("Password = %s" % password)
```

Cela donne le résultat suivant pour les cookies définis par le script ci-dessus :

```bash
User ID = ABC
Password = ABC123
```

## Exemple de téléchargement de fichiers

Pour télécharger un fichier, le formulaire HTML doit avoir l'attribut enctype défini sur ```multipart/form-data```. La balise input avec le type de fichier crée un bouton "Browse".

```html
<html>
    <body>
        <form enctype="multipart/form-data" action="save_file.py" method="post">
        <p>File: <input type="file" name="filename"/></p>
        <p><input type="submit" value="Upload"/></p>
        </form>
    </body>
</html>
```

L'exemple ci-dessus a été désactivé intentionnellement pour éviter que les gens téléchargent des fichiers sur notre serveur, mais vous pouvez essayer le code ci-dessus avec votre serveur.

Voici le script ```save_file.py``` pour gérer le téléchargement de fichiers :

```python
#!/usr/bin/python

import cgi, os
import cgitb; cgitb.enable()

form = cgi.FieldStorage()

# Get filename here.
fileitem = form['filename']

# Test if the file was uploaded
if fileitem.filename:
    # strip leading path from file name to avoid 
    # directory traversal attacks
    fn = os.path.basename(fileitem.filename)
    open('/tmp/' + fn, 'wb').write(fileitem.file.read())

    message = 'The file "' + fn + '" was uploaded successfully'

else:
    message = 'No file was uploaded'

print("""
Content-Type: text/html\n
<html>
    <body>
        <p>%s</p>
    </body>
</html>
""" % message)
```

Si vous exécutez le script ci-dessus sur Unix/Linux, alors vous devez prendre soin de remplacer le séparateur de fichier comme suit, sinon sur votre machine Windows l'instruction ```open()``` ci-dessus devrait fonctionner correctement.

```python
fn = os.path.basename(fileitem.filename.replace("\\", "/" ))
```

## Comment faire apparaître une boîte de dialogue "Téléchargement de fichier" ?

Parfois, on souhaite donner la possibilité à un utilisateur de cliquer sur un lien et une boîte de dialogue "Téléchargement de fichier" s'ouvrira à l'utilisateur au lieu d'afficher le contenu réel. Ceci est très facile et peut être réalisé grâce à l'en-tête HTTP. Cet en-tête HTTP est différent de l'en-tête mentionné dans la section précédente.

Par exemple, si vous voulez que le fichier FileName puisse être téléchargé à partir d'un lien donné, sa syntaxe est la suivante :

```python
#!/usr/bin/python

# HTTP Header
print("Content-Type:application/octet-stream; name = \"FileName\"\r\n")
print("Content-Disposition: attachment; filename = \"FileName\"\r\n\n")

# Actual File Content will go here.
fo = open("foo.txt", "rb")

str = fo.read();
print("str")

# Close opend file
fo.close()
```
