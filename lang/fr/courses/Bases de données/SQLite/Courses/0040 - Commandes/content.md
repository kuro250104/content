Ce cours vous présentera des commandes simples et utiles utilisées par les programmeurs SQLite. Ces commandes sont appelées SQLite dot commands et l'exception avec ces commandes est qu'elles ne doivent pas être terminées par un point-virgule ( ;).

Commençons par taper une simple commande sqlite3 à l'invite de commande qui vous donnera accès à l'invite de commande SQLite où vous pourrez lancer diverses commandes SQLite.

```bash
$sqlite3
SQLite version 3.3.6
Enter ".help" for instructions
sqlite>
```

Pour obtenir une liste des commandes point disponibles, vous pouvez saisir ".help" à tout moment. Par exemple .

La commande ci-dessus affichera une liste de diverses commandes importantes de SQLite dot, qui sont énumérées dans le tableau suivant.

**Commande et description**

- ```.backup ?DB? FILE``` - Sauvegarde de la BD (par défaut "main") vers le FICHIER
- ```.bail ON|OFF``` - Il s'arrête après avoir rencontré une erreur. Par défaut OFF
- ```.databases``` - Liste des noms et des fichiers des bases de données jointes
- ```.dump ?TABLE?``` - Dump la base de données dans un format texte SQL. Si TABLE est spécifié, seules les tables correspondant au modèle LIKE TABLE seront vidées.
- ```.echo ON|OFF``` - Activer ou désactiver l'écho des commandes
- ```.exit``` - Quitter l'invite SQLite
- ```.explain ON|OFF``` - Active ou désactive le mode de sortie approprié pour EXPLAIN. Sans argument, EXPLAIN est activé.
- ```.header(s) ON|OFF``` - Activer ou désactiver l'affichage des en-têtes
- ```.help``` - Afficher ce message
- ```.import FILE TABLE``` - Importer des données du FICHIER vers le TABLEAU
- ```.indices ?TABLE?``` - Affiche les noms de tous les index. Si TABLE est spécifié, seuls les index des tables correspondant au modèle LIKE TABLE sont affichés.
- ```.load FILE ?ENTRY?``` - Charger une bibliothèque d'extension
- ```.log FILE|off``` - Active ou désactive la journalisation. FILE peut être stderr/stdout.
- ```.mode MODE``` - Définir le mode de sortie où MODE est l'un de -
    - ```csv``` − Valeurs séparées par des virgules
    - ```column``` − Colonnes alignées à gauche.
    - ```html``` − Code HTML ```<table>```
    - ```insert``` − Instructions d'insertion SQL pour TABLE
    - ```line``` − Une valeur par ligne
    - ```list``` − Valeurs délimitées par une chaîne de séparation .séparateur
    - ```tabs``` − Valeurs séparées par des tabulations
    - ```tcl``` − Éléments de liste TCL
- ```.nullvalue STRING``` - Imprimer STRING à la place des valeurs NULL
- ```.output FILENAME``` - Envoyer la sortie vers FILENAME
- ```.output stdout``` - Envoyer la sortie à l'écran
- ```.print STRING…``` - Imprimer une STRING littérale
- ```.prompt MAIN CONTINUE``` - Remplacer les invites standard
- ```.quit``` - Exit SQLite prompt
- ```.read FILENAME``` - Exécuter SQL dans FILENAME
- ```.schema ?TABLE?``` - Affiche les instructions CREATE. Si TABLE est spécifié, seules les tables correspondant au modèle LIKE TABLE sont affichées.
- ```.separator STRING``` - Changez le séparateur utilisé par le mode de sortie et .import
- ```.show``` - Afficher les valeurs actuelles de divers paramètres
- ```.stats ON|OFF``` - Activer ou désactiver les statistiques
- ```.tables ?PATTERN?``` - Lister les noms des tables correspondant à un motif LIKE
- ```.timeout MS``` - Essayez d'ouvrir les tables verrouillées pour MS millisecondes
- ```.width NUM NUM``` - Définir la largeur des colonnes pour le mode "colonne
- ```.timer ON|OFF``` - Activer ou désactiver la mesure de la minuterie du CPU

Essayons la commande ```.show``` pour voir les paramètres par défaut de votre invite de commande SQLite.

```sql
sqlite>.show
     echo: off
  explain: off
  headers: off
     mode: column
nullvalue: ""
   output: stdout
separator: "|"
    width:
sqlite>
```

Assurez-vous qu'il n'y a pas d'espace entre sqlite> prompt et la commande dot, sinon cela ne fonctionnera pas.

## Formatage de la sortie

Vous pouvez utiliser la séquence suivante de commandes de points pour formater votre sortie.

```sql
sqlite>.header on
sqlite>.mode column
sqlite>.timer on
sqlite>
```

Le paramètre ci-dessus produira la sortie au format suivant.

```bash
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
CPU Time: user 0.000000 sys 0.000000
```

## La table sqlite_master

La table maître contient les informations clés sur les tables de votre base de données et elle est appelée **sqlite_master**. Vous pouvez voir son schéma comme suit -

Cela donnera le résultat suivant.

```sql
CREATE TABLE sqlite_master (
    type text,
    name text,
    tbl_name text,
    rootpage integer,
    sql text
);```