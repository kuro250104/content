La base de données Redis peut être sécurisée, de sorte que tout client établissant une connexion doit s'authentifier avant d'exécuter une commande. Pour sécuriser Redis, vous devez définir le mot de passe dans le fichier de configuration.

## Exemple

L'exemple suivant montre les étapes pour sécuriser votre instance Redis.

```bash
127.0.0.1:6379> CONFIG get requirepass 
1) "requirepass" 
2) "" 
```

Par défaut, cette propriété est vide, ce qui signifie qu'aucun mot de passe n'est défini pour cette instance. Vous pouvez modifier cette propriété en exécutant la commande suivante.

```bash
127.0.0.1:6379> CONFIG set requirepass "microlead" 
OK 
127.0.0.1:6379> CONFIG get requirepass 
1) "requirepass" 
2) "microlead"
```

Après avoir défini le mot de passe, si un client exécute la commande sans authentification, l'erreur **(error) NOAUTH Authentication required**. sera renvoyée. Par conséquent, le client doit utiliser la commande **AUTH** pour s'authentifier.

## Syntaxe

Voici la syntaxe de base de la commande **AUTH**.

```bash
127.0.0.1:6379> AUTH password 
```

## Exemple

```bash
127.0.0.1:6379> AUTH "tutorialspoint" 
OK 
127.0.0.1:6379> SET mykey "Test value" 
OK 
127.0.0.1:6379> GET mykey 
"Test value"
```