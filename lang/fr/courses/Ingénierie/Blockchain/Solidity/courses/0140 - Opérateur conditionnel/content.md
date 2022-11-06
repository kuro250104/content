## Qu'est-ce qu'un opérateur ?

Prenons une expression simple : **4 + 5** est égal à **9**. Ici, **4** et **5** sont appelés **opérandes** et '**+**' est appelé l'**opérateur**. Solidity prend en charge les types d'opérateurs suivants :

- Opérateurs arithmétiques
- Opérateurs de comparaison
- Opérateurs logiques (ou relationnels)
- Opérateurs d'affectation
- Opérateurs conditionnels (ou ternaires)

## Opérateur conditionnel

L'opérateur conditionnel évalue d'abord une expression pour obtenir une valeur vraie ou fausse, puis exécute l'une des deux instructions données en fonction du résultat de l'évaluation. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    uint storedData; 
    constructor() public{
        storedData = 10;   
    }
    function getResult() public view returns(string memory){
        uint a = 1; // local variable
        uint b = 2;
        uint result = (a > b? a: b);  //conditional operation
        return integerToString(result); 
    }
}
```

L’exemple ci-dessus retourne “2”