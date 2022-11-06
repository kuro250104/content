La portée des variables locales est limitée à la fonction dans laquelle elles sont définies, mais les variables d'état peuvent avoir trois types de portée :

- **Public** - Les variables d'état publiques sont accessibles en interne ainsi que par le biais de messages. Pour une variable d'état publique, une fonction getter automatique est générée.
- **Internal** - Les variables d'état internes sont accessibles uniquement en interne à partir du contrat actuel ou du contrat qui en découle sans utiliser cette fonction.
- **Private** - Les variables d'état privées ne sont accessibles qu'en interne, à partir du contrat en cours ou du contrat qui en découle, et non dans le contrat qui en est dérivé.

Exemple : 

```solidity
pragma solidity ^0.5.0;
contract C {
    uint public data = 30;
    uint internal iData= 10;
    
    function x() public returns (uint) {
        data = 3; // internal access
        return data;
    }
}
contract Caller {
    C c = new C();
    function f() public view returns (uint) {
        return c.data(); //external access
    }
}
contract D is C {
    function y() public returns (uint) {
        iData = 3; // internal access
        return iData;
    }
    function getResult() public view returns(uint){
        uint a = 1; // local variable
        uint b = 2;
        uint result = a + b;
        return storedData; //access the state variable
    }
}
```