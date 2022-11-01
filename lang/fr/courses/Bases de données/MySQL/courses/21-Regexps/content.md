## Introduction

Vous avez vu le filtrage MySQL avec **LIKE** ...%. MySQL supporte un autre type d'opération de filtrage basé sur les 
expressions régulières et l'opérateur **REGEXP**. Si vous connaissez PHP ou PERL, il vous sera très facile de comprendre 
car cette correspondance est identique à celle des expressions régulières.

Voici le tableau des motifs qui peuvent être utilisés avec l'opérateur **REGEXP**.

| Pattern  | Correspondance                                          | 
|----------|---------------------------------------------------------|
| ^        | Début de la chaîne                                      |
| $        | Fin de la chaîne                                        | 
| .        | Tout caractère unique                                   |  
| [...]    | Tout caractère figurant entre les crochets              |
| [^...]   | Tout caractère ne figurant pas entre les crochets       |
| p1,p2,p3 | Alternance ; correspond à l'un des motifs p1, p2 ou p3. |
| *        | Zéro ou plus d'instances de l'élément précédent         |
| +        | Une ou plusieurs instances de l'élément précédent       |
| {n}      | n instances de l'élément précédent                      |
| {m,n}    | m à n instances de l'élément précédent                  |

### Exemples

Sur la base du tableau ci-dessus, vous pouvez créer différents types de requêtes SQL pour répondre à vos besoins. 
Je vais en énumérer quelques-unes pour votre compréhension.

Considérez que nous avons une table appelée person_tbl et qu'elle a un champ appelé name -

Requête pour trouver tous les noms commençant par '**st**'.

``` sql
mysql> SELECT name FROM person_tbl WHERE name REGEXP '^st';
```

Requête pour trouver tous les noms se terminant par 'ok'. 

``` sql
mysql> SELECT name FROM person_tbl WHERE name REGEXP 'ok$';
```

Requête pour trouver tous les noms qui contiennent 'mar'.

``` sql
mysql> SELECT name FROM person_tbl WHERE name REGEXP 'mar';
```

Requête pour trouver tous les noms commençant par une voyelle et se terminant par 'ok'.

``` sql
mysql> SELECT FirstName FROM intque.person_tbl WHERE FirstName REGEXP '^[aeiou].*ok$';
```

