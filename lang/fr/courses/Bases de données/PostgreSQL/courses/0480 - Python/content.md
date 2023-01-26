## Installation

Le PostgreSQL peut être intégré à Python à l'aide du module psycopg2. psycopg2 est un adaptateur de base de données PostgreSQL pour le langage de programmation Python. psycopg2 a été écrit dans le but d'être très petit et rapide, et stable comme un roc. Vous n'avez pas besoin d'installer ce module séparément car il est livré, par défaut, avec la version 2.5.x et suivantes de Python.

Si vous ne l'avez pas installé sur votre machine, vous pouvez utiliser la commande yum pour l'installer de la manière suivante :

```bash
$yum install python-psycopg2
```

Pour utiliser le module psycopg2, vous devez d'abord créer un objet Connexion qui représente la base de données et ensuite, en option, vous pouvez créer un objet Curseur qui vous aidera à exécuter toutes les instructions SQL.

## Python psycopg2 module APIs

Voici les principales routines du module psycopg2, qui peuvent répondre à votre besoin de travailler avec la base de données PostgreSQL depuis votre programme Python. Si vous cherchez une application plus sophistiquée, vous pouvez consulter la documentation officielle du module Python psycopg2.

**API & Description**

- ```psycopg2.connect(database="testdb", user="postgres", password="cohondob", host="127.0.0.1", port="5432")``` - Cette API ouvre une connexion à la base de données PostgreSQL. Si la base de données est ouverte avec succès, elle renvoie un objet de connexion.
- ```connection.cursor()``` - Cette routine crée un curseur qui sera utilisé tout au long de votre programmation de base de données avec Python.
- ```cursor.execute(sql [, optional parameters])``` - Cette routine exécute une instruction SQL. L'instruction SQL peut être paramétrée (c'est-à-dire des placeholders au lieu de littéraux SQL). Le module psycopg2 supporte les placeholders en utilisant le signe %s. Par exemple : ```cursor.execute("insert into people values (%s, %s)", (who, age))```.
- ```cursor.executemany(sql, seq_of_parameters)``` - Cette routine exécute une commande SQL contre toutes les séquences de paramètres ou les mappings trouvés dans la séquence sql.
- ```cursor.callproc(procname[, parameters])``` - Cette routine exécute une procédure de base de données stockée avec le nom donné. La séquence de paramètres doit contenir une entrée pour chaque argument attendu par la procédure.
- ```cursor.rowcount``` - Cet attribut en lecture seule renvoie le nombre total de lignes de la base de données qui ont été modifiées, insérées ou supprimées par le dernier ```execute()```.
- ```connection.commit()``` - Cette méthode permet de valider la transaction en cours. Si vous n'appelez pas cette méthode, tout ce que vous avez fait depuis le dernier appel à ```commit()``` n'est pas visible depuis les autres connexions à la base de données.
- ```connection.rollback()``` - Cette méthode annule toutes les modifications apportées à la base de données depuis le dernier appel à ```commit()```.
- ```connection.close()``` - Notez que cette méthode n'appelle pas automatiquement ```commit()```. Si vous fermez simplement votre connexion à la base de données sans appeler ```commit()``` au préalable, vos modifications seront perdues !
- ```cursor.fetchone()``` - Cette méthode récupère la ligne suivante d'un ensemble de résultats de requête, renvoyant une seule séquence, ou None lorsque plus aucune donnée n'est disponible.
- ```cursor.fetchmany([size=cursor.arraysize])``` - Cette routine récupère le prochain ensemble de lignes d'un résultat de requête, en retournant une liste. Une liste vide est retournée lorsqu'il n'y a plus de lignes disponibles. La méthode essaie de récupérer autant de lignes qu'indiqué par le paramètre size.
- ```cursor.fetchall()``` - Cette routine récupère toutes les lignes (restantes) du résultat d'une requête et renvoie une liste. Une liste vide est retournée si aucune ligne n'est disponible.

## Connection à la base de données

Le code Python suivant montre comment se connecter à une base de données existante. Si la base de données n'existe pas, elle sera créée et finalement un objet de base de données sera retourné :

```python
#!/usr/bin/python

import psycopg2

conn = psycopg2.connect(database="testdb", user="postgres", password="pass123", host="127.0.0.1", port="5432")

print("Opened database successfully")
```

Ici, vous pouvez également fournir la base de données testdb comme nom et si la base de données est ouverte avec succès, alors il donnera le message suivant :

```bash
Open database successfully
```

## Create a Table

Le programme Python suivant sera utilisé pour créer une table dans la base de données créée précédemment :

```python
#!/usr/bin/python

import psycopg2

conn = psycopg2.connect(database="testdb", user="postgres", password="pass123", host="127.0.0.1", port="5432")
print("Opened database successfully")

cur = conn.cursor()
cur.execute('''CREATE TABLE COMPANY
        (ID INT PRIMARY KEY     NOT NULL,
        NAME           TEXT    NOT NULL,
        AGE            INT     NOT NULL,
        ADDRESS        CHAR(50),
        SALARY         REAL);''')
print("Table created successfully")

conn.commit()
conn.close()
```

Lorsque le programme donné ci-dessus est exécuté, il créera la table COMPANY dans votre test.db et il affichera les messages suivants :

```bash
Opened database successfully
Table created successfully
```

## Opération INSERT

Le programme Python suivant montre comment nous pouvons créer des enregistrements dans notre table SOCIÉTÉ créée dans l'exemple ci-dessus :

```python
#!/usr/bin/python

import psycopg2

conn = psycopg2.connect(database="testdb", user="postgres", password="pass123", host="127.0.0.1", port="5432")
print("Opened database successfully")

cur = conn.cursor()

cur.execute("INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) \
        VALUES (1, 'Paul', 32, 'California', 20000.00 )")

cur.execute("INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) \
        VALUES (2, 'Allen', 25, 'Texas', 15000.00 )")

cur.execute("INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) \
        VALUES (3, 'Teddy', 23, 'Norway', 20000.00 )")

cur.execute("INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) \
        VALUES (4, 'Mark', 25, 'Rich-Mond ', 65000.00 )")

conn.commit()
print("Records created successfully")
conn.close()
```

Lorsque le programme ci-dessus est exécuté, il créera des enregistrements donnés dans la table COMPANY et affichera les deux lignes suivantes :

```bash
Opened database successfully
Records created successfully
```

## Opération SELECT

Le programme Python suivant montre comment nous pouvons récupérer et afficher les enregistrements de notre table SOCIÉTÉ créée dans l'exemple ci-dessus :

```python
#!/usr/bin/python

import psycopg2

conn = psycopg2.connect(database="testdb", user="postgres", password="pass123", host="127.0.0.1", port="5432")
print("Opened database successfully")

cur = conn.cursor()

cur.execute("SELECT id, name, address, salary from COMPANY")
rows = cur.fetchall()
for row in rows:
    print("ID =", row[0])
    print("NAME =", row[1])
    print("ADDRESS =", row[2])
    print("SALARY =", row[3], "\n")

print("Operation done successfully")
conn.close()
```

Lorsque le programme donné ci-dessus est exécuté, il produira le résultat suivant :

```bash
Opened database successfully
ID = 1
NAME = Paul
ADDRESS = California
SALARY = 20000.0

ID = 2
NAME = Allen
ADDRESS = Texas
SALARY = 15000.0

ID = 3
NAME = Teddy
ADDRESS = Norway
SALARY = 20000.0

ID = 4
NAME = Mark
ADDRESS = Rich-Mond
SALARY = 65000.0

Operation done successfully
```

## Opération UPDATE

Le code Python suivant montre comment utiliser l'instruction UPDATE pour mettre à jour n'importe quel enregistrement, puis récupérer et afficher les enregistrements mis à jour dans la table COMPANY :

```python
#!/usr/bin/python

import psycopg2

conn = psycopg2.connect(database="testdb", user="postgres", password="pass123", host="127.0.0.1", port="5432")
print "Opened database successfully"

cur = conn.cursor()

cur.execute("UPDATE COMPANY set SALARY = 25000.00 where ID = 1")
conn.commit()
print("Total number of rows updated :", cur.rowcount)

cur.execute("SELECT id, name, address, salary from COMPANY")
rows = cur.fetchall()
for row in rows:
    print("ID =", row[0])
    print("NAME =", row[1])
    print("ADDRESS =", row[2])
    print("SALARY =", row[3], "\n")

print("Operation done successfully")
conn.close()
```

Lorsque le programme donné ci-dessus est exécuté, il produira le résultat suivant -

```bash
Opened database successfully
Total number of rows updated : 1
ID = 1
NAME = Paul
ADDRESS = California
SALARY = 25000.0

ID = 2
NAME = Allen
ADDRESS = Texas
SALARY = 15000.0

ID = 3
NAME = Teddy
ADDRESS = Norway
SALARY = 20000.0

ID = 4
NAME = Mark
ADDRESS = Rich-Mond
SALARY = 65000.0

Operation done successfully
```

## Opération DELETE

Le code Python suivant montre comment utiliser l'instruction DELETE pour supprimer un enregistrement, puis récupérer et afficher les enregistrements restants dans la table COMPANY :

```python
#!/usr/bin/python

import psycopg2

conn = psycopg2.connect(database="testdb", user="postgres", password="pass123", host="127.0.0.1", port="5432")
print("Opened database successfully")

cur = conn.cursor()

cur.execute("DELETE from COMPANY where ID=2;")
conn.commit()
print("Total number of rows deleted :", cur.rowcount)

cur.execute("SELECT id, name, address, salary from COMPANY")
rows = cur.fetchall()
for row in rows:
    print("ID =", row[0])
    print("NAME =", row[1])
    print("ADDRESS =", row[2])
    print("SALARY =", row[3], "\n")

print("Operation done successfully")
conn.close()
```

Lorsque le programme donné ci-dessus est exécuté, il produira le résultat suivant :

```bash
Opened database successfully
Total number of rows deleted : 1
ID = 1
NAME = Paul
ADDRESS = California
SALARY = 20000.0

ID = 3
NAME = Teddy
ADDRESS = Norway
SALARY = 20000.0

ID = 4
NAME = Mark
ADDRESS = Rich-Mond
SALARY = 65000.0

Operation done successfully
```
