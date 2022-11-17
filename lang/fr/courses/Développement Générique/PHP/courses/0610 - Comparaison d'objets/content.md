Depuis PHP 5, la comparaison d'objets est plus complexe qu'en PHP 4, et plus proche du comportement que l'on pourrait attendre d'un langage orienté objet (sans aller jusqu'à dire que PHP 5 en soit un).

Lors de l'utilisation de l'opérateur de comparaison (==), les objets sont comparés de manière simple, à savoir : deux objets sont égaux s'ils ont les mêmes attributs et valeurs, et qu'ils sont des instances de la même classe.

D'un autre côté, lors de l'utilisation de l'opérateur d'identité (===), les objets sont identiques uniquement s'ils font référence à la même instance de la même classe.

Exemple :

```php
<?php
function bool2str($bool)
{
	if ($bool === false) {
		return 'FALSE';
	} else {
		return 'TRUE';
	}
}

function compareObjects(&$o1, &$o2)
{
	echo('o1 == o2 : '.bool2str($o1 == $o2)."\n");
	echo('o1 != o2 : '.bool2str($o1 != $o2)."\n");
	echo('o1 === o2 : '.bool2str($o1 === $o2)."\n");
	echo('o1 !== o2 : '.bool2str($o1 !== $o2)."\n");
}

class Flag
{
	public $flag;

	function Flag($flag = true) {
		$this->flag = $flag;
	}
}

class OtherFlag
{
	public $flag;

	function OtherFlag($flag = true) {
		$this->flag = $flag;
	}
}

$o = new Flag();
$p = new Flag();
$q = $o;
$r = new OtherFlag();

echo("Deux instances de la même classe\n");
compareObjects($o, $p);

echo("\nDeux références sur le même objet\n");
compareObjects($o, $q);

echo("\nInstances de classes différentes\n");
compareObjects($o, $r);
?>
```

L'exemple ci-dessus va afficher :

```php
Deux instances de la même classe
o1 == o2 : TRUE
o1 != o2 : FALSE
o1 === o2 : FALSE
o1 !== o2 : TRUE

Deux références sur le même objet
o1 == o2 : TRUE
o1 != o2 : FALSE
o1 === o2 : TRUE
o1 !== o2 : FALSE

Instances de classes différentes
o1 == o2 : FALSE
o1 != o2 : TRUE
o1 === o2 : FALSE
o1 !== o2 : TRUE
```