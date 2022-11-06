Le guide de style aide à maintenir une présentation cohérente du code et à le rendre plus lisible. Voici les meilleures pratiques à suivre lors de la rédaction de contrats avec Solidity.

## Disposition du code

- **Indentation** - Utilisez 4 espaces au lieu de la tabulation pour maintenir le niveau d'indentation. Évitez de mélanger espaces et tabulations.
- **Règle des deux lignes vierges** - Utilisez deux lignes vierges entre deux définitions de contrat.

```solidity
pragma solidity ^0.5.0;

contract LedgerBalance {
    //...
}


contract Updater {
    //...
}
```

- **Règle de la ligne vierge** - Utilisez une ligne vierge entre deux fonctions. Dans le cas d'une simple déclaration, il n'est pas nécessaire d'avoir des lignes vierges.

```solidity
pragma solidity ^0.5.0;

contract A {
    function balance() public pure;
    function account() public pure;
}
contract B is A {
    function balance() public pure {
        // ...
    }

    function account() public pure {
        // ...
    }
}
```

- **Longueur maximale des lignes** - Une seule ligne ne doit pas dépasser 79 caractères afin que les lecteurs puissent facilement analyser le code.
- **Règles d'habillage** - Le premier argument doit être sur une nouvelle ligne sans parenthèses ouvrantes. Utilisez une seule indentation par argument. L'élément de terminaison ); doit être le dernier.

```solidity
function_with_a_long_name(
    longArgument1,
    longArgument2,
    longArgument3
);
variable = function_with_a_long_name(
    longArgument1,
    longArgument2,
    longArgument3
);
event multipleArguments(
    address sender,
    address recipient,
    uint256 publicKey,
    uint256 amount,
    bytes32[] options
);
MultipleArguments(
    sender,
    recipient,
    publicKey,
    amount,
    options
);
```

- **Codage du code source** - Le codage UTF-8 ou ASCII doit être utilisé de préférence.
- **Importations** - Les déclarations d'importation doivent être placées en haut du fichier, juste après la déclaration de pragma.
- **Ordre des fonctions** - Les fonctions doivent être regroupées en fonction de leur visibilité.

```solidity
pragma solidity ^0.5.0;

contract A {
    constructor() public {
        // ...
    }
    function() external {
        // ...
    }

    // External functions
    // ...

    // External view functions
    // ...

    // External pure functions 
    // ...

    // Public functions
    // ...

    // Internal functions
    // ...

    // Private functions
    // ...
}
```

- **Évitez les espaces supplémentaires** - Évitez les espaces à l'intérieur des parenthèses, des crochets ou des accolades.
- **Structures de contrôle** - Les accolades doivent s'ouvrir sur la même ligne que la déclaration. Elles doivent se fermer sur leur propre ligne en conservant la même indentation. Utilisez un espace avec l'accolade ouvrante.

```solidity
pragma solidity ^0.5.0;

contract Coin {
    struct Bank {
        address owner;
        uint balance;
    }
}
if (x < 3) {
    x += 1;
} else if (x > 7) {
    x -= 1;
} else {
    x = 5;
}
if (x < 3)
    x += 1;
else
    x -= 1;
```

- **Déclaration de fonction** - Utilisez la règle ci-dessus pour les accolades. Ajoutez toujours une étiquette de visibilité. L'étiquette de visibilité doit venir en premier avant tout modificateur personnalisé.

```solidity
function kill() public onlyowner {
    selfdestruct(owner);
}
```

- **Mappings** - Évitez les espaces blancs lorsque vous déclarez des variables de mapping.

```solidity
mapping(uint => uint) map;
mapping(address => bool) registeredAddresses;
mapping(uint => mapping(bool => Data[])) public data;
mapping(uint => mapping(uint => s)) data;
```

- **Déclaration des variables** - Évitez les espaces lorsque vous déclarez des variables de tableau.

```solidity
uint[] x;  // not unit [] x;
```

- **Déclaration de chaîne de caractères** - Utilisez des guillemets doubles pour déclarer une chaîne de caractères au lieu de guillemets simples.

```solidity
str = "foo";
str = "Hamlet says, 'To be or not to be...'";
```

## Ordre de mise en page

Les éléments doivent être disposés dans l'ordre suivant :

- Instructions Pragma
- Instructions d'importation
- Interfaces
- Bibliothèques
- Contrats

Au sein d'une interface, d'une bibliothèque ou d'un contrat, l'ordre doit être le suivant

- Déclarations de type
- Variables d'état
- Événements
- Fonctions

## Conventions de nommage

- Le contrat et la bibliothèque doivent être nommés en utilisant le style CapWords. Par exemple, SmartContract, Owner, etc.
- Le nom du contrat et de la bibliothèque doit correspondre au nom de leur fichier.
- En cas de contrats/bibliothèques multiples dans un fichier, utilisez le nom du contrat/bibliothèque principal.

### Owned.sol

```solidity
pragma solidity ^0.5.0;

// Owned.sol
contract Owned {
    address public owner;
    constructor() public {
        owner = msg.sender;
    }
    modifier onlyOwner {
        //....
    }
    function transferOwnership(address newOwner) public onlyOwner {
        //...
    }
}
```

### Congress.sol

```solidity
pragma solidity ^0.5.0;

// Congress.sol
import "./Owned.sol";

contract Congress is Owned, TokenRecipient {
    //...
}
```

- **Noms de structures** : utilisez le style CapWords comme SmartCoin.
- **Noms d’événements** : utilisez le style CapWords comme Deposit, AfterTransfer.
- **Noms de fonctions** : utilisez le style majuscule mixte comme initiateSupply.
- **Variables locales et d’états** : utilisez le style majuscule mixte comme creatorAddress, supply.
- **Constantes** : utilisez des lettres majuscules et des underscores pour séparer les mots, comme MAX_BLOCKS.
- **Noms des modificateurs** : utilisez le style mixCase comme onlyAfter.
- **Noms d’Enum** : utilisez le style CapWords comme TokenGroup.