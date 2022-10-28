Généralement un site web est divisé en plusieurs parties : en-tête (*header*, en anglais), un ou plusieurs menus, le contenu et le pied de page (*footer*, en anglais).

## L’en-tête (header)

L’en-tête est situé en haut d’une page web et contient généralement le logo. Celui-ci est couramment placé au-dessus du menu horizontal, s’il y en a un.

Exemple :

```css
header {
	background-color: red;
	text-align: center;
	color: white;
	padding: 10px;
}
```

## Le menu de navigation

Un menu de navigation contient une liste de liens permettant à l’utilisateur de naviguer parmi les différentes pages d’un site web.

Exemple :

```css
nav {
	background-color: grey;
}

nav li {
	list-style-type: none;
}

nav a {
	display: inline;
	text-decoration: none;
	color: white;
	padding: 10px 20px;
}

nav a:hover {
	background-color: white;
	color: black;
}
```

## Le contenu

La disposition du contenu dépend souvent de l’appareil sur lequel le site web est consulté. Une des trois (ou les trois) dispositions suivantes est communément utilisée :

- 1 colonne : généralement utilisé pour les appareils mobiles
- 2 colonnes : communément utilisé pour les tablettes ou ordinateurs portables
- 3 colonnes : utilisé pour les ordinateurs de bureau

Exemple :

```css
.colonne {
	float: left;
	width: 30%;
}

.rangee:after {
	clear: both;
}
```

L’exemple ci-dessus permet de créer un contenu à 3 colonnes.

## Colonnes inégales

Le contenu principal est le plus important sur un site web. Il est donc courant que ce soit la colonne du contenu principale (généralement la colonne centrale) qui soit la plus large ; le contenu moins important étant relégué dans des colonnes moins larges. 

Exemple :

```css
.colonne {
	float: left;
	width: 30%;
}

.colonne_moins_importante {
	width: 25%; /* Les colonnes avec du contenu secondaires sont moins large */
}

.colonne_princiapale {
	width: 50%; /* La colonne avec le contenu principale est la plus large, occupant 50% de la page */
}
```

## Pied de page (footer)

Le pied de page est placé tout en bas de la page et contient généralement le copyright, les mentions légales, ainsi que les informations de contact. Il est également de plus en plus courant que les différents réseaux sociaux sur lesquels l’utilisateur peut retrouver les actualités du site soient placés dans le pied de page.

Exemple :

```css
footer {
	background-color: red;
	color: white;
	text-align: center;
	padding: 20px;
}
```