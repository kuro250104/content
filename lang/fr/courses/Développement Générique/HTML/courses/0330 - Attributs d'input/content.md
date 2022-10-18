Comme pour beaucoup d’éléments en HTML, ```<input>``` peut-être complété par certains attributs spécifiques, permettant de modifier son affichage ou son comportement.

## L'attribut value

Cet attribut permet d’ajouter une valeur par défaut dans un champ de texte.

Exemple :

``` html
<input type="text" id="metier" name="metier" value="Développeur">
```

## L'attribut readonly

Readonly transforme un champ de saisie en champ de texte en lecture seule. Cela signifie que l’utilisateur ne pourra pas modifier le contenu du champ - il pourra seulement le lire. Malgré tout, le contenu d’un champ en lecture seule est tout de même envoyé lors de la soumission du formulaire. 

Ce type d’attribut est généralement utilisé pour les Conditions Générales d’Utilisation d’un site internet. L’utilisateur peut les lire, mais, bien entendu, ne peut pas les modifier. 

Exemple :

``` html
<input type="text" id="metier" name="metier" value="Développeur" readonly>
```

## L'attribut disabled

Cet attribut permet de désactiver un champ. Cela a pour conséquence que l’utilisateur ne pourra rien saisir dans ce champ. Le champ de saisie, accompagné de cet attribut, est également rendu non cliquable.

Bien entendu, la valeur d’un champ désactivé n’est pas envoyée lors de la soumission du formulaire.

Exemple :

``` html
<input type="text" id="metier" name="metier" value="Développeur" disabled>
```

## L'attribut size

*Size* permet de définir la largeur d’un élément input, en termes de nombres de caractères. Par défaut, la valeur *size* est de 20 caractères. 

**Remarque** : L'attribut size fonctionne seulement avec les types d’input suivants: text, search, tel, url, email et password.

Exemple :

``` html
<input type="text" id="pin" name="pin" size="4">
```

## L'attribut maxlength

Cet attribut permet de définir le nombre maximum de caractères qu’un utilisateur peut saisir dans un champ. Ainsi, lorsque ce nombre maximum est atteint, l’utilisateur ne peut automatiquement plus rien saisir dans le champ. 

Cependant, il n’y a aucune action de la part du navigateur pour avertir que l’utilisateur a atteint le nombre maximum de caractères. Pour ce faire, il faudra utiliser d’autres langages tels que le JavaScript.

Exemple :

``` html
<input type="text" id="pin" name="pin" size="4" maxlength="4">
```

## Les attributs min et max

Ces deux attributs permettent de spécifier une valeur minimum et une valeur maximum acceptées par l’input. Cela signifie que l’utilisateur ne pourra saisir un nombre inférieur au minimum, ni un nombre supérieur au maximum.

__Remarque__ : Les attributs ```min``` et ```max``` fonctionnent avec les types d’input suivants: number, range, date, datetime-local, month, time et week.

Exemple :

``` html
<label for="age">Age (entre 1 et 50):</label>
<input type="number" id="age" name="age" min="1" max="50">
```

## L'attribut multiple

Multiple permet à l’utilisateur de saisir plusieurs entrées dans l’input.

**Remarque** : L'attribut multiple fonctionne avec les types d’input suivants: email et file.

Exemple :

``` html
<input type="file" id="fichiers" name="fichiers" multiple>
```

## L'attribut pattern

L’attribut ```pattern``` est assez particulier. En effet, il reçoit en valeur une expression régulière qui permettra que la saisie de l’utilisateur soit correcte, lors de la soumission du formulaire. 

*Pattern* peut être utilisé avec un champ de type *mail* pour vérifier que l’adresse mail saisie respecte la forme attendue. 

**Remarque** : L'attribut pattern fonctionne avec les types d'entrée suivants: text, date, search, url, tel, email et password.

Exemple :

``` html
<input type="text" id="codePays" name="codePays" pattern="[A-Za-z]{2}" title="Deux lettres pour le code pays, exemple FR">
```

## L'attribut placeholder

Cet attribut permet de spécifier un texte provisoire à l’intérieur d’un champ. Ce texte est remplacé à partir du moment où l’utilisateur commence à taper du texte à l’intérieur du champ. De manière générale, le texte passé en valeur à l’attribut ```placeholder``` est affiché en gris à l’intérieur du champ.

__Remarque__ : L'attribut ```placeholder``` fonctionne avec les input de type text, search, url, tel, email et password.

Exemple :

``` html
<input type="text" id="codePays" name="codePays" pattern="[A-Za-z]{2}" title="Deux lettres pour le code pays, exemple FR" placeholder="FR">
```

## L'attribut required

L’attribut ```required``` ne reçoit pas de valeur, il est généralement placé avant le chevron fermant la balise input. Cet attribut est utilisé afin d’indiquer au navigateur que le champ est obligatoire. Ainsi, sur les navigateurs modernes, lorsque l’utilisateur soumet un formulaire et qu’un champ **required** n’est pas rempli, le navigateur retourne une erreur en disant à l’utilisateur que le champ est obligatoire.

__Remarque__ : ```Required``` fonctionne avec les types d'entrées suivants: text, search, url, tel, email, password, date, number, checkbox, radio et file.

Exemple :

``` html
<input type="text" id="metier" name="metier" required>
```

## L'attribut step

Cet attribut définit un intervalle de nombre utilisable. Ainsi, si step = "2", les nombres acceptés sont -2, 0, 2, 4, etc.

Cet attribut peut également être utilisé avec les attributs ```min``` et ```max``` afin de définir une plage de nombres acceptés avec l’intervalle défini dans step.

__Remarque__ : L'attribut ```step``` fonctionne avec les types d'entrées suivants: number, range, date, datetime-local, month, time et week.

Exemple :

``` html
<input type="number" id="multiplede2" name="multiplede2" step="2">
```

## L'attribut autofocus

**Autofocus** permet de placer automatiquement le curseur dans un champ lors du premier chargement de la page. Généralement, cet attribut est placé dans le premier input du formulaire.

Cet attribut ne reçoit aucune valeur et est généralement placé avant le chevron fermant la balise.

Exemple:

``` html
<input type="text" id="metier" name="metier" autofocus>
```

## L'attribut autocomplete

L’attribut ```autocomplete``` permet au navigateur d’activer l’autocomplétion lors de la saisie utilisateur dans un champ. 

L’autocomplétion est une fonction présente sur tous les navigateurs modernes. Au fur et à mesure que l’utilisateur saisit du texte dans un champ, le navigateur “prédit” sa saisie et lui fournit une liste de propositions. Cette fonction est visible sur certains moteurs de recherche, par exemple.

Cet attribut reçoit la valeur “*on*” si l’autocomplétion doit être activée.

__Remarque__ : L'attribut de saisie semi-automatique fonctionne avec ```<form>``` et les types ```<input>``` suivants: text, search, url, tel, email, password, date, range et color.

Exemple :

``` html
<form action="envoyer.php" autocomplete="on">
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" autocomplete="off">
    <input type="checkbox" id="dev" name="metier" value="dev">
    <label for="male">Développeur</label><br>
    <input type="checkbox" id="res" name="metier" value="res">
    <label for="female">Réseaux</label><br>
    <input type="submit" value="Envoyer">
    <input type="reset">
</form>
```