Dans le développement de logiciels, le terme "réflexion" signifie qu'un programme connaît sa propre structure au moment de l'exécution et qu'il peut également la modifier. Cette capacité est également appelée "introspection". Dans le domaine PHP, Reflection est utilisé pour garantir la sécurité des types dans le code de programme.

## Exemple

Préparons une classe d'exemple simple :

```php
class Example {

	private $attribute1;

	protected $attribute2;

	public $attribute3;

	const PI = 3.1415;

	public function __construct() {
		$this->attribute1 = "Lorem ipsum";
		$this->attribute2 = 36;
		$this->attribute3 = 2 * self::PI;
	}


	public function getAttribute1() {
		return $this->attribute1;
	}
	
	public function setAttribute1($attribute1) {
		$this->attribute1 = $attribute1;
	}

	private function getAttribute2() {
		return $this->attribute2;
	}
	
}
```

Comme on peut le voir, cette classe d'exemple fournit quelques méthodes et attributs simples. Elle nous servira de point de départ dans les prochains exemples.

### Lister les méthodes d’un objet

Grâce à l'API Reflection, il est possible d'analyser les méthodes d’un objet depuis l'extérieur. Pour obtenir une liste complète des méthodes, ```Reflection()``` met à disposition la méthode statique ```getMethods()```.

```php
$reflection_class = new ReflectionClass("Example");

foreach ($reflection_class->getMethods() as $method) {
	echo($method->getName() . "\n"));
}
```

Le résultat est le suivant :

- ```__construct```
- ```getAttribute1```
- ```setAttribute1```
- ```getAttribute2```

La fonction ```ReflectionClass()``` n'attend comme paramètre que le nom complet de la classe à analyser (y compris le namespace, s'il existe). Pour rendre l'initialisation un peu plus agréable, on peut aussi utiliser directement la résolution du nom de classe de PHP :

```php
$reflection_class = new ReflectionClass( Example::class );
```

Outre les noms des méthodes, d'autres informations peuvent être lues :

```php
$reflection_class = new ReflectionClass( Example::class );

foreach ($reflection_class->getMethods() as $method) {
	echo($method->getName() . "\n");

	echo("Nombre de paramètres : " . $method->getNumberOfParameters() . "\n");
	echo("Est privé : " . ($method->isPrivate() ? 'Oui' : 'Non') . "\n\n");
}
```

Le résultat est le suivant :

- ```__construction```
    - Nombre de paramètres : 0
    - Est privé : Non
- ```getAttribute1```
    - Nombre de paramètres : 0
    - Est privé : Non
- ```setAttribute1```
    - Nombre de paramètres : 1
    - Est privé : Non
- ```getAttribute2```
    - Nombre de paramètres : 0
    - Est privé : Oui

### Lire les attributs

Le même comportement peut d'ailleurs être appliqué aux attributs. Au lieu de ```getMethods()```, on utilise simplement ```getProperties()```.

```php
$reflection_class = new ReflectionClass(Example::class);

foreach ($reflection_class->getProperties() as $property) {
    echo($property->getName() . "\n");

    echo("Est privé: " . ($property->isPrivate() ? 'Oui' : 'Non') . "\n\n");
}
```

Le résultat est ici comparable à celui des méthodes précédentes :

- ```attribut1```
    - Est privé : Oui
- ```attribut2```
    - Est privé : Non
- ```attribut3```
    - Est privé : Non

### Exécuter des méthodes à l'aide de Reflection

L'API de Reflection a d'ailleurs une particularité. Elle permet d'exécuter directement des méthodes privées, ce qui ne serait pas possible dans un contexte de programme normal.

```php
$object = new Example();

$reflection_object = new ReflectionObject($object);
$method = $reflection_object->getMethod("getAttribute1");

try {
	echo($method->invoke($object));
	
} catch (ReflectionException $e) {
	echo("Erreur !");
}
```

La chaîne de caractères "Lorem ipsum" est affichée. Cela est dû au fait que la méthode appelée ```getAttribute1()``` renvoie l'attribut ```attribute1```, qui a été initialisé avec cette chaîne dans le constructeur de la classe.

Comme on peut le voir, l'appel de cette méthode a fonctionné à merveille.

Essayons maintenant, dans l'étape suivante, d'appeler notre méthode privée ```getAttribute2()``` en indiquant dans ```getMethod()``` le nom de la méthode souhaitée :

```php
$object = new Example();

$reflection_object = new ReflectionObject($object);
$method = $reflection_object->getMethod("getAttribute2");

try {
	echo($method->invoke($object));
	
} catch (ReflectionException $e) {
	echo("Erreur !");
}
```

Le résultat est "Erreur !", comme défini dans notre gestion des exceptions. Comme prévu, cela est dû au fait que l'on ne peut pas accéder directement aux méthodes privées en dehors de la classe instanciée.

La méthode ```setAccessible()``` de l'API de Reflection est très utile dans ce cas.

```php
$object = new Example();

$reflection_object = new ReflectionObject($object);
$method = $reflection_object->getMethod("getAttribute2");

try {
	$method->setAccessible(true);
	echo($method->invoke($object));
	
} catch (ReflectionException $e) {
	echo("Erreur !");
}
```

Nous obtenons maintenant en sortie le nombre "36", tel que déclaré dans notre classe.

Avec ```setAccessible()```, le comportement privé de la méthode peut être désactivé pour la suite de son exécution.

Cependant, cela n'est pas très recommandé dans la pratique, car il y a généralement des raisons pour lesquelles certaines méthodes sont définies comme privées. Une utilisation possible de telles techniques pourrait par exemple être intéressante pour les tests unitaires.

## Autre exemple : objet d'entité avec remplissage automatique

Avec cet exemple, nous souhaitons vous montrer l'utilisation de l'API de Reflection dans la pratique. Pour illustrer cela, nous allons utiliser un objet d'entité, comme on le voit déjà dans de nombreux frameworks.

Pour cela, nous construisons d'abord un élément de base à partir duquel nous pouvons dériver nos entités individuelles. Nous partons du principe que chaque entité possède les attributs suivants (inspirés du framework Laravel) :

- id
- createdAt
- updatedAt
- deletedAt

```php
/**
 * Class BaseElement
 */
abstract class BaseElement {

	/**
	 * @var int $id
	 */
	private $id;

	/**
	 * @var \DateTime $createdAt
	 */
	private $createdAt;

	/**
	 * @var \DateTime $updatedAt
	 */
	private $updatedAt;

	/**
	 * @var \DateTime $deletedAt
	 */
	private $deletedAt;


	/**
	 * @var array
	 */
	private $_hidden = [ 'deleted_at' ];


	/**
	 * BaseElement constructor.
	 *
	 * @param array $data
	 */
	public function __construct( $data = null ) {
		
	}



	/**
	 * Returns the ID.
	 *
	 * @return int
	 */
	public function getId() {
		return $this->id;
	}


	/**
	 * Set the ID.
	 *
	 * @param int $id
	 */
	public function setId( int $id ) {
		$this->id = $id;
	}


	/**
	 * Returns the creation date.
	 *
	 * @return \DateTime
	 */
	public function getCreatedAt() {
		return $this->createdAt;
	}


	/**
	 * Set the creation date.
	 *
	 * @param \DateTime $createdAt
	 */
	public function setCreatedAt( $createdAt ) {
		$this->createdAt = $createdAt;
	}


	/**
	 * Returns the update date.
	 *
	 * @return \DateTime
	 */
	public function getUpdatedAt() {
		return $this->updatedAt;
	}


	/**
	 * Set the update date.
	 *
	 * @param \DateTime $updatedAt
	 */
	public function setUpdatedAt( $updatedAt ) {
		$this->updatedAt = $updatedAt;
	}


	/**
	 * Returns the delete date.
	 *
	 * @return \DateTime|null
	 */
	public function getDeletedAt() {
		return $this->deletedAt;
	}


	/**
	 * Set the delete date.
	 *
	 * @param \DateTime|null $deletedAt
	 */
	public function setDeletedAt( $deletedAt ) {
		$this->deletedAt = $deletedAt;
	}

}
```

### Mettre en œuvre le remplissage automatique

Nous avons maintenant une classe de base qui possède quatre attributs, avec les méthodes getter et setter correspondantes. Dans l'étape suivante, nous veillons à ce qu'un tableau de données puisse être transmis dans le constructeur, à l'aide duquel les méthodes Setter correspondantes seront automatiquement déterminées et exécutées.

Pour ce faire, nous écrivons deux classes Helper : l'une pour les opérations de chaînes de caractères concernant la conversion de et vers Camel-Case, et l'autre pour le Type-Casting :

```php
class StringHelper {

	/**
	 * Translates a camel case string into a string with
	 * underscores (e.g. firstName -> first_name)
	 *
	 * @param string $str String in camel case format
	 *
	 * @return string $str Translated into underscore format
	 */
	public static function fromCamelCase( $str ) {
		$str[0] = strtolower( $str[0] );
		$func   = create_function( '$c', 'return "_" . strtolower($c[1]);' );

		return preg_replace_callback( '/([A-Z])/', $func, $str );
	}

	/**
	 * Translates a string with underscores
	 * into camel case (e.g. first_name -> firstName)
	 *
	 * @param string $str String in underscore format
	 * @param bool $capitalise_first_char If true, capitalise the first char in $str
	 *
	 * @return string $str translated into camel caps
	 */
	public static function toCamelCase( $str, $capitalise_first_char = false ) {
		if ( $capitalise_first_char ) {
			$str[0] = strtoupper( $str[0] );
		}
		$func = create_function( '$c', 'return strtoupper($c[1]);' );

		return preg_replace_callback( '/_([a-z])/', $func, $str );
	}

}
```

```php
class IoHelper {

	/**
	 * Helper function for casting variables into desired types.
	 *
	 * @param $value
	 * @param string $type
	 *
	 * @return float|int|bool|string
	 */
	public static function castValue( $value, $type = 'string' ) {
		$type = strtolower($type);

		switch ( $type ) {
			case 'string':
				$value = (string) $value;
				break;
			case 'int':
			case 'integer':
				$value = (int) $value;
				break;
			case 'double':
				$value = (double) $value;
				break;
			case 'float':
				$value = (float) $value;
				break;
			case 'bool':
			case 'boolean':
				$value = (bool) $value;
				break;
			default:
				$value = $value;
		}

		return $value;
	}
}
```

Revenons maintenant à notre classe de base. Pour cela, nous étendons le constructeur comme suit :

```php
/**
 * BaseElement constructor.
 *
 * @param array $data
 */
public function __construct( $data = null ) {
	// check if fill data was provided
	if ( $data ) {

		// cast object into array if it's an object
		if ( is_object( $data ) ) {
			$data = (array) $data;
		}

		// iterate over data array
		foreach ( $data as $key => $value ) {

			// build up name for equivalent setter-function
			$setterFunction = 'set' . StringHelper::toCamelCase( $key, true );

			// check if desired setter-functions exists and if so, execute it
			if ( method_exists( $this, $setterFunction ) ) {

				// get reflection method
				$reflectionMethod = new \ReflectionMethod( $this, $setterFunction );

				// get parameters for reflection method
				$reflectionParameters = $reflectionMethod->getParameters();

				// check if desired parameter at position 0 exists
				if ( isset( $reflectionParameters[0] ) ) {

					// detect desired data type by reading doc-comments
					$type        = strtolower( (string) $reflectionParameters[0]->getType() );
					$castedValue = IoHelper::castValue( $value, $type );

					// call setter-function with casted parameter
					$this->$setterFunction( $castedValue );
				}

			}
		}
	}

}
```

Ce qui se passe ici est relativement simple à expliquer : on vérifie si un tableau de données a été transmis. Dans le cas d'une réponse positive, on vérifie alors s'il s'agit éventuellement d'un objet (comme ce serait par exemple le cas avec l'Eloquent-ORM de Laravel). Si c'est le cas, il est converti en un tableau. L'étape suivante consiste à itérer sur chaque attribut passé en paramètre à l'aide d'une boucle foreach de style key value. Comme l'index est toujours connu et qu'il doit représenter l'attribut concerné, nous supposons que la fonction Setter correspondante est nommée dans le style ```set<AttributName>```.

Si une telle méthode Setter existe réellement dans l'instance d'objet actuelle, nous l'instancions avec la ```ReflectionMethod()```. En théorie, il serait déjà possible de l'utiliser directement. Cependant, nous devons d'abord caster la valeur transmise de manière à ce qu'elle corresponde au type de données attendu de la méthode Setter correspondante.

Pour cela, il faut ensuite lire à l'aide de ```getParameters()``` quels paramètres peuvent être transmis à la méthode Setter concernée. Nous partons ici du principe que chacune de ces méthodes peut prendre en charge un seul paramètre, c'est-à-dire la valeur à définir. Si ce paramètre est défini, ```getType()``` renvoie le type de données attendu, qui a été défini dans les annotations PHP. Nous transmettons ensuite ce type de données cible à notre classe Helper et recevons en retour la variable castée correspondante.

Dans la dernière étape, nous appelons la méthode Setter par un accès régulier à celle-ci et lui transmettons comme paramètre la valeur castée précédemment. Nous avons ainsi implémenté notre fonctionnalité principale concernant l'auto-remplissage.

### Sortir les données

Pour accéder à l'intérieur de notre classe de base en utilisant la méthode getter correspondante, nous écrivons une petite méthode auxiliaire privée :

```php
/**
 * Tries to find an adequate Getter-function for the specified attribute key, and returns its value.
 *
 * @param $key
 *
 * @return null
 */
private function getElementByKey( $key ) {
	// build up name for equivalent setter-function
	$getterFunction = 'get' . StringHelper::toCamelCase( $key, true );

	// check if desired setter-functions exists and if so, execute it
	if ( method_exists( $this, $getterFunction ) ) {

		// get reflection method
		$reflectionMethod     = new \ReflectionMethod( $this, $getterFunction );
		$reflectionMethodName = $reflectionMethod->getName();

		return $this->$reflectionMethodName();
	}

	return null;
}
```

Nous pouvons lui transmettre comme paramètre le nom de l'attribut souhaité. De la même manière que pour la définition des valeurs, nous déterminons le nom de la méthode getter correspondante en supposant qu'elle a été définie sous la forme ```get<AttributName>```.

Si la méthode existe dans le contexte de l'objet actuel, elle est exécutée à l'aide de la fonction ```ReflectionMethod()``` et la valeur de l'attribut souhaité est renvoyée comme résultat.

Afin de permettre une sortie dynamique de tous les attributs, nous devons savoir quels attributs sont généralement disponibles dans la classe appelée, ainsi que dans la classe de base (en tant que classe parente). Pour cela, nous définissons une méthode appelée ```getDocument()```, qui fait exactement cela :

```php
/**
 * Build up the public exposed data array.
 *
 * @param bool $buildRelations
 *
 * @return array
 */
public function getDocument() {
	$reflectionClass = new \ReflectionClass( $this );
	$properties      = [];

	// determine properties of parent class from current context
	$this->buildPropertyArray( $reflectionClass->getParentClass()->getProperties(), $properties );

	// determine properties of current class
	$this->buildPropertyArray( $reflectionClass->getProperties(), $properties );

	// build up data array
	$data = [];
	foreach ( $properties as $property ) {
		if ( ! in_array( StringHelper::fromCamelCase( $property ), $this->_hidden ) ) {
			$data[ $property ] = $this->getElementByKey( $property );
		}
	}

	return $data;
}



/**
 * Internal helper function for extracting valid (public) attributes from ReflectionProperty() array.
 *
 * @param $reflectionProperties
 * @param $data
 */
private function buildPropertyArray( $reflectionProperties, &$data ) {
	foreach ( $reflectionProperties as $property ) {
		$propertyName = $property->getName();

		if ( substr( $propertyName, 0, 1 ) == '_' ) {
			continue;
		}

		$data[] = $property->getName();
	}
}
```

La méthode auxiliaire ```buildPropertyArray()``` sert en premier lieu à éviter le code dupliqué, et en même temps à ignorer les attributs qui commencent par un underscore ("_"). Dans ce cas, les attributs commençant par un tiret bas ne sont pas exportés vers l'extérieur via getDocument() et restent donc secrets.

### Dériver ses propres entités

Pour dériver nos propres classes d'entités à l'aide de la classe de base, il suffit de créer une nouvelle classe avec le nom souhaité, qui hérite de la classe de base que nous avons créée précédemment.

Dans celle-ci, on peut définir des attributs individuels selon le même principe - c'est tout ce qui est nécessaire ici.

```php
/**
 * Class Dummy
 */
class Dummy extends BaseElement {


	/**
	 * @var string $title
	 */
	private $title;



	/**
	 * Returns the title.
	 *
	 * @return string
	 */
	public function getTitle() {
		return $this->title;
	}


	/**
	 * Set the title.
	 *
	 * @param string $title
	 */
	public function setTitle( string $title ) {
		$this->title = $title;
	}

	
}
```

Pour tester notre classe d'entités, nous définissons un petit tableau de données, avec quelques valeurs de test. Dans notre cas, ce tableau doit simuler une source de données externe.

```php
$data = [
	"id"	=> 14,
	"title"	=> "Lorem ipsum",
];
```

Dans l'étape suivante, nous initialisons notre classe d'entités nouvellement créée avec ce tableau de données et pouvons ensuite exporter le résultat complet à l'aide de getDocument() :

```php
$entity = new Dummy( $data );
print_r( $entity->getDocument() );
```

## Conclusion

Grâce à Reflection, le programme peut agir de manière "intelligente" dans le développement moderne de logiciels, car il est en mesure d'analyser et même de modifier les propriétés de ses propres fonctions pendant l'exécution.

L'implémentation de Reflection en PHP est toutefois si vaste que nous n'avons démontré ici qu'une petite partie des possibilités. Il existe encore d'innombrables autres fonctions permettant de décomposer encore plus le code du programme.

En résumé, nous constatons que Reflection est une technologie très puissante qui permet de faire énormément de choses.