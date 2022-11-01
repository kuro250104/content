## Introduction

### Qu'est-ce qu'une base de données ?

Une base de données est une application distincte qui stocke une collection de données. Chaque base de
données possède une ou plusieurs API distinctes pour créer, accéder, gérer, rechercher et répliquer les 
données qu'elle contient.

D'autres types de stockage de données peuvent également être utilisés, comme des fichiers sur le système de fichiers
ou de grandes tables de hachage en mémoire, mais l'extraction et l'écriture de données ne seraient pas aussi rapides
et faciles avec ce type de systèmes.

De nos jours, nous utilisons des systèmes de gestion de bases de données relationnelles (SGBDR) pour stocker et gérer 
d'énormes volumes de données. On parle de base de données relationnelle car toutes les données sont stockées dans 
différentes tables et les relations sont établies à l'aide de clés primaires ou d'autres clés appelées **Foreign Keys**.

Un **Relational DataBase Management System (RDBMS)** est un logiciel qui :

  - Permet d'implémenter une base de données avec des tables, des colonnes et des index.
  - Garantit l'intégrité référentielle entre les lignes des différentes tables.
  - Met automatiquement à jour les index.
  - Interprète une requête SQL et combine les informations provenant de différentes tables.

## Terminologie des SGBDR

Avant de procéder à l'explication du système de base de données MySQL, révisons quelques définitions relatives à la
base de données.

  - **Database** − Une base de données est une collection de tables, avec des données liées.
  - **Table** − Une table est une matrice contenant des données. Une table dans une base de données ressemble à une simple feuille de calcul.
  - **Column** − Une colonne (élément de données) contient des données d'un seul et même type, par exemple la colonne code postal.
  - **Row** − Une ligne (= tuple, entrée ou enregistrement) est un groupe de données liées, par exemple les données d'un abonnement.
  - **Redundancy** − Stocker les données deux fois, de manière redondante, pour rendre le système plus rapide.
  - **Primary Key** − Une clé primaire est unique. La valeur d'une clé ne peut pas apparaître deux fois dans une même table. Avec une clé, vous ne pouvez trouver qu'une seule ligne.
  - **Foreign Key** − Une clé étrangère est l'axe de liaison entre deux tables.
  - **Compound Key** − Une clé composée (clé composite) est une clé qui se compose de plusieurs colonnes, car une colonne n'est pas suffisamment unique.
  - **Index** − Un index dans une base de données ressemble à un index à la fin d'un livre.
  - **Referential Integrity** − L'intégrité référentielle permet de s'assurer qu'une valeur de clé étrangère pointe toujours vers une ligne existante.

## Base de données MySQL

MySQL est un SGBDR rapide et facile à utiliser, utilisé par de nombreuses petites et grandes entreprises. MySQL est
développé, commercialisé et supporté par MySQL AB, une société suédoise. La popularité de MySQL s'explique par de 
nombreuses bonnes raisons.

  - MySQL est publié sous une licence open-source. Vous n'avez donc rien à payer pour l'utiliser.
  - MySQL est un programme très puissant en soi. Il gère un large sous-ensemble de la fonctionnalité des paquets de bases de données les plus chers et les plus puissants.
  - MySQL utilise une forme standard du célèbre langage de données SQL.
  - MySQL fonctionne sur de nombreux systèmes d'exploitation et avec de nombreux langages, notamment PHP, PERL, C, C++, JAVA, etc.
  - MySQL fonctionne très rapidement et fonctionne bien même avec de grands ensembles de données.
  - MySQL est très convivial avec PHP, le langage le plus apprécié pour le développement web.
  - MySQL prend en charge les grandes bases de données, jusqu'à 50 millions de lignes ou plus dans une table. La taille limite par défaut d'un fichier pour une table est de 4 Go, mais vous pouvez l'augmenter (si votre système d'exploitation le permet) jusqu'à une limite théorique de 8 millions de téraoctets (TB).
  - MySQL est personnalisable. La licence open-source GPL permet aux programmeurs de modifier le logiciel MySQL pour l'adapter à leurs propres environnements spécifiques.

## Avant de commencer

Avant de commencer ce tutoriel, vous devez avoir une connaissance de base des informations couvertes dans nos tutoriels 
PHP et HTML.

Ce tutoriel se concentre principalement sur l'utilisation de MySQL dans un environnement PHP. De nombreux exemples
donnés dans ce tutoriel seront utiles aux programmeurs PHP.

Nous vous recommandons de consulter notre tutoriel PHP à titre de référence.
