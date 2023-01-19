## Introduction

Ce chapitre vous aide à comprendre ce qu'est SQLite, en quoi il diffère de SQL, pourquoi il est nécessaire et la façon dont il gère les applications Base de données.

SQLite est une bibliothèque logicielle qui implémente un moteur de base de données SQL transactionnel autonome, sans serveur et sans configuration. SQLite est l'un des moteurs de base de données dont la croissance est la plus rapide, mais il s'agit d'une croissance en termes de popularité, qui n'a rien à voir avec sa taille. Le code source de SQLite est dans le domaine public.

## Qu'est-ce que SQLite ?

SQLite est une bibliothèque in-process qui implémente un moteur de base de données SQL transactionnel, autonome, sans serveur et sans configuration. C'est une base de données, qui est zéro-configuration, ce qui signifie que comme d'autres bases de données vous n'avez pas besoin de la configurer dans votre système.

Le moteur SQLite n'est pas un processus autonome comme les autres bases de données, vous pouvez le lier statiquement ou dynamiquement à votre application en fonction de vos besoins. SQLite accède directement à ses fichiers de stockage.

## Pourquoi SQLite ?

- SQLite ne nécessite pas de processus ou de système de serveur distinct pour fonctionner (sans serveur).
- SQLite est livré avec zéro-configuration, ce qui signifie qu'aucune installation ou administration n'est nécessaire.
- Une base de données SQLite complète est stockée dans un seul fichier disque multiplateforme.
- SQLite est très petit et léger, moins de 400KiB entièrement configurés ou moins de 250KiB avec des fonctionnalités optionnelles omises.
- SQLite est autonome, ce qui signifie qu'il n'a pas de dépendances externes.
- Les transactions SQLite sont entièrement conformes à la norme ACID, permettant un accès sécurisé à partir de plusieurs processus ou threads.
- SQLite prend en charge la plupart des fonctionnalités du langage d'interrogation de la norme SQL92 (SQL2).
- SQLite est écrit en ANSI-C et fournit une API simple et facile à utiliser.
- SQLite est disponible sous UNIX (Linux, Mac OS-X, Android, iOS) et Windows (Win32, WinCE, WinRT).

## SQLite : une brève histoire

- 2000 - D. Richard Hipp a conçu SQLite dans le but de ne pas nécessiter d'administration pour faire fonctionner un programme.
- 2000 - En août, SQLite 1.0 a été publié avec GNU Database Manager.
- 2011 - Hipp a annoncé l'ajout de l'interface UNQl à la base de données SQLite et le développement de UNQLite (base de données orientée document).

## Limitations de SQLite

Il y a quelques fonctionnalités non supportées de SQL92 dans SQLite qui sont listées dans le tableau suivant.

**Caractéristiques et description**

- **RIGHT OUTER JOIN** - Seul le LEFT OUTER JOIN est mis en œuvre.
- **FULL OUTER JOIN** - Seul le LEFT OUTER JOIN est mis en œuvre.
- **ALTER TABLE** - Les variantes RENAME TABLE et ADD COLUMN de la commande ALTER TABLE sont prises en charge. Les commandes DROP COLUMN, ALTER COLUMN et ADD CONSTRAINT ne sont pas prises en charge.
- **Trigger support** - Les déclencheurs FOR EACH ROW sont pris en charge mais pas les déclencheurs FOR EACH STATEMENT.
- **VIEWS** - Les VIEWs dans SQLite sont en lecture seule. Vous ne pouvez pas exécuter une instruction DELETE, INSERT ou UPDATE sur une vue.
- **GRANT and REVOKE** - Les seules autorisations d'accès qui peuvent être appliquées sont les autorisations normales d'accès aux fichiers du système d'exploitation sous-jacent.

## SQLite Commands

Les commandes SQLite standard pour interagir avec les bases de données relationnelles sont similaires à SQL. Il s'agit de CREATE, SELECT, INSERT, UPDATE, DELETE et DROP. Ces commandes peuvent être classées en groupes, en fonction de leur nature opérationnelle.

## DDL - Data Definition Language

**Commande et description**

- **INSERT** - Créer un enregistrement.
- **UPDATE** - Modifie les enregistrements.
- **DELETE** - Supprime les enregistrements.

## DQL - Data Query Language

**Commande et description**

- **SELECT** - Extrais certaines données d'une ou plusieurs tables.
