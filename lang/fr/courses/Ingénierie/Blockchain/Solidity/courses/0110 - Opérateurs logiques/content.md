## Qu'est-ce qu'un opérateur ?

Prenons une expression simple : **4 + 5** est égal à **9**. Ici, **4** et **5** sont appelés **opérandes** et '**+**' est appelé l'**opérateur**. Solidity prend en charge les types d'opérateurs suivants :

- Opérateurs arithmétiques
- Opérateurs de comparaison
- Opérateurs logiques (ou relationnels)
- Opérateurs d'affectation
- Opérateurs conditionnels (ou ternaires)

## Opérateurs logiques

### ET (&&)

Si les deux opérandes sont différents de zéro, alors la condition devient vraie. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1; 
        uint b = 0;
        if (a && b) { // opérateur de comparaison
            return "vrai";
        }
        return "faux";
    }
}
```

L’exemple ci-dessus renverra “faux”.

### OU (||)

Si l'un des deux opérandes est différent de zéro, alors la condition devient vraie. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1; 
        uint b = 0;
        if (a || b) { // opérateur de comparaison
            return "vrai";
        }
        return "faux";
    }
}
```

L’exemple ci-dessus renverra “vrai”.

### NON (!)

Inverse l'état logique de son opérande. Si une condition est vraie, l'opérateur logique NOT la rendra fausse. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1; 
        uint b = 0;
        if (!(a || b)) { // opérateur de comparaison
            return "vrai";
        }
        return "faux";
    }
}
```

L’exemple ci-dessus renverra “faux”.