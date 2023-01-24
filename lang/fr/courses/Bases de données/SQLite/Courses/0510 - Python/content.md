Dans ce chapitre, vous apprendrez à utiliser SQLite dans les programmes Python.

## Installation

SQLite3 peut être intégré à Python en utilisant le module sqlite3, qui a été écrit par Gerhard Haring. Il fournit une interface SQL conforme à la spécification DB-API 2.0 décrite par le PEP 249. Vous n'avez pas besoin d'installer ce module séparément car il est livré par défaut avec Python à partir de la version 2.5.x.

Pour utiliser le module sqlite3, vous devez d'abord créer un objet de connexion qui représente la base de données et ensuite, en option, vous pouvez créer un objet curseur, qui vous aidera à exécuter toutes les instructions SQL.

## APIs du module sqlite3 en Python

Voici les principales routines du module sqlite3, qui peuvent répondre à vos besoins pour travailler avec la base de données SQLite depuis votre programme Python. Si vous cherchez une application plus sophistiquée, vous pouvez consulter la documentation officielle du module sqlite3 de Python.

**API & Description**

- ```sqlite3.connect(database [,timeout ,other optional arguments])``` - Cette API ouvre une connexion au fichier de la base de données SQLite. Vous pouvez utiliser ":memory :" pour ouvrir une connexion à une base de données qui réside dans la RAM plutôt que sur le disque. Si la base de données est ouverte avec succès, elle renvoie un objet de connexion. Lorsqu'une base de données est accessible par plusieurs connexions, et que l'un des processus modifie la base de données, la base de données SQLite est verrouillée jusqu'à ce que la transaction soit validée. Le paramètre timeout spécifie combien de temps la connexion doit attendre que le verrou disparaisse avant de lever une exception. La valeur par défaut du paramètre timeout est 5.0 (cinq secondes). Si le nom de base de données donné n'existe pas, cet appel créera la base de données. Vous pouvez également spécifier filename avec le chemin d'accès requis si vous souhaitez créer une base de données ailleurs que dans le répertoire actuel.
- ```connection.cursor([cursorClass])``` - Cette routine crée un curseur qui sera utilisé tout au long de votre programmation de base de données avec Python. Cette méthode accepte un seul paramètre optionnel cursorClass. S'il est fourni, il doit s'agir d'une classe de curseur personnalisée qui étend sqlite3. Cursor.
- ```cursor.execute(sql [, optional parameters])``` - Cette routine exécute une instruction SQL. L'instruction SQL peut être paramétrée (i.e. des caractères de remplacement au lieu de littéraux SQL). Le module sqlite3 supporte deux types de placeholders : les points d'interrogation et les placeholders nommés (style nommé). Par exemple - ```cursor.execute("insert into people values (?, ?)", (who, âge))```
- ```connection.execute(sql [, optional parameters])``` - Cette routine est un raccourci de la méthode execute ci-dessus fournie par l'objet curseur. Elle crée un objet curseur intermédiaire en appelant la méthode cursor, puis appelle la méthode execute du curseur avec les paramètres donnés.
- ```cursor.executemany(sql, seq_of_parameters)``` - Cette routine exécute une commande SQL contre toutes les séquences de paramètres ou les mappings trouvés dans la séquence sql.
- ```connection.executemany(sql[, parameters])``` - Cette routine est un raccourci qui crée un objet curseur intermédiaire en appelant la méthode cursor, puis appelle la méthode execute many du curseur avec les paramètres donnés.
- ```cursor.executescript(sql_script)``` - Cette routine exécute plusieurs instructions SQL à la fois fournies sous forme de script. Elle émet d'abord une déclaration COMMIT, puis exécute le script SQL qu'elle reçoit en paramètre. Toutes les instructions SQL doivent être séparées par un point-virgule (;).
- ```connection.executescript(sql_script)``` - Cette routine est un raccourci qui crée un objet curseur intermédiaire en appelant la méthode cursor, puis appelle la méthode executescript du curseur avec les paramètres donnés.
- ```connection.total_changes()``` - Cette routine renvoie le nombre total de lignes de la base de données qui ont été modifiées, insérées ou supprimées depuis l'ouverture de la connexion à la base de données.
- ```connection.commit()``` - Cette méthode permet de valider la transaction en cours. Si vous n'appelez pas cette méthode, tout ce que vous avez fait depuis le dernier appel à commit() n'est pas visible depuis les autres connexions à la base de données.
- ```connection.rollback()``` - Cette méthode annule toutes les modifications apportées à la base de données depuis le dernier appel à ```commit()```.
- ```connection.close()``` - Cette méthode ferme la connexion à la base de données. Notez que cette méthode n'appelle pas automatiquement ```commit()```. Si vous fermez simplement votre connexion à la base de données sans appeler ```commit()``` au préalable, vos modifications seront perdues !
- ```cursor.fetchone()``` - Cette méthode récupère la ligne suivante d'un ensemble de résultats de requête, renvoyant une seule séquence, ou None lorsque plus aucune donnée n'est disponible.
- ```cursor.fetchmany([size = cursor.arraysize])``` - Cette routine récupère le prochain ensemble de lignes d'un résultat de requête, en retournant une liste. Une liste vide est retournée lorsqu'il n'y a plus de lignes disponibles. La méthode essaie de récupérer autant de lignes qu'indiqué par le paramètre size.
- ```cursor.fetchall()``` - Cette routine récupère toutes les lignes (restantes) du résultat d'une requête et renvoie une liste. Une liste vide est retournée si aucune ligne n'est disponible.

## Connexion à la base de données

Le code Python suivant montre comment se connecter à une base de données existante. Si la base de données n'existe pas, elle sera créée et un objet de base de données sera retourné.

```python
#!/usr/bin/python

import sqlite3

conn = sqlite3.connect('test.db')

print "Opened database successfully";
```

Ici, vous pouvez également fournir le nom de la base de données comme nom spécial :memory : pour créer une base de données en RAM. Maintenant, exécutons le programme ci-dessus pour créer notre base de données test.db dans le répertoire courant. Vous pouvez changer votre chemin selon vos besoins. Gardez le code ci-dessus dans le fichier sqlite.py et exécutez-le comme indiqué ci-dessous. Si la base de données est créée avec succès, alors le message suivant s'affichera.

```bash
$chmod +x sqlite.py
$./sqlite.py
Open database successfully
```

## Créer un tableau

Le programme Python suivant sera utilisé pour créer une table dans la base de données précédemment créée.

```python
#!/usr/bin/python

import sqlite3

conn = sqlite3.connect('test.db')
print "Opened database successfully";

conn.execute('''CREATE TABLE COMPANY
            (ID INT PRIMARY KEY     NOT NULL,
            NAME           TEXT    NOT NULL,
            AGE            INT     NOT NULL,
            ADDRESS        CHAR(50),
            SALARY         REAL);''')
print "Table created successfully";

conn.close()
```

Lorsque le programme ci-dessus est exécuté, il créera la table COMPANY dans votre **test.db** et il affichera les messages suivants -

```bash
Opened database successfully
Table created successfully
```

## Opération INSERT

Le programme Python suivant montre comment créer des enregistrements dans la table COMPANY créée dans l'exemple ci-dessus.

```python
#!/usr/bin/python

import sqlite3

conn = sqlite3.connect('test.db')
print "Opened database successfully";

conn.execute("INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) \
        VALUES (1, 'Paul', 32, 'California', 20000.00 )");

conn.execute("INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) \
        VALUES (2, 'Allen', 25, 'Texas', 15000.00 )");

conn.execute("INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) \
        VALUES (3, 'Teddy', 23, 'Norway', 20000.00 )");

conn.execute("INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) \
        VALUES (4, 'Mark', 25, 'Rich-Mond ', 65000.00 )");

conn.commit()
print "Records created successfully";
conn.close()
```

Lorsque le programme ci-dessus est exécuté, il créera les enregistrements donnés dans la table SOCIÉTÉ et affichera les deux lignes suivantes : - 1.

```bash
Opened database successfully
Records created successfully
```

## Opération SELECT

Le programme Python suivant montre comment récupérer et afficher les enregistrements de la table SOCIÉTÉ créée dans l'exemple ci-dessus.

```python
#!/usr/bin/python

import sqlite3

conn = sqlite3.connect('test.db')
print "Opened database successfully";

cursor = conn.execute("SELECT id, name, address, salary from COMPANY")
for row in cursor:
    print "ID = ", row[0]
    print "NAME = ", row[1]
    print "ADDRESS = ", row[2]
    print "SALARY = ", row[3], "\n"

print "Operation done successfully";
conn.close()
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant.

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

Le code Python suivant montre comment utiliser l'instruction UPDATE pour mettre à jour un enregistrement, puis récupérer et afficher les enregistrements mis à jour dans la table COMPANY.

```python
#!/usr/bin/python

import sqlite3

conn = sqlite3.connect('test.db')
print "Opened database successfully";

conn.execute("UPDATE COMPANY set SALARY = 25000.00 where ID = 1")
conn.commit()
print "Total number of rows updated :", conn.total_changes

cursor = conn.execute("SELECT id, name, address, salary from COMPANY")
for row in cursor:
    print "ID = ", row[0]
    print "NAME = ", row[1]
    print "ADDRESS = ", row[2]
    print "SALARY = ", row[3], "\n"

print "Operation done successfully";
conn.close()
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant.

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

Le code Python suivant montre comment utiliser l'instruction DELETE pour supprimer un enregistrement, puis récupérer et afficher les enregistrements restants dans la table COMPANY.

```python
#!/usr/bin/python

import sqlite3

conn = sqlite3.connect('test.db')
print "Opened database successfully";

conn.execute("DELETE from COMPANY where ID = 2;")
conn.commit()
print "Total number of rows deleted :", conn.total_changes

cursor = conn.execute("SELECT id, name, address, salary from COMPANY")
for row in cursor:
    print "ID = ", row[0]
    print "NAME = ", row[1]
    print "ADDRESS = ", row[2]
    print "SALARY = ", row[3], "\n"

print "Operation done successfully";
conn.close()
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant.

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
