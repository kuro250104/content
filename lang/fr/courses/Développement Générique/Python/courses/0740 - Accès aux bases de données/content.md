Le standard Python pour les interfaces de base de données est l'interface Python DB-API. La plupart des interfaces de base de données Python adhèrent à ce standard.

Vous pouvez choisir la base de données qui convient à votre application. L'API de base de données Python prend en charge un large éventail de serveurs de bases de données tels que :

- GadFly
- mSQL
- MySQL
- PostgreSQL
- Microsoft SQL Server 2000
- Informix
- Interbase
- Oracle
- Sybase
- SQLite

Vous devez télécharger un module DB API distinct pour chaque base de données à laquelle vous devez accéder. Par exemple, si vous devez accéder à une base de données Oracle ainsi qu'à une base de données MySQL, vous devez télécharger les modules Oracle et MySQL.

L'API DB fournit un standard minimal pour travailler avec des bases de données en utilisant, dans la mesure du possible, les structures et la syntaxe Python. Cette API comprend les éléments suivants :

- Importer le module API.
- Obtenir une connexion avec la base de données.
- Émettre des instructions SQL et des procédures stockées.
- Fermeture de la connexion.

Python a un support intégré pour SQLite. Dans cette section, nous allons apprendre tous les concepts en utilisant MySQL. Le module MySQLdb, une interface populaire avec MySQL, n'est pas compatible avec Python 3. Nous utiliserons plutôt le module PyMySQL.

## Qu'est-ce que PyMySQL ?

PyMySQL est une interface permettant de se connecter à un serveur de base de données MySQL depuis Python. Elle implémente l'API Python Database v2.0 et contient une bibliothèque client MySQL purement Python. L'objectif de PyMySQL est d'être un remplacement direct de MySQLdb.

## Comment installer PyMySQL ?

Avant de poursuivre, vous devez vous assurer que PyMySQL est installé sur votre machine. Tapez simplement ce qui suit, dans votre script Python et exécutez-le :

```python
#!/usr/bin/python3

import pymysql
```

Si le résultat est le suivant, cela signifie que le module MySQLdb n'est pas installé :

```bash
Traceback (most recent call last):
    File "test.py", line 3, in <module>
        Import pymysql
ImportError: No module named pymysql
```

La dernière version stable est disponible sur PyPI et peut être installée avec pip :

```bash
pip install pymysql
```

Alternativement (par exemple si pip n'est pas disponible), une archive peut être téléchargée depuis GitHub et installée avec Setuptools comme suit :

```bash
$ # X.X is the desired pymysql version (e.g. 0.5 or 0.6).
$ curl -L https://github.com/PyMySQL/PyMySQL/tarball/pymysql-X.X | tar xz
$ cd PyMySQL*
$ python setup.py install
$ # The folder PyMySQL* can be safely removed now.
```

__Remarque__ : Assurez-vous d'avoir les privilèges de root pour installer le module ci-dessus.

## Connexion à la base de données

Avant de vous connecter à une base de données MySQL, assurez-vous des points suivants :

- Vous avez créé une base de données TESTDB.
- Vous avez créé une table EMPLOYEE dans TESTDB.
- Cette table a des champs FIRST_NAME, LAST_NAME, AGE, SEX et INCOME.
- L'ID utilisateur "testuser" et le mot de passe "test123" sont définis pour accéder à TESTDB.
- Le module Python PyMySQL est correctement installé sur votre machine.
- Vous avez parcouru le tutoriel MySQL pour comprendre les bases de MySQL.

### Exemple

Voici un exemple de connexion à la base de données MySQL "TESTDB" :

```python
#!/usr/bin/python3

import pymysql

# Open database connection
db = pymysql.connect("localhost", "testuser", "test123", "TESTDB")

# prepare a cursor object using cursor() method
cursor = db.cursor()

# execute SQL query using execute() method.
cursor.execute("SELECT VERSION()")

# Fetch a single row using fetchone() method.
data = cursor.fetchone()
print("Database version : %s " % data)

# disconnect from server
db.close()
```

En exécutant ce script, il produit le résultat suivant.

```bash
Database version : 5.5.20-log
```

Si une connexion est établie avec la source de données, un objet de connexion est renvoyé et enregistré dans ```db``` pour une utilisation ultérieure, sinon ```db``` prend la valeur ```None```. Ensuite, l'objet ```db``` est utilisé pour créer un objet cursor, qui à son tour est utilisé pour exécuter des requêtes SQL. Enfin, avant de sortir, il s'assure que la connexion à la base de données est fermée et que les ressources sont libérées.

## Création d'une table de base de données

Une fois la connexion à la base de données établie, nous sommes prêts à créer des tables ou des enregistrements dans les tables de la base de données en utilisant la méthode ```execute``` du curseur créé.

### Exemple

Créons une table de base de données EMPLOYEE :

```python
#!/usr/bin/python3

import pymysql

# Open database connection
db = pymysql.connect("localhost", "testuser", "test123", "TESTDB")

# prepare a cursor object using cursor() method
cursor = db.cursor()

# Drop table if it already exist using execute() method.
cursor.execute("DROP TABLE IF EXISTS EMPLOYEE")

# Create table as per requirement
sql = """CREATE TABLE EMPLOYEE (
    FIRST_NAME  CHAR(20) NOT NULL,
    LAST_NAME  CHAR(20),
    AGE INT,  
    SEX CHAR(1),
    INCOME FLOAT )"""

cursor.execute(sql)

# disconnect from server
db.close()
```

## Opération INSERT

L'opération INSERT est nécessaire lorsque vous souhaitez créer vos enregistrements dans une table de base de données.

### Exemple

L'exemple suivant exécute l'instruction SQL INSERT pour créer un enregistrement dans la table EMPLOYEE.

```python
#!/usr/bin/python3

import pymysql

# Open database connection
db = pymysql.connect("localhost", "testuser", "test123", "TESTDB" )

# prepare a cursor object using cursor() method
cursor = db.cursor()

# Prepare SQL query to INSERT a record into the database.
sql = """INSERT INTO EMPLOYEE(FIRST_NAME,
    LAST_NAME, AGE, SEX, INCOME)
    VALUES ('Mac', 'Mohan', 20, 'M', 2000)"""
try:
    # Execute the SQL command
    cursor.execute(sql)
    # Commit your changes in the database
    db.commit()
except:
    # Rollback in case there is any error
    db.rollback()

# disconnect from server
db.close()
```

L'exemple ci-dessus peut être écrit comme suit pour créer des requêtes SQL de manière dynamique :

```python
#!/usr/bin/python3

import pymysql

# Open database connection
db = pymysql.connect("localhost", "testuser", "test123", "TESTDB")

# prepare a cursor object using cursor() method
cursor = db.cursor()

# Prepare SQL query to INSERT a record into the database.
sql = "INSERT INTO EMPLOYEE(FIRST_NAME, \
    LAST_NAME, AGE, SEX, INCOME) \
    VALUES ('%s', '%s', '%d', '%c', '%d' )" % \
    ('Mac', 'Mohan', 20, 'M', 2000)
try:
    # Execute the SQL command
    cursor.execute(sql)
    # Commit your changes in the database
    db.commit()
except:
    # Rollback in case there is any error
    db.rollback()

# disconnect from server
db.close()
```

### Exemple

Le segment de code suivant est une autre forme d'exécution où vous pouvez passer des paramètres directement :

```python
# ..................................
user_id = "test123"
password = "password"

con.execute('insert into Login values("%s", "%s")' % \
                (user_id, password))
# ..................................
```

## Opération de lecture

L'opération READ sur une base de données signifie que l'on va chercher des informations utiles dans la base de données.

Une fois la connexion à la base de données établie, vous êtes prêt à effectuer une requête dans cette base de données. Vous pouvez utiliser la méthode ```fetchone()``` pour extraire un seul enregistrement ou la méthode ```fetchall()``` pour extraire plusieurs valeurs d'une table de base de données.

- ```fetchone()``` - Elle récupère la ligne suivante d'un ensemble de résultats de requête. Un ensemble de résultats est un objet qui est renvoyé lorsqu'un objet curseur est utilisé pour interroger une table.
- ```fetchall()``` - Elle récupère toutes les lignes d'un ensemble de résultats. Si certaines lignes ont déjà été extraites du jeu de résultats, elle récupère les lignes restantes du jeu de résultats.
- ```rowcount``` - Il s'agit d'un attribut en lecture seule qui renvoie le nombre de lignes qui ont été affectées par une méthode ```execute()```.

### Exemple

La procédure suivante interroge tous les enregistrements de la table EMPLOYEE dont le salaire est supérieur à 1000 :

```python
#!/usr/bin/python3

import pymysql

# Open database connection
db = pymysql.connect("localhost", "testuser", "test123", "TESTDB")

# prepare a cursor object using cursor() method
cursor = db.cursor()

# Prepare SQL query to INSERT a record into the database.
sql = "SELECT * FROM EMPLOYEE \
        WHERE INCOME > '%d'" % (1000)
try:
    # Execute the SQL command
    cursor.execute(sql)
    # Fetch all the rows in a list of lists.
    results = cursor.fetchall()
    for row in results:
        fname = row[0]
        lname = row[1]
        age = row[2]
        sex = row[3]
        income = row[4]
        # Now print fetched result
        print("fname = %s, lname = %s, age = %d, sex = %s, income = %d" % \
            (fname, lname, age, sex, income ))
except:
    print("Error: unable to fetch data")

# disconnect from server
db.close()
```

### Sortie

Cela donnera le résultat suivant :

```bash
fname = Mac, lname = Mohan, age = 20, sex = M, income = 2000
```

## Opération de mise à jour

L'opération de mise à jour d'une base de données permet de mettre à jour un ou plusieurs enregistrements déjà disponibles dans la base.

La procédure suivante met à jour tous les enregistrements dont le SEXE est 'M'. Ici, nous augmentons l'AGE de tous les hommes d'une année.

### Exemple

```python
#!/usr/bin/python3

import pymysql

# Open database connection
db = pymysql.connect("localhost", "testuser", "test123", "TESTDB")

# prepare a cursor object using cursor() method
cursor = db.cursor()

# Prepare SQL query to UPDATE required records
sql = "UPDATE EMPLOYEE SET AGE = AGE + 1
                            WHERE SEX = '%c'" % ('M')
try:
    # Execute the SQL command
    cursor.execute(sql)
    # Commit your changes in the database
    db.commit()
except:
    # Rollback in case there is any error
    db.rollback()

# disconnect from server
db.close()
```

## Opération DELETE

L'opération DELETE est nécessaire lorsque vous souhaitez supprimer certains enregistrements de votre base de données. Voici la procédure à suivre pour supprimer tous les enregistrements de EMPLOYEE dont l'âge est supérieur à 20 ans :

### Exemple

```python
#!/usr/bin/python3

import pymysql

# Open database connection
db = pymysql.connect("localhost", "testuser", "test123", "TESTDB")

# prepare a cursor object using cursor() method
cursor = db.cursor()

# Prepare SQL query to DELETE required records
sql = "DELETE FROM EMPLOYEE WHERE AGE > '%d'" % (20)
try:
    # Execute the SQL command
    cursor.execute(sql)
    # Commit your changes in the database
    db.commit()
except:
    # Rollback in case there is any error
    db.rollback()

# disconnect from server
db.close()
```

## Transactions en cours

Les transactions sont un mécanisme qui assure la cohérence des données. Les transactions ont les quatre propriétés suivantes :

- **Atomicité** - Soit une transaction se termine, soit il ne se passe rien du tout.
- **Cohérence** - Une transaction doit commencer dans un état cohérent et quitter le système dans un état cohérent.
- **Isolation** - Les résultats intermédiaires d'une transaction ne sont pas visibles en dehors de la transaction en cours.
- **Durabilité** - Une fois qu'une transaction a été engagée, ses effets sont persistants, même après une panne du système.

L'API Python DB 2.0 fournit deux méthodes pour valider ou annuler une transaction.

### Exemple

Vous savez déjà comment mettre en œuvre des transactions. Voici un exemple similaire :

```python
# Prepare SQL query to DELETE required records
sql = "DELETE FROM EMPLOYEE WHERE AGE > '%d'" % (20)
try:
    # Execute the SQL command
    cursor.execute(sql)
    # Commit your changes in the database
    db.commit()
except:
    # Rollback in case there is any error
    db.rollback()
```

## Opération COMMIT

Commit est une opération qui donne un signal vert à la base de données pour finaliser les changements, et après cette opération, aucun changement ne peut être annulé.

Voici un exemple simple pour appeler la méthode commit.

```python
db.commit()
```

## Opération ROLLBACK

Si vous n'êtes pas satisfait d'un ou plusieurs changements et que vous souhaitez revenir en arrière, utilisez la méthode ```rollback()```.

Voici un exemple simple pour appeler la méthode ```rollback()```.

```python
db.rollback()
```

## Déconnexion de la base de données

Pour déconnecter la connexion à la base de données, utilisez la méthode ```close()```.

```python
db.close()
```

Si la connexion à une base de données est fermée par l'utilisateur avec la méthode ```close()```, toutes les transactions en cours sont annulées par la base de données. Cependant, au lieu de dépendre des détails d'implémentation de niveau inférieur de la base de données, votre application ferait mieux d'appeler explicitement commit ou rollback.

## Traitement des erreurs

Les sources d'erreurs sont nombreuses. Quelques exemples sont une erreur de syntaxe dans une instruction SQL exécutée, un échec de connexion, ou l'appel de la méthode ```fetch``` pour un handle d'instruction déjà annulé ou terminé.

L'API DB définit un certain nombre d'erreurs qui doivent exister dans chaque module de base de données. Le tableau suivant répertorie ces exceptions :

- ```Warning``` : Utilisé pour les problèmes non fatals. Doit sous-classer StandardError.
- ```Error``` : Classe de base pour les erreurs. Doit sous-classer StandardError.
- ```InterfaceError``` : Utilisé pour les erreurs dans le module de base de données, pas la base de données elle-même. Doit sous-classer Error.
- ```DatabaseError``` : Utilisé pour les erreurs dans la base de données. Doit sous-classer Error.
- ```DataError``` : Sous-classe de DatabaseError qui fait référence aux erreurs dans les données.
- ```OperationalError``` : Sous-classe de DatabaseError qui fait référence à des erreurs telles que la perte d'une connexion à la base de données. Ces erreurs échappent généralement au contrôle du scripteur Python.
- ```IntegrityError``` : Sous-classe de DatabaseError pour les situations qui porteraient atteinte à l'intégrité relationnelle, comme les contraintes d'unicité ou les clés étrangères.
- ```InternalError``` : Sous-classe de DatabaseError qui fait référence à des erreurs internes au module de base de données, comme un curseur qui n'est plus actif.
- ```Programming``` : Sous-classe d'erreur de DatabaseError qui fait référence à des erreurs telles qu'un mauvais nom de table et d'autres choses qui peuvent vous être imputées sans risque.
- ```NotSupportedError``` : Sous-classe de DatabaseError qui fait référence à la tentative d'appeler une fonctionnalité non prise en charge.

Vos scripts Python devraient gérer ces erreurs, mais avant d'utiliser l'une des exceptions ci-dessus, assurez-vous que votre base MySQLdb supporte cette exception. Vous pouvez obtenir plus d'informations à leur sujet en lisant la spécification DB API 2.0.
