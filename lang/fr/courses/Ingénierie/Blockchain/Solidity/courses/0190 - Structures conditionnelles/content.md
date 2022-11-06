Lors de l'écriture d'un programme, il peut arriver que vous deviez adopter un choix parmi un ensemble donné de chemins. Dans de tels cas, vous devez utiliser des instructions conditionnelles qui permettent à votre programme de prendre les bonnes décisions et d'effectuer les bonnes actions.

Solidity prend en charge les instructions conditionnelles qui sont utilisées pour effectuer différentes actions en fonction de différentes conditions.

## L’instruction if

L'instruction **if** est l'instruction de contrôle fondamentale qui permet à Solidity de prendre des décisions et d'exécuter des instructions de manière conditionnelle.

### Syntaxe

La syntaxe d'une instruction **if** de base est la suivante :

```solidity
if (expression) {
    Statement(s) to be executed if expression is true
}
```

Ici, une **expression** Solidity est évaluée. Si la valeur résultante est vraie, la ou les instructions données sont exécutées. Si l'expression est fausse, aucune instruction ne sera exécutée. La plupart du temps, vous utiliserez des opérateurs de comparaison pour prendre des décisions.

### Exemple

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    uint storedData; 
    constructor() public {
        storedData = 10;   
    }
    function getResult() public view returns(string memory){
        uint a = 1; 
        uint b = 2;
        uint result = a + b;
        return integerToString(result); 
    }
    function integerToString(uint _i) internal pure 
        returns (string memory) {
        if (_i == 0) {   // if statement
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

        while (_i != 0) {
            bstr[k--] = byte(uint8(48 + _i % 10));
            _i /= 10;
        }
        return string(bstr);//access local variable
    }
}
```

### Rendu

```solidity
0: string: 3
```

## L’instruction if...else

L'instruction 'if...else' est la forme suivante d'instruction de contrôle qui permet à Solidity d'exécuter des instructions d'une manière plus contrôlée.

### Syntaxe

```solidity
if (expression) {
    Statement(s) to be executed if expression is true
} else {
    Statement(s) to be executed if expression is false
}
```

Ici, l'expression Solidity est évaluée. Si la valeur résultante est vraie, la ou les instructions données dans le bloc '**if**' sont exécutées. Si l'expression est fausse, la ou les instructions du bloc else sont exécutées.

### Exemple

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    uint storedData; 
    constructor() public{
        storedData = 10;   
    }
    function getResult() public view returns(string memory){
        uint a = 1; 
        uint b = 2;
        uint result
        if( a > b) {   // if else statement
            result = a;
        } else {
            result = b;
        }       
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
        
        while (_i != 0) {
            bstr[k--] = byte(uint8(48 + _i % 10));
            _i /= 10;
        }
        return string(bstr);//access local variable
    }
}
```

### Rendu

```solidity
0: string: 2
```

## L’instruction if...else if…

L'instruction **if...else if...** est une forme avancée de **if...else** qui permet à Solidity de prendre une décision correcte à partir de plusieurs conditions.

### Syntaxe

La syntaxe d'une instruction **if-else-if** est la suivante :

```solidity
if (expression 1) {
    Statement(s) to be executed if expression 1 is true
} else if (expression 2) {
    Statement(s) to be executed if expression 2 is true
} else if (expression 3) {
    Statement(s) to be executed if expression 3 is true
} else {
    Statement(s) to be executed if no expression is true
}
```

Il n'y a rien de spécial dans ce code. Il s'agit simplement d'une série d'instructions **if**, où chaque **if** fait partie de la clause **else** de l'instruction précédente. La ou les déclarations sont exécutées en fonction de la condition vraie, si aucune des conditions n'est vraie, alors le bloc **else** est exécuté.

### Exemple

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    uint storedData; // State variable
    constructor() public {
        storedData = 10;   
    }
    function getResult() public view returns(string memory) {
        uint a = 1; 
        uint b = 2;
        uint c = 3;
        uint result
        
        if( a > b && a > c) {   // if else statement
            result = a;
        } else if( b > a && b > c ){
            result = b;
        } else {
            result = c;
        }       
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
        
        while (_i != 0) {
            bstr[k--] = byte(uint8(48 + _i % 10));
            _i /= 10;
        }
        return string(bstr);//access local variable
    }
}
```

### Rendu

```solidity
0: string: 3
```