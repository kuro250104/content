Le langage HTML permet également d’afficher du code qui ne sera pas interprété par le navigateur (pour un site web qui donne des cours de code, par exemple), ou encore, d’afficher des combinaisons de touches (pour des raccourcis claviers, par exemple). Tous ces éléments mis à dispositions par le HTML permettent à un développeur web de créer un site donnant des cours sur des langages informatiques. 

## L’élément <kbd>

Cet élément est utilisé pour afficher une combinaison de touches. Lorsque le navigateur rencontrera cet élément, il l’affichera dans une police monospace, afin de distinguer son contenu du reste du paragraphe.

Exemple :

``` html
<!-- Affiche une combinaison de touches -->
<p>Pour quitter le site veuillez faire <kbd> Alt + F4</kbd></p>
```

## L’élément <samp>

Si un développeur se retrouve à créer un site web de cours sur différents langages informatiques, il est possible qu’il faille à un moment afficher un message de sortie de fin de programme. C’est le rôle de l’élément ```<samp></samp>```, dont le rôle est de distinguer ce message du reste du paragraphe.

Exemple :

``` html
<p>Message:</p>
<!-- Message de sortie de programme -->
<p><samp>Fichier introuvable.</samp></p>
```

## L’élément <code>

```<code></code>``` permet d’afficher un code source sur la page web, qui ne sera pas interprété par le navigateur. 

__Remarque__ : Lorsque le navigateur rencontre cet élément, il n’affiche pas les espaces ou tabulations, et ne retient pas les retours à la ligne, pourtant essentiels pour un code clair et lisible. Pour résoudre ce problème, il est possible d’entourer le code de l’élément de pré-formatage ```<pre></pre>```.

Exemple :

``` html
<!-- Définit un morceau de code -->
<pre>
<code>
    <body>
		<p>Je suis un paragraphe affiché dans du code qui n'est pas interprété par le navigateur </p>
	</body>
</code>
</pre>
```

## L’élément <var>

En informatique, une variable est une place en mémoire qui est allouée à un élément. Le rôle d’une variable est de conserver en mémoire une valeur pendant toute la durée d’exécution d’un programme, et d’effacer ce contenu lorsque le programme n’est plus exécuté.

L’élément ```<var></var>``` permet d’afficher le contenu de variable, afin de les distinguer du reste du paragraphe en cours. 

Exemple :

``` html
<!-- Définit des variables -->
<p>Si c désigne la longueur d'un côté d'un triangle et h la hauteur relative à ce côté, l'aire de ce triangle est égale à (<var>c</var> × <var>h</var>) / 2.</p>
```