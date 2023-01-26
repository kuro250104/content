PostgreSQL est un système de base de données objet-relationnel puissant et open source. Il a plus de 15 ans de phase active de développement et une architecture éprouvée qui lui a valu une solide réputation de fiabilité, d'intégrité des données et de justesse.

Ce cours vous permettra de démarrer rapidement avec PostgreSQL et de vous familiariser avec la programmation PostgreSQL.

## Qu'est-ce PostgreSQL?

PostgreSQL (prononcé comme post-gress-Q-L) est un système de gestion de base de données relationnelle (SGBD) open source développé par une équipe mondiale de volontaires. PostgreSQL n'est contrôlé par aucune société ou autre entité privée et le code source est disponible gratuitement.

## Une brève histoire de PostgreSQL

PostgreSQL, initialement appelé Postgres, a été créé à l'UCB par un professeur d'informatique nommé Michael Stonebraker. Stonebraker a lancé Postgres en 1986 comme projet de suivi de son prédécesseur, Ingres, aujourd'hui propriété de Computer Associates.

- **1977-1985** − Un projet appelé INGRES a été développé.
    - Preuve de concept pour les bases de données relationnelles.
    - Création de la société Ingres en 1980.
    - Rachetée par Computer Associates en 1994.
- **1986-1994** − POSTGRES
    - Développement des concepts d'INGRES en mettant l'accent sur l'orientation objet et le langage d'interrogation Quel.
    - La base de code d'INGRES n'a pas été utilisée comme base pour POSTGRES.
    - Commercialisé sous le nom d'Illustra (racheté par Informix, racheté par IBM).
- **1994-1995** − Postgres95
    - Le support de SQL a été ajouté en 1994.
    - Sortie de Postgres95 en 1995.
    - Reprise sous le nom de PostgreSQL 6.0 en 1996.
    - Création de l'équipe de développement mondial de PostgreSQL.

## Key Features of PostgreSQL

PostgreSQL fonctionne sur tous les principaux systèmes d'exploitation, notamment Linux, UNIX (AIX, BSD, HP-UX, SGI IRIX, Mac OS X, Solaris, Tru64) et Windows. Il prend en charge le texte, les images, les sons et la vidéo, et comprend des interfaces de programmation pour C / C++, Java, Perl, Python, Ruby, Tcl et Open Database Connectivity (ODBC).

PostgreSQL prend en charge une grande partie de la norme SQL et offre de nombreuses fonctionnalités modernes, notamment les suivantes :

- Complex SQL queries
- SQL Sub-selects
- Foreign keys
- Trigger
- Views
- Transactions
- Multiversion concurrency control (MVCC)
- Streaming Replication (as of 9.0)
- Hot Standby (as of 9.0)

Vous pouvez consulter la documentation officielle de PostgreSQL pour comprendre les fonctionnalités mentionnées ci-dessus. PostgreSQL peut être étendu par l'utilisateur de plusieurs façons. Par exemple en ajoutant de nouveaux :

- Data types
- Functions
- Operators
- Aggregate functions
- Index methods

## Procedural Languages Support

PostgreSQL supporte quatre langages procéduraux standard, ce qui permet aux utilisateurs d'écrire leur propre code dans n'importe lequel de ces langages et il peut être exécuté par le serveur de base de données PostgreSQL. Ces langages procéduraux sont : PL/pgSQL, PL/Tcl, PL/Perl et PL/Python. En outre, d'autres langages procéduraux non standard comme PL/PHP, PL/V8, PL/Ruby, PL/Java, etc. sont également supportés.
