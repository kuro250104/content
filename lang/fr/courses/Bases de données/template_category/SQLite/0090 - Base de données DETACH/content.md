## Introduction

La commande SQLite **DETACH DATABASE** est utilisée pour détacher et dissocier une base de données nommée d'une connexion de base de données qui a été précédemment attachée en utilisant la commande **ATTACH**. Si le même fichier de base de données a été attaché avec plusieurs alias, alors la commande DETACH ne déconnectera que le nom donné et le reste de l'attachement continuera. Vous ne pouvez pas détacher les bases de données **principales** ou **temporaires**.

Si la base de données est une base de données en mémoire ou temporaire, la base de données sera détruite et son contenu sera perdu.

## Syntaxe

Voici la syntaxe de base de l'instruction SQLite DETACH DATABASE 'Alias-Name'.

```sql
DETACH DATABASE 'Alias-Name';
```

Ici, 'Alias-Name' est le même alias que celui que vous avez utilisé pour attacher la base de données à l'aide de l'instruction **ATTACH**.

## Exemple

Considérons que vous avez une base de données, que vous avez créée dans le chapitre précédent et attachée avec 'test' et 'currentDB' comme nous pouvons le voir en utilisant la commande **.database**.

```sql
sqlite>.databases
seq  name             file
---  ---------------  ----------------------
0    main             /home/sqlite/testDB.db
2    test             /home/sqlite/testDB.db
3    currentDB        /home/sqlite/testDB.db
```

Essayons de détacher 'currentDB' de testDB.db en utilisant la commande suivante.

```sql
sqlite> DETACH DATABASE 'currentDB';
```

Maintenant, si vous vérifiez l'attachement actuel, vous constaterez que testDB.db est toujours connecté à 'test' et 'main'.

```sql
sqlite>.databases
seq  name             file
---  ---------------  ----------------------
0    main             /home/sqlite/testDB.db
2    test             /home/sqlite/testDB.db
```