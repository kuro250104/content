En JavaScript, il est coutumier de placer un point-virgule à chaque fin d’instruction. Avec les nouvelles évolutions de la technologie, ce point n’est plus une nécessité absolue même si nous vous recommandons au moins pour les débuts de vous y tenir.

Il existe de nombreuses syntaxes en JavaScript tout comme dans les autres langages de programmation. Nous allons ici vous en montrer quelques-unes parmi les plus utilisées.

## Écrire une phrase

Il existe deux principales manières d’écrire une phrase en JavaScript. La syntaxe est simple : écrire la phrase entre des guillemets. Ainsi, vous pouvez aussi bien utiliser les guillemets simples ( ‘ ) que les guillemets doubles ( “ ). Par exemple :

``` js
alert("Je suis une instruction JavaScript");

alert('Je suis une instruction JavaScript');
```

Notons également qu’en programmation, nous ne parlons pas de “phrase”, mais de “chaîne de caractères”. Nous utiliserons donc désormais ce terme.

## Écrire un nombre

Les nombres s’écrivent plus simplement que les chaînes de caractères, puisqu’ils ne nécessitent pas de guillemets. Il suffit de renseigner le nombre. Par exemple : 

``` js
alert(3);
```

Une petite particularité existe cependant pour les nombres à virgule : la notation doit se faire de manière anglo-saxonne. Ainsi un “nombre à virgule” ne va pas s’écrire avec une “virgule”, mais un “point” afin de distinguer la partie décimale.

``` js
alert(12.5);
```

Attention, si vous écrivez un nombre entre guillemets, alors JavaScript va prendre ce “nombre” pour une chaîne de caractères. Ainsi pour un affichage, vous ne rencontrerez aucun problème, par contre si vous essayez de réaliser des calculs, vous risquez d’obtenir des erreurs.

## Indentation

L’indentation est le terme utilisé pour décrire un décalage de certaines lignes de code par rapport à d’autres en laissant des espaces au début de certaines d’entre elles. On utilise cette technique dans la quasi-totalité des langages de programmation, et elle permet généralement d’améliorer la lisibilité et la maintenabilité du code.

L’indentation s’effectue de manière générale avec la touche “tabulation” de votre clavier et permet d’indiquer visuellement au lecteur ou rédacteur du code une dépendance entre des blocs de lignes par rapport à d’autres.

En développement informatique, cette pratique vous permet de repérer visuellement des boucles, des fonctions, des conditions etc… Dans certains langages, l’indentation est obligatoire sans quoi le code ne peut pas fonctionner correctement (par exemple en “python”). Cependant, elle n’est pas obligatoire en JavaScript. Vous pourriez donc tout à fait réaliser un code sans indentation. Nous vous le déconseillons fortement : rappelez-vous que la lisibilité d’un code fait partie intégrante de sa qualité, et que sans celle-ci votre code ne sera jamais maintenable et ne permettra pas le travail en équipe.

``` js
if(condition) {
	alert('Indentation ici');
}
```

Dans l’exemple ci-dessus, l’instruction ```alert()``` est dépendante du bloc “if”, Il convient donc de faire une tabulation devant ```alert()``` afin de l’indenter et de représenter visuellement cette dépendance.

## Commentaires

Comme dans la grande majorité des langages de programmation, JavaScript nous offre la possibilité d’utiliser des commentaires. Les commentaires sont des lignes qui ne sont pas interprétées comme du code, et qui sont principalement à destination des développeurs pour leur permettre de documenter, d’organiser et de comprendre plus facilement le code réalisé.

Il existe deux types de commentaires, les commentaires mono-lignes et les commentaires multilignes bien que la syntaxe des commentaires multilignes peut être utilisée pour réaliser des commentaires mono-lignes.

Nous avons donc pour les commentaires mono-lignes les syntaxes suivantes :

``` js
//Je suis un commentaire mono-ligne
/* Je suis un commentaire mono-ligne */
```

Et pour les commentaires multilignes :

``` js
/*
Je suis un commentaire
multi-lignes
*/
```

Attention, lorsque vous écrivez des commentaires, pensez aussi à ne pas y laisser d'informations sensibles comme des mots de passe. N’oubliez pas que JavaScript est un langage “client-side” et donc si un utilisateur inspecte votre page web, il pourra accéder aux commentaires dans la console de son navigateur et donc disposer des informations que vous pourrez y avoir laissé.