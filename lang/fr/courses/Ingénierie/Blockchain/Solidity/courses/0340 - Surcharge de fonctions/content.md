Vous pouvez avoir plusieurs définitions pour le même nom de fonction dans la même portée. Les définitions de la fonction doivent différer les unes des autres par les types et/ou le nombre d'arguments dans la liste des arguments. Vous ne pouvez pas surcharger les déclarations de fonctions qui ne diffèrent que par le type de retour.

L'exemple suivant montre le concept de surcharge de fonction dans Solidity.

## Exemple

```solidity
pragma solidity ^0.5.0;

contract Test {
    function getSum(uint a, uint b) public pure returns(uint){      
        return a + b;
    }
    function getSum(uint a, uint b, uint c) public pure returns(uint){      
        return a + b + c;
    }
    function callSumWithTwoArguments() public pure returns(uint){
        return getSum(1,2);
    }
    function callSumWithThreeArguments() public pure returns(uint){
        return getSum(1,2,3);
    }
}
```

Cliquez d'abord sur le bouton **callSumWithTwoArguments**, puis sur le bouton **callSumWithThreeArguments** pour voir le résultat.

## Rendu

```solidity
0: uint256: 3
0: uint256: 6
```