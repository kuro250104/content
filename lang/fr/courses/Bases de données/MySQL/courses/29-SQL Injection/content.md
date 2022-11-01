## Introduction

Si vous prenez une entrée utilisateur par le biais d'une page Web et que vous l'insérez dans une base de données MySQL, 
il est possible que vous vous soyez exposé à un problème de sécurité connu sous le nom d'injection SQL. Ce chapitre
vous apprendra à prévenir ce problème et à sécuriser vos scripts et vos instructions MySQL.

L'injection SQL se produit généralement lorsque vous demandez à un utilisateur une entrée, comme son nom, et qu'au
lieu d'un nom, il vous donne une instruction MySQL que vous allez exécuter à son insu sur votre base de données.

Ne vous fiez jamais aux données fournies par un utilisateur, ne traitez ces données qu'après les avoir validées ; 
en règle générale, cela se fait par comparaison de motifs. Dans l'exemple suivant, le nom d'utilisateur est limité aux 
caractères alphanumériques plus le trait de soulignement et à une longueur comprise entre 8 et 20 caractères - modifiez 
ces règles selon vos besoins.

``` php
if (preg_match("/^\w{8,20}$/", $_GET['username'], $matches)) {
   $result = mysql_query("SELECT * FROM users WHERE username = $matches[0]");
} else  {
   echo "username not accepted";
}
```

Pour illustrer ce problème, considérons l'extrait suivant.

``` php
// supposed input
$name = "Qadir'; DELETE FROM users;";
mysql_query("SELECT * FROM users WHERE name = '{$name}'");
```

L'appel de fonction est censé récupérer un enregistrement de la table users, où la colonne name correspond au nom 
spécifié par l'utilisateur. Dans des circonstances normales, **$name** ne devrait contenir que des caractères alphanumériques
et peut-être des espaces. Mais ici, en ajoutant une toute nouvelle requête à $name, l'appel à la base de données tourne
au désastre. La requête DELETE injectée supprime tous les enregistrements des utilisateurs.

Heureusement, si vous utilisez MySQL, la fonction **mysql_query()** ne permet pas l'empilement de requêtes ou l'exécution
de plusieurs requêtes en un seul appel de fonction. Si vous essayez d'empiler des requêtes, l'appel échoue.

Cependant, d'autres extensions de bases de données PHP, comme **SQLite** et **PostgreSQL**, effectuent heureusement des 
requêtes empilées, exécutant toutes les requêtes fournies dans une seule chaîne et créant un sérieux problème de sécurité.

## Preventing SQL Injection

Vous pouvez gérer intelligemment tous les caractères d'échappement dans les langages de script comme PERL et PHP. 
L'extension MySQL pour PHP fournit la fonction **mysql_real_escape_string()** pour échapper aux caractères d'entrée
qui sont spéciaux à MySQL.

``` php
if (get_magic_quotes_gpc()) {
   $name = stripslashes($name);
}

$name = mysql_real_escape_string($name);
mysql_query("SELECT * FROM users WHERE name = '{$name}'");
```

## The LIKE Quandary

Pour résoudre le dilemme LIKE, un mécanisme d'échappement personnalisé doit convertir les caractères % et _ fournis par
l'utilisateur en littéraux. Utilisez **addcslashes()**, une fonction qui vous permet de spécifier une plage de caractères à échapper.


``` php
$sub = addcslashes(mysql_real_escape_string("%something_"), "%_");
// $sub == \%something\_
mysql_query("SELECT * FROM messages WHERE subject LIKE '{$sub}%'");
```