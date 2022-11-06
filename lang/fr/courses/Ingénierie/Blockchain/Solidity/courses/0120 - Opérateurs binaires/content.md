## Qu'est-ce qu'un opérateur ?

Prenons une expression simple : **4 + 5** est égal à **9**. Ici, **4** et **5** sont appelés **opérandes** et '**+**' est appelé l'**opérateur**. Solidity prend en charge les types d'opérateurs suivants :

- Opérateurs arithmétiques
- Opérateurs de comparaison
- Opérateurs logiques (ou relationnels)
- Opérateurs d'affectation
- Opérateurs conditionnels (ou ternaires)

## Opérateurs binaires

### AND (&)

Il effectue un **Booléen ET une opération** sur chaque bit de ses arguments entiers. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 2; 
        uint b = 3;
        uint result = a & b; // opération binaire
        return result;
    }
}
```

L’exemple ci-dessus renverra “2”.

### OR (|)

Il effectue un **Booléen OU une opération** sur chaque bit de ses arguments entiers. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 2; 
        uint b = 3;
        uint result = a | b; // opération binaire
        return result;
    }
}
```

L’exemple ci-dessus renverra “3”.

### XOR (^)

Elle effectue une **booléenne exclusive OU une opération** sur chaque bit de ses arguments entiers. L'opération OU exclusif signifie que soit l'opérande un est vrai, soit l'opérande deux est vrai, mais pas les deux. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 2; 
        uint b = 3;
        uint result = a ^ b; // opération binaire
        return result;
    }
}
```

L’exemple ci-dessus renverra “1”.

### NOT (~)

C'est un opérateur unaire qui opère en inversant tous les bits de l'opérande. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 3;
        uint result = ~ a; // opération binaire
        return result;
    }
}
```

L’exemple ci-dessus renverra “-4”.

### Déplacement vers la gauche (<<)

Elle déplace tous les bits de son premier opérande vers la gauche du nombre de places spécifié dans le second opérande. Les nouveaux bits sont remplis de zéros. Décaler une valeur vers la gauche d'une position revient à la multiplier par 2, décaler de deux positions revient à la multiplier par 4, et ainsi de suite. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 2;
        uint result = a << 1; // opération binaire
        return result;
    }
}
```

L’exemple ci-dessus renverra “4”.

### Déplacement vers la droite (>>)

Opérateur de décalage binaire à droite. La valeur de l'opérande de gauche est déplacée vers la droite du nombre de bits spécifié par l'opérande de droite. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 2;
        uint result = a >> 1; // opération binaire
        return result;
    }
}
```

L’exemple ci-dessus renverra “1”.

### Déplacement vers la droite avec zéro (>>>)

Cet opérateur est identique à l'opérateur >>, sauf que les bits décalés à gauche sont toujours zéro. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 2;
        uint result = a >>> 1; // opération binaire
        return result;
    }
}
```

L’exemple ci-dessus renverra “1”.