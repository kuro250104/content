## Qu'est-ce qu'un opérateur ?

Prenons une expression simple : **4 + 5** est égal à **9**. Ici, **4** et **5** sont appelés **opérandes** et '**+**' est appelé l'**opérateur**. Solidity prend en charge les types d'opérateurs suivants :

- Opérateurs arithmétiques
- Opérateurs de comparaison
- Opérateurs logiques (ou relationnels)
- Opérateurs d'affectation
- Opérateurs conditionnels (ou ternaires)

## Opérateurs de comparaisons

### Égal (==)

Vérifie si la valeur de deux opérandes est égale ou non, si oui, alors la condition devient vraie. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1; 
        uint b = 2;
        if (a == b) { // opérateur de comparaison
            return "vrai";
        }
        return "faux";
    }
}
```

L’exemple ci-dessus renverra “faux”.

### Non égal (!=)

Vérifie si la valeur de deux opérandes est égale ou non, si les valeurs ne sont pas égales, alors la condition devient vraie. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1; 
        uint b = 2;
        if (a != b) { // opérateur de comparaison
            return "vrai";
        }
        return "faux";
    }
}
```

L’exemple ci-dessus renverra “vrai”.

### Plus grand que (>)

Vérifie si la valeur de l'opérande de gauche est supérieure à la valeur de l'opérande de droite, si oui, alors la condition devient vraie. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1; 
        uint b = 2;
        if (a > b) { // opérateur de comparaison
            return "vrai";
        }
        return "faux";
    }
}
```

L’exemple ci-dessus renverra “faux”.

### Plus petit que (<)

Vérifie si la valeur de l'opérande de gauche est inférieure à la valeur de l'opérande de droite, si oui, alors la condition devient vraie. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1; 
        uint b = 2;
        if (a < b) { // opérateur de comparaison
            return "vrai";
        }
        return "faux";
    }
}
```

L’exemple ci-dessus renverra “vrai”.

### Supérieur ou égal (>=)

Vérifie si la valeur de l'opérande de gauche est supérieure ou égale à la valeur de l'opérande de droite, si oui, alors la condition devient vraie. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1; 
        uint b = 2;
        if (a >= b) { // opérateur de comparaison
            return "vrai";
        }
        return "faux";
    }
}
```

L’exemple ci-dessus renverra “faux”.

### Inférieur ou égal (<=)

Vérifie si la valeur de l'opérande de gauche est inférieure ou égale à la valeur de l'opérande de droite, si oui, alors la condition devient vraie. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1; 
        uint b = 2;
        if (a <= b) { // opérateur de comparaison
            return "vrai";
        }
        return "faux";
    }
}
```

L’exemple ci-dessus renverra “vrai”.