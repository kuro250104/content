Dans le cours d’introduction aux formulaires, certains types d’input - les plus utilisés - ont déjà été évoqués. 

Le but de ce chapitre est de montrer les autres types d’input mis à disposition des développeurs par le langage HTML.

## Input Type Color

Ce type d’input est utilisé afin que l’utilisateur puisse choisir une couleur.

En fonction du navigateur utilisé et de la version de celui-ci, un sélecteur de couleur peut apparaître.

Exemple :

```html
<input type="color" id="color" name="color">
```

## Input Type Date

Tout bon formulaire d’inscription qui se respecte demande la date de naissance de l’utilisateur. Avant le HTML5, chaque site avait sa manière de faire sélectionner sa date de naissance à l’utilisateur, avant des champs de texte ou des listes déroulantes, par exemple. 

Depuis le HTML5, il est possible de créer un champ de type date. Ce champ permet la saisie d’une date au format jj/mm/aaaa, et en fonction du navigateur utilisé et de sa version, un sélecteur de date peut être disponible.

Exemple :

```html
<input type="date" id="naissance" name="naissance">
```

Les champs de type date permettent également de définir une date minimum et une date maximum sélectionnable par l’utilisateur. 

Pour ce faire, les attributs ```min``` et ```max``` doivent être utilisés. Ils prennent en valeur la date minimum sélectionnable et la date maximum. 

Remarque : Dans les attributs ```min``` et ```max```, les formats de dates sont anglais, à savoir **aaaa-mm-jj**.

Exemple :

```html
<!-- Date minimum possible le 01/01/1980 et maximum le 01/01/2020 -->
<input type="date" id="naissance" name="naissance" min="1980-01-01" max="2020-01-01">
```

## Input Type Datetime-local

Ce type d’input permet d’insérer un champ qui recevra à la fois  . 

En fonction du type de navigateur utilisé, un sélecteur de date et heure peut apparaître.

Exemple :

```html
<input type="datetime-local" id="flight" name="flight" title="Date et heure de votre vol" />
```

## Input Type Week

Cet input permet à l’utilisateur de saisir une semaine et une année. 

Selon le navigateur utilisé et sa version, un sélecteur peut apparaître dans le champ. 

Exemple :

```html
<input type="week" id="semaine" name="semaine">
```

## Input Type Month

L’input de type **month** permet de saisir un mois et une année. 

En fonction du navigateur utilisé, un sélecteur de mois et d’année peut-être mis à la disposition de l’utilisateur.

Exemple :

```html
<input type="month" id="naissanceMois" name="naissanceMois">
```

## Input Type Time

Cet input permet à l’utilisateur de saisir une heure. 

En fonction du type de navigateur utilisé et de sa version, un sélecteur d’heure peut apparaître dans le champ de saisie.

Exemple :

```html
<input type="time" id="heure" name="heure">
```

## Input Type Email

Un champ de type email n’aura pas d’affichage particulier. Il apparaît comme un simple champ de texte. Cependant, en fonction du navigateur utilisé, il est possible que si l’email n’est pas au format correct, cela envoie un message d’erreur à l’utilisateur lors de l’envoie du formulaire. 

Exemple :

```html
<input type="email" id="email" name="email" />
```

## Input Type File

Ce type de champ permet d’ajouter un bouton parcourir afin de donner à l’utilisateur la possibilité de sélectionner un fichier. 

C’est ce type d’input qui est utilisé lorsque l’utilisateur doit sélectionner une photo de profil.

Exemple :

```html
<input type="file" id="monfichier" name="monfichier">
```

## Input Type Number

Ce type d’input affiche un champ d’entrée numérique. Sur tous les navigateurs modernes, ce champ est accompagné de deux flèches (haut et bas), permettant la sélection d’un nombre.

De plus, il est possible de définir un nombre minimum et un nombre maximum en utilisant les attributs **min** et **max**. 


L'exemple suivant affiche un champ de saisie numérique, dans lequel l’utilisateur ne peut saisir qu’un nombre en 1 et 50 :

```html
<input type="number" id="age" name="age" min="1" max="50" />
```

## Input Type Range

Un input de type range affiche à l’écran un slider (une barre de défilement) permettant à l’utilisateur de sélectionner un nombre. 

L'intervalle de sélection est définie en utilisant les attributs **min** et **max**. 

Exemple :

```html
<input type="range" id="age" name="age" min="1" max="50">
```

## Input Type Search

Ce type d’input est utilisé pour les barres de recherche. Il s’affiche comme un simple champ de texte. 

Exemple :

```html
<input type="search" id="recherche" name="recherche">
```

## Input Type Tel

Le ```<input type = "tel">``` permet la saisie d’un numéro de téléphone. 

Ce type d’input doit être complété avec l’attribut ```pattern```, définissant le format du numéro de téléphone à saisir sous forme d’expression régulière.

Exemple :

```html
<input type="tel" id="telephone" name="telephone" pattern="[0-9]{2}-[0-9]{2}-[0-9]{2}-[0-9]{2}-[0-9]{2}">
```

Dans cet exemple, le pattern précise que le numéro de téléphone doit être au format suivant : 5 paires de chiffres allant de 0 à 9.

## Input Type Url

Cet input permet à l’utilisateur de saisir une URL (un lien vers son profil Facebook, par exemple).

Exemple :

```html
<input type="url" id="lien" name="lien">
```