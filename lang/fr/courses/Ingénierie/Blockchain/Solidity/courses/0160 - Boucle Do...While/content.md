La boucle **do...while** est similaire à la boucle **while**, sauf que la vérification de la condition se fait à la fin de la boucle. Cela signifie que la boucle sera toujours exécutée au moins une fois, même si la condition est fausse.

## Syntaxe

La syntaxe de la boucle do...while dans Solidity est la suivante :

```solidity
do {
    Statement(s) to be executed;
} while (expression);
```

__Remarque__ :  N’oubliez pas le point-virgule utilisé à la fin de la boucle **do...while**.

## Exemple

Essayez l'exemple suivant pour apprendre comment mettre en œuvre une boucle do...while dans Solidity.

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    uint storedData; 
    constructor() public{
        storedData = 10;   
    }
    function getResult() public view returns(string memory){
        uint a = 10; 
        uint b = 2;
        uint result = a + b;
        return integerToString(result); 
    }
    function integerToString(uint _i) internal pure 
        returns (string memory) {
        
        if (_i == 0) {
            return "0";
        }
        uint j = _i;
        uint len;
        
        while (j != 0) {
            len++;
            j /= 10;
        }
        bytes memory bstr = new bytes(len);
        uint k = len - 1;
        
        do {                   // do while loop	
            bstr[k--] = byte(uint8(48 + _i % 10));
            _i /= 10;
        }
        while (_i != 0);
        return string(bstr);
    }
}
```

Rendu :

```solidity
0: string: 12
```