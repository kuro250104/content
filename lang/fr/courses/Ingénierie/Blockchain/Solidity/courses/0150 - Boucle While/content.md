La boucle la plus basique dans Solidity est la boucle **while** qui sera abordée dans ce chapitre. Le but d'une boucle **while** est d'exécuter une instruction ou un bloc de code de manière répétée tant qu'une expression est vraie. Lorsque l'expression devient fausse, la boucle se termine.

## Syntaxe

La syntaxe de la boucle while dans Solidity est la suivante :

```solidity
while (expression) {
    Statement(s) to be executed if expression is true
}
```

## Exemple

Essayez l'exemple suivant pour mettre en œuvre la boucle while.

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
        
        while (_i != 0) { // while loop
            bstr[k--] = byte(uint8(48 + _i % 10));
            _i /= 10;
        }
        return string(bstr);
    }
}
```

Rendu :

```solidity
0: string: 12
```