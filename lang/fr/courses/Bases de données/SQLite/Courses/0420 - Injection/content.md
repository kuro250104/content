Si vous prenez une entrée utilisateur par le biais d'une page Web et que vous l'insérez dans une base de données SQLite, il y a de fortes chances que vous vous soyez exposé à un problème de sécurité connu sous le nom d'injection SQL. Dans ce chapitre, vous apprendrez à prévenir ce problème et à sécuriser vos scripts et vos instructions SQLite.

L'injection se produit généralement lorsque vous demandez à un utilisateur une entrée, comme son nom, et qu'au lieu d'un nom, il vous donne une instruction SQLite que vous exécuterez à son insu sur votre base de données.

Ne faites jamais confiance aux données fournies par l'utilisateur, ne traitez ces données qu'après les avoir validées ; en règle générale, cela se fait par comparaison de motifs. Dans l'exemple suivant, le nom d'utilisateur est limité à des caractères alphanumériques plus un trait de soulignement et à une longueur comprise entre 8 et 20 caractères - modifiez ces règles si nécessaire.

```php
if (preg_match("/^\w{8,20}$/", $_GET['username'], $matches)){
    $db = new SQLiteDatabase('filename');
    $result = @$db->query("SELECT * FROM users WHERE username = $matches[0]");
} else {
    echo "username not accepted";
}
```

Pour démontrer le problème, considérez cet extrait -

```php
$name = "Qadir'; DELETE FROM users;";
@$db->query("SELECT * FROM users WHERE username = '{$name}'");
```

L'appel de fonction est censé récupérer un enregistrement de la table users dont la colonne name correspond au nom spécifié par l'utilisateur. Dans des circonstances normales, $name ne devrait contenir que des caractères alphanumériques et peut-être des espaces. Cependant, dans ce cas, en ajoutant une requête entièrement nouvelle à $name, l'appel à la base de données tourne au désastre : la requête DELETE injectée supprime tous les enregistrements des utilisateurs.

Certaines interfaces de bases de données ne permettent pas l'empilement de requêtes ou l'exécution de plusieurs requêtes en un seul appel de fonction. Si vous essayez d'empiler des requêtes, l'appel échoue mais SQLite et PostgreSQL, exécutent allègrement les requêtes empilées, exécutant toutes les requêtes fournies dans une seule chaîne et créant un sérieux problème de sécurité.

## Prévention de l'injection SQL

Vous pouvez gérer intelligemment tous les caractères d'échappement dans les langages de script comme PERL et PHP. Le langage de programmation PHP fournit la fonction ```string sqlite_escape_string()``` pour échapper aux caractères d'entrée qui sont spéciaux à SQLite.

```php
if (get_magic_quotes_gpc()) {
    $name = sqlite_escape_string($name);
}
$result = @$db->query("SELECT * FROM users WHERE username = '{$name}'");
```

Bien que l'encodage permette d'insérer les données en toute sécurité, il rendra inutilisables les comparaisons de texte simples et les clauses **LIKE** dans vos requêtes pour les colonnes qui contiennent les données binaires.

__Remarque__ - ```addslashes()``` ne doit PAS être utilisé pour citer vos chaînes de caractères pour les requêtes SQLite ; cela conduira à des résultats étranges lors de la récupération de vos données.
