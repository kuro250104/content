## Qu'est-ce qu'un opérateur ?

Prenons une expression simple : **4 + 5** est égal à **9**. Ici, **4** et **5** sont appelés **opérandes** et '**+**' est appelé l'**opérateur**. Solidity prend en charge les types d'opérateurs suivants :

- Opérateurs arithmétiques
- Opérateurs de comparaison
- Opérateurs logiques (ou relationnels)
- Opérateurs d'affectation
- Opérateurs conditionnels (ou ternaires)

## Opérateurs d’affectation

### Affectation simple (=)

Affecte les valeurs de l'opérande de droite à l'opérande de gauche. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1; // opérateur d'affectation
        uint b = 2; // opérateur d'affectation
        uint c = a + b; // opérateur d'affectation
        return c;
    }
}
```

L’exemple ci-dessus retourne “3”.

### Affectation et addition (+=)

Il ajoute l'opérande de droite à l'opérande de gauche et affecte le résultat à l'opérande de gauche. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1; // opérateur d'affectation
        uint a += 2; // opérateur d'affectation et addition
        return a;
    }
}
```

L’exemple ci-dessus retourne “3”.

### Affectation et soustraction (-=)

Il soustrait l'opérande de droite de l'opérande de gauche et affecte le résultat à l'opérande de gauche. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 2; // opérateur d'affectation
        uint a -= 1; // opérateur d'affectation et soustraction
        return a;
    }
}
```

L’exemple ci-dessus retourne “1”.

### Affectation et multiplication (*=)

Il multiplie l'opérande de droite par l'opérande de gauche et affecte le résultat à l'opérande de gauche. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 2; // opérateur d'affectation
        uint a *= 2; // opérateur d'affectation et multiplication
        return a;
    }
}
```

L’exemple ci-dessus retourne “4”.

### Affectation et division (/=)

Il divise l'opérande de gauche par l'opérande de droite et affecte le résultat à l'opérande de gauche. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 2; // opérateur d'affectation
        uint a /= 2; // opérateur d'affectation et division
        return a;
    }
}
```

L’exemple ci-dessus retourne “1”.

### Affectation et modulo (%=)

Il prend le modulo en utilisant deux opérandes et assigne le résultat à l'opérande de gauche. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 5; // opérateur d'affectation
        uint a %= 3; // opérateur d'affectation et modulo
        return a;
    }
}
```

L’exemple ci-dessus retourne “2”.