## Installation

PostgreSQL peut être intégré à Perl en utilisant le module Perl DBI, qui est un module d'accès aux bases de données pour le langage de programmation Perl. Il définit un ensemble de méthodes, de variables et de conventions qui fournissent une interface standard de base de données.

Voici les étapes simples pour installer le module DBI sur votre machine Linux/Unix.

```bash
$ wget http://search.cpan.org/CPAN/authors/id/T/TI/TIMB/DBI-1.625.tar.gz
$ tar xvfz DBI-1.625.tar.gz
$ cd DBI-1.625
$ perl Makefile.PL
$ make
$ make install
```

Si vous avez besoin d'installer le pilote SQLite pour DBI, il peut être installé comme suit :

```bash
$ wget http://search.cpan.org/CPAN/authors/id/T/TU/TURNSTEP/DBD-Pg-2.19.3.tar.gz
$ tar xvfz DBD-Pg-2.19.3.tar.gz
$ cd DBD-Pg-2.19.3
$ perl Makefile.PL
$ make
$ make install
```

Avant de commencer à utiliser l'interface Perl PostgreSQL, trouvez le fichier pg_hba.conf dans votre répertoire d'installation PostgreSQL et ajoutez la ligne suivante :

```bash
# IPv4 local connections:
host    all         all         127.0.0.1/32          md5
```

Vous pouvez démarrer/redémarrer le serveur postgres, au cas où il ne serait pas en cours d'exécution, à l'aide de la commande suivante :

```bash
[root@host]# service postgresql restart
Stopping postgresql service:                               [  OK  ]
Starting postgresql service:                               [  OK  ]
```

## DBI Interface APIs

Voici les principales routines DBI, qui peuvent répondre à vos besoins pour travailler avec la base de données SQLite depuis votre programme Perl. Si vous cherchez une application plus sophistiquée, vous pouvez consulter la documentation officielle de Perl DBI.

**API & Description**

- ```DBI→connect($data_source, "userid", "password", \%attr)``` - Établis une connexion à la base de données, ou session, à la source de données demandée $data_source. Retourne un objet handle de base de données si la connexion réussit. Datasource à la forme suivante : ```DBI:Pg:dbname=$database;host=127.0.0.1;port=5432``` Pg est le nom du pilote PostgreSQL et testdb est le nom de la base de données.
- ```$dbh→do($sql)``` - Cette routine prépare et exécute une seule instruction SQL. Elle retourne le nombre de lignes affectées ou undef en cas d'erreur. Une valeur de retour de -1 signifie que le nombre de lignes est inconnu, non applicable ou non disponible. Ici, ```$dbh``` est un handle renvoyé par l'appel ```DBI→connect()```.
- ```$dbh→prepare($sql)``` - Cette routine prépare une déclaration pour une exécution ultérieure par le moteur de base de données et renvoie une référence à un objet de gestion de déclaration.
- ```$sth→execute()``` - Cette routine effectue tout traitement nécessaire à l'exécution de l'instruction préparée. Undef est retourné si une erreur se produit. Une exécution réussie renvoie toujours true, quel que soit le nombre de lignes concernées. Ici, ```$sth``` est un handle d'instruction renvoyé par l'appel ```$dbh→prepare($sql)```.
- ```$sth→fetchrow_array()``` - Cette routine récupère la ligne de données suivante et la renvoie sous la forme d'une liste contenant les valeurs des champs. Les champs nuls sont retournés sous forme de valeurs undef dans la liste.
- ```$DBI::err``` - Ceci est équivalent à ```$h→err```, où ```$h``` est l'un des types de handle comme ```$dbh```, ```$sth```, ou ```$drh```. Cela renvoie le code d'erreur natif du moteur de base de données de la dernière méthode de pilote appelée.
- ```$DBI::errstr``` - Ceci est équivalent à ```$h→errstr```, où ```$h``` est un des types de handle comme ```$dbh```, ```$sth```, ou ```$drh```. Cela renvoie le message d'erreur du moteur de base de données natif de la dernière méthode DBI appelée.
- ```$dbh->disconnect()``` - Cette routine ferme une connexion à une base de données précédemment ouverte par un appel à ```DBI→connect()```.

## Connecting to Database

Le code Perl suivant montre comment se connecter à une base de données existante. Si la base de données n'existe pas, elle sera créée et finalement un objet de base de données sera retourné :

```perl
#!/usr/bin/perl

use DBI;
use strict;

my $driver  = "Pg"; 
my $database = "testdb";
my $dsn = "DBI:$driver:dbname = $database;host = 127.0.0.1;port = 5432";
my $userid = "postgres";
my $password = "pass123";
my $dbh = DBI->connect($dsn, $userid, $password, { RaiseError => 1 }) 
    or die $DBI::errstr;

print "Opened database successfully\n";
```

Maintenant, exécutons le programme ci-dessus pour ouvrir notre base de données testdb ; si la base de données est ouverte avec succès, le message suivant s'affichera :

```bash
Open database successfully
```

## Créer une table

Le programme Perl suivant sera utilisé pour créer une table dans la base de données précédemment créée :

```perl
#!/usr/bin/perl

use DBI;
use strict;

my $driver = "Pg"; 
my $database = "testdb";
my $dsn = "DBI:$driver:dbname=$database;host=127.0.0.1;port=5432";
my $userid = "postgres";
my $password = "pass123";
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

Lorsque le programme donné ci-dessus est exécuté, il créera la table COMPANY dans votre testdb et il affichera les messages suivants :

```bash
Opened database successfully
Table created successfully
```

## Opération INSERT

Le programme Perl suivant montre comment nous pouvons créer des enregistrements dans notre table SOCIÉTÉ créée dans l'exemple ci-dessus :

```perl
#!/usr/bin/perl

use DBI;
use strict;

my $driver = "Pg"; 
my $database = "testdb";
my $dsn = "DBI:$driver:dbname = $database;host = 127.0.0.1;port = 5432";
my $userid = "postgres";
my $password = "pass123";
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

Lorsque le programme ci-dessus est exécuté, il créera des enregistrements donnés dans la table COMPANY et affichera les deux lignes suivantes :

```bash
Opened database successfully
Records created successfully
```

## Opération SELECT

Le programme Perl suivant montre comment nous pouvons récupérer et afficher les enregistrements de notre table SOCIÉTÉ créée dans l'exemple ci-dessus :

```perl
#!/usr/bin/perl

use DBI;
use strict;

my $driver = "Pg"; 
my $database = "testdb";
my $dsn = "DBI:$driver:dbname = $database;host = 127.0.0.1;port = 5432";
my $userid = "postgres";
my $password = "pass123";
my $dbh = DBI->connect($dsn, $userid, $password, { RaiseError => 1 })
    or die $DBI::errstr;
print "Opened database successfully\n";

my $stmt = qq(SELECT id, name, address, salary  from COMPANY;);
my $sth = $dbh->prepare( $stmt );
my $rv = $sth->execute() or die $DBI::errstr;
if($rv < 0) {
    print $DBI::errstr;
}
while(my @row = $sth->fetchrow_array()) {
        print "ID = ". $row[0] . "\n";
        print "NAME = ". $row[1] ."\n";
        print "ADDRESS = ". $row[2] ."\n";
        print "SALARY = ". $row[3] ."\n\n";
}
print "Operation done successfully\n";
$dbh->disconnect();
```

Lorsque le programme donné ci-dessus est exécuté, il produira le résultat suivant :

```bash
Opened database successfully
ID = 1
NAME = Paul
ADDRESS = California
SALARY = 20000

ID = 2
NAME = Allen
ADDRESS = Texas
SALARY = 15000

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

## Opération UPDATE

Le code Perl suivant montre comment utiliser l'instruction UPDATE pour mettre à jour n'importe quel enregistrement, puis récupérer et afficher les enregistrements mis à jour dans la table SOCIÉTÉ.

```perl
#!/usr/bin/perl

use DBI;
use strict;

my $driver = "Pg"; 
my $database = "testdb";
my $dsn = "DBI:$driver:dbname = $database;host = 127.0.0.1;port = 5432";
my $userid = "postgres";
my $password = "pass123";
my $dbh = DBI->connect($dsn, $userid, $password, { RaiseError => 1 })
    or die $DBI::errstr;
print "Opened database successfully\n";

my $stmt = qq(UPDATE COMPANY set SALARY = 25000.00 where ID=1;);
my $rv = $dbh->do($stmt) or die $DBI::errstr;
if( $rv < 0 ) {
    print $DBI::errstr;
}else{
    print "Total number of rows updated : $rv\n";
}
$stmt = qq(SELECT id, name, address, salary  from COMPANY;);
my $sth = $dbh->prepare( $stmt );
$rv = $sth->execute() or die $DBI::errstr;
if($rv < 0) {
    print $DBI::errstr;
}
while(my @row = $sth->fetchrow_array()) {
        print "ID = ". $row[0] . "\n";
        print "NAME = ". $row[1] ."\n";
        print "ADDRESS = ". $row[2] ."\n";
        print "SALARY = ". $row[3] ."\n\n";
}
print "Operation done successfully\n";
$dbh->disconnect();
```

Lorsque le programme donné ci-dessus est exécuté, il produira le résultat suivant :

```bash
Opened database successfully
Total number of rows updated : 1
ID = 1
NAME = Paul
ADDRESS = California
SALARY = 25000

ID = 2
NAME = Allen
ADDRESS = Texas
SALARY = 15000

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

## Opération Delete

Le code Perl suivant montre comment utiliser l'instruction DELETE pour supprimer n'importe quel enregistrement, puis récupérer et afficher les enregistrements restants dans la table COMPANY :

```perl
#!/usr/bin/perl

use DBI;
use strict;

my $driver = "Pg"; 
my $database = "testdb";
my $dsn = "DBI:$driver:dbname = $database;host = 127.0.0.1;port = 5432";
my $userid = "postgres";
my $password = "pass123";
my $dbh = DBI->connect($dsn, $userid, $password, { RaiseError => 1 })
    or die $DBI::errstr;
print "Opened database successfully\n";

my $stmt = qq(DELETE from COMPANY where ID=2;);
my $rv = $dbh->do($stmt) or die $DBI::errstr;
if( $rv < 0 ) {
    print $DBI::errstr;
} else{
    print "Total number of rows deleted : $rv\n";
}
$stmt = qq(SELECT id, name, address, salary  from COMPANY;);
my $sth = $dbh->prepare( $stmt );
$rv = $sth->execute() or die $DBI::errstr;
if($rv < 0) {
    print $DBI::errstr;
}
while(my @row = $sth->fetchrow_array()) {
        print "ID = ". $row[0] . "\n";
        print "NAME = ". $row[1] ."\n";
        print "ADDRESS = ". $row[2] ."\n";
        print "SALARY = ". $row[3] ."\n\n";
}
print "Operation done successfully\n";
$dbh->disconnect();
```

Lorsque le programme donné ci-dessus est exécuté, il produira le résultat suivant :

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
