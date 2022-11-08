Dans ce chapitre, vous apprendrez à utiliser SQLite dans les programmes Perl.

## Installation

SQLite3 peut être intégré à Perl en utilisant le module Perl DBI, qui est un module d'accès aux bases de données pour le langage de programmation Perl. Il définit un ensemble de méthodes, de variables et de conventions qui fournissent une interface de base de données standard.

Les étapes suivantes sont simples pour installer le module DBI sur votre machine Linux/UNIX.

```bash
$ wget http://search.cpan.org/CPAN/authors/id/T/TI/TIMB/DBI-1.625.tar.gz
$ tar xvfz DBI-1.625.tar.gz
$ cd DBI-1.625
$ perl Makefile.PL
$ make
$ make install
```

Si vous avez besoin d'installer le pilote SQLite pour DBI, il peut être installé comme suit -

```bash
$ wget http://search.cpan.org/CPAN/authors/id/M/MS/MSERGEANT/DBD-SQLite-1.11.tar.gz
$ tar xvfz DBD-SQLite-1.11.tar.gz
$ cd DBD-SQLite-1.11
$ perl Makefile.PL
$ make
$ make install
```

## DBI Interface APIs

Voici les principales routines DBI, qui peuvent répondre à vos besoins pour travailler avec la base de données SQLite à partir de votre programme Perl. Si vous cherchez une application plus sophistiquée, vous pouvez consulter la documentation officielle de Perl DBI.

**API & Description**

- ```DBI->connect($data_source, "", "", \%attr)``` - Établit une connexion à la base de données, ou session, à la source de données demandée $data_source. Renvoie un objet de gestion de base de données si la connexion réussit. La source de données a la forme suivante : DBI:SQLite:dbname = 'test.db' où SQLite est le nom du pilote SQLite et test.db est le nom du fichier de base de données SQLite. Si le nom de fichier est donné sous la forme ':memory:', cela créera une base de données en mémoire dans la RAM qui ne durera que le temps de la session. Si le nom de fichier est un nom de fichier de périphérique réel, alors il tente d'ouvrir le fichier de base de données en utilisant sa valeur. Si aucun fichier de ce nom n'existe, alors un nouveau fichier de base de données de ce nom est créé. Vous gardez les deuxième et troisième paramètres comme des chaînes vides et le dernier paramètre sert à passer divers attributs comme indiqué dans l'exemple suivant.
- ```$dbh->do($sql)``` - Cette routine prépare et exécute une seule instruction SQL. Elle retourne le nombre de lignes affectées ou undef en cas d'erreur. Une valeur de retour de -1 signifie que le nombre de lignes n'est pas connu, pas applicable, ou pas disponible. Ici, $dbh est un handle retourné par l'appel DBI->connect().
- ```$dbh->prepare($sql)``` - Cette routine prépare une déclaration pour une exécution ultérieure par le moteur de base de données et renvoie une référence à un objet de gestion de déclaration.
- ```$sth->execute()``` - Cette routine effectue tout traitement nécessaire à l'exécution de l'instruction préparée. Undef est retourné si une erreur se produit. Une exécution réussie renvoie toujours true, quel que soit le nombre de lignes concernées. Ici, $sth est un handle d'instruction retourné par l'appel $dbh->prepare($sql).
- ```$sth->fetchrow_array()``` - Cette routine récupère la ligne de données suivante et la renvoie sous la forme d'une liste contenant les valeurs des champs. Les champs nuls sont retournés sous forme de valeurs undef dans la liste.
- ```$DBI::err``` - Ceci est équivalent à $h->err, où $h est un des types de handle comme $dbh, $sth, ou $drh. Cela renvoie le code d'erreur du moteur de base de données natif de la dernière méthode du pilote appelée.
- ```$DBI::errstr``` - Ceci est équivalent à $h->errstr, où $h est un des types de handle comme $dbh, $sth, ou $drh. Ceci renvoie le message d'erreur du moteur de base de données natif de la dernière méthode DBI appelée.
- ```$dbh->disconnect()``` - Cette routine ferme une connexion à une base de données précédemment ouverte par un appel à ```DBI->connect()```.

## Connexion à la base de données

Le code Perl suivant montre comment se connecter à une base de données existante. Si la base de données n'existe pas, elle sera créée et finalement un objet de base de données sera retourné.

```perl
#!/usr/bin/perl

use DBI;
use strict;

my $driver   = "SQLite"; 
my $database = "test.db";
my $dsn = "DBI:$driver:dbname=$database";
my $userid = "";
my $password = "";
my $dbh = DBI->connect($dsn, $userid, $password, { RaiseError => 1 }) 
    or die $DBI::errstr;

print "Opened database successfully\n";
```

Maintenant, exécutons le programme ci-dessus pour créer notre base de données test.db dans le répertoire courant. Vous pouvez changer votre chemin selon vos besoins. Gardez le code ci-dessus dans le fichier sqlite.pl et exécutez-le comme indiqué ci-dessous. Si la base de données est créée avec succès, le message suivant s'affichera -

```bash
$ chmod +x sqlite.pl
$ ./sqlite.pl
Open database successfully
```

## Créer un tableau

Le programme Perl suivant est utilisé pour créer une table dans la base de données précédemment créée.

```perl
#!/usr/bin/perl

use DBI;
use strict;

my $driver   = "SQLite";
my $database = "test.db";
my $dsn = "DBI:$driver:dbname=$database";
my $userid = "";
my $password = "";
my $dbh = DBI->connect($dsn, $userid, $password, { RaiseError => 1 })
    or die $DBI::errstr;
print "Opened database successfully\n";

my $stmt = qq(CREATE TABLE COMPANY
    (ID INT PRIMARY KEY     NOT NULL,
        NAME           TEXT    NOT NULL,
        AGE            INT     NOT NULL,
        ADDRESS        CHAR(50),
        SALARY         REAL););

my $rv = $dbh->do($stmt);
if($rv < 0) {
    print $DBI::errstr;
} else {
    print "Table created successfully\n";
}
$dbh->disconnect();
```

Lorsque le programme ci-dessus est exécuté, il créera la table COMPANY dans votre test.db et il affichera les messages suivants -

```bash
Opened database successfully
Table created successfully
```

__Remarque__ - Si vous voyez l'erreur suivante dans l'une des opérations :

```bash
DBD::SQLite::st execute failed: not an error(21) at dbdimp.c line 398
```

Dans ce cas, ouvrez le fichier ```dbdimp.c``` file disponible dans l'installation de DBD-SQLite et trouvez la fonction ```sqlite3_prepare()``` et changez son troisième argument en ```-1``` au lieu de ```0```. Enfin, installez ```DBD::SQLite``` en utilisant make et faites make install pour résoudre le problème.

## Opération INSERT

Le programme Perl suivant montre comment créer des enregistrements dans la table SOCIÉTÉ créée dans l'exemple ci-dessus.

```perl
#!/usr/bin/perl

use DBI;
use strict;

my $driver   = "SQLite";
my $database = "test.db";
my $dsn = "DBI:$driver:dbname=$database";
my $userid = "";
my $password = "";
my $dbh = DBI->connect($dsn, $userid, $password, { RaiseError => 1 })
    or die $DBI::errstr;
print "Opened database successfully\n";

my $stmt = qq(INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
                VALUES (1, 'Paul', 32, 'California', 20000.00 ));
my $rv = $dbh->do($stmt) or die $DBI::errstr;

$stmt = qq(INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
                VALUES (2, 'Allen', 25, 'Texas', 15000.00 ));
$rv = $dbh->do($stmt) or die $DBI::errstr;

$stmt = qq(INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
                VALUES (3, 'Teddy', 23, 'Norway', 20000.00 ));

$rv = $dbh->do($stmt) or die $DBI::errstr;

$stmt = qq(INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
                VALUES (4, 'Mark', 25, 'Rich-Mond ', 65000.00 ););

$rv = $dbh->do($stmt) or die $DBI::errstr;

print "Records created successfully\n";
$dbh->disconnect();
```

Lorsque le programme ci-dessus est exécuté, il créera les enregistrements donnés dans la table SOCIÉTÉ et affichera les deux lignes suivantes : - 1.

```bash
Opened database successfully
Records created successfully
```

## Opération SELECT

Le programme Perl suivant montre comment récupérer et afficher les enregistrements de la table SOCIÉTÉ créée dans l'exemple ci-dessus.

```perl
#!/usr/bin/perl

use DBI;
use strict;

my $driver = "SQLite";
my $database = "test.db";
my $dsn = "DBI:$driver:dbname=$database";
my $userid = "";
my $password = "";
my $dbh = DBI->connect($dsn, $userid, $password, { RaiseError => 1 })
    or die $DBI::errstr;
print "Opened database successfully\n";

my $stmt = qq(SELECT id, name, address, salary from COMPANY;);
my $sth = $dbh->prepare( $stmt );
my $rv = $sth->execute() or die $DBI::errstr;

if($rv < 0) {
    print $DBI::errstr;
}

while(my @row = $sth->fetchrow_array()) {
        print "ID = ". $row[0] . "\n";
        print "NAME = ". $row[1] ."\n";
        print "ADDRESS = ". $row[2] ."\n";
        print "SALARY =  ". $row[3] ."\n\n";
}
print "Operation done successfully\n";
$dbh->disconnect();
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant.

```bash
Opened database successfully
ID = 1
NAME = Paul
ADDRESS = California
SALARY =  20000

ID = 2
NAME = Allen
ADDRESS = Texas
SALARY =  15000

ID = 3
NAME = Teddy
ADDRESS = Norway
SALARY =  20000

ID = 4
NAME = Mark
ADDRESS = Rich-Mond
SALARY =  65000

Operation done successfully
```

## Opération UPDATE

Le code Perl suivant montre comment utiliser l'instruction UPDATE pour mettre à jour un enregistrement, puis récupérer et afficher les enregistrements mis à jour dans la table COMPANY.

```perl
#!/usr/bin/perl

use DBI;
use strict;

my $driver   = "SQLite";
my $database = "test.db";
my $dsn = "DBI:$driver:dbname=$database";
my $userid = "";
my $password = "";
my $dbh = DBI->connect($dsn, $userid, $password, { RaiseError => 1 })
    or die $DBI::errstr;
print "Opened database successfully\n";

my $stmt = qq(UPDATE COMPANY set SALARY = 25000.00 where ID=1;);
my $rv = $dbh->do($stmt) or die $DBI::errstr;

if( $rv < 0 ) {
    print $DBI::errstr;
} else {
    print "Total number of rows updated : $rv\n";
}
$stmt = qq(SELECT id, name, address, salary from COMPANY;);
my $sth = $dbh->prepare( $stmt );
$rv = $sth->execute() or die $DBI::errstr;

if($rv < 0) {
    print $DBI::errstr;
}

while(my @row = $sth->fetchrow_array()) {
        print "ID = ". $row[0] . "\n";
        print "NAME = ". $row[1] ."\n";
        print "ADDRESS = ". $row[2] ."\n";
        print "SALARY =  ". $row[3] ."\n\n";
}
print "Operation done successfully\n";
$dbh->disconnect();
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant.

```bash
Opened database successfully
Total number of rows updated : 1
ID = 1
NAME = Paul
ADDRESS = California
SALARY =  25000

ID = 2
NAME = Allen
ADDRESS = Texas
SALARY =  15000

ID = 3
NAME = Teddy
ADDRESS = Norway
SALARY =  20000

ID = 4
NAME = Mark
ADDRESS = Rich-Mond
SALARY =  65000

Operation done successfully
```

## Opération DELETE

Le code Perl suivant montre comment utiliser l'instruction DELETE pour supprimer un enregistrement, puis récupérer et afficher les enregistrements restants dans la table COMPANY.

```perl
#!/usr/bin/perl

use DBI;
use strict;

my $driver   = "SQLite";
my $database = "test.db";
my $dsn = "DBI:$driver:dbname=$database";
my $userid = "";
my $password = "";
my $dbh = DBI->connect($dsn, $userid, $password, { RaiseError => 1 })
    or die $DBI::errstr;
print "Opened database successfully\n";

my $stmt = qq(DELETE from COMPANY where ID = 2;);
my $rv = $dbh->do($stmt) or die $DBI::errstr;

if( $rv < 0 ) {
    print $DBI::errstr;
} else {
    print "Total number of rows deleted : $rv\n";
}

$stmt = qq(SELECT id, name, address, salary from COMPANY;);
my $sth = $dbh->prepare( $stmt );
$rv = $sth->execute() or die $DBI::errstr;

if($rv < 0) {
    print $DBI::errstr;
}

while(my @row = $sth->fetchrow_array()) {
    print "ID = ". $row[0] . "\n";
    print "NAME = ". $row[1] ."\n";
    print "ADDRESS = ". $row[2] ."\n";
    print "SALARY =  ". $row[3] ."\n\n";
}
print "Operation done successfully\n";
$dbh->disconnect();
```

Lorsque le programme ci-dessus est exécuté, il produit le résultat suivant.

```bash
Opened database successfully
Total number of rows deleted : 1
ID = 1
NAME = Paul
ADDRESS = California
SALARY = 25000

ID = 3
NAME = Teddy
ADDRESS = Norway
SALARY = 20000

ID = 4
NAME = Mark
ADDRESS = Rich-Mond
SALARY = 65000

Operation done successfully
```