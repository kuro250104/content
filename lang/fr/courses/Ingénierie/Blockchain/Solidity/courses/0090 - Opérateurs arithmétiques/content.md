## Qu'est-ce qu'un opérateur ?

Prenons une expression simple : **4 + 5** est égal à **9**. Ici, **4** et **5** sont appelés **opérandes** et '**+**' est appelé l'**opérateur**. Solidity prend en charge les types d'opérateurs suivants :

- Opérateurs arithmétiques
- Opérateurs de comparaison
- Opérateurs logiques (ou relationnels)
- Opérateurs d'affectation
- Opérateurs conditionnels (ou ternaires)

## Opérateurs arithmétiques

### Addition (+)

Additionne plusieurs opérandes. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1; 
        uint b = 2;
        uint result = a + b; //arithmetic operation
        return result; // retournera 3
    }
}
```

### Soustraction (-)

Soustrait plusieurs opérandes. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
    constructor() public{
    }
    function getResult() public view returns(uint){
        uint a = 1; 
        uint b = 2;
        uint result = b - a; //arithmetic operation
        return result; // retournera 1
    }
}
```

### Multiplication (*)
Multiplie plusieurs opérandes. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
   constructor() public{
   }
   function getResult() public view returns(uint){
      uint a = 1; 
      uint b = 2;
      uint result = a * b; //arithmetic operation
      return result; // retournera 2
   }
}
```

### Division (/)

Divise le numérateur (b) par le dénominateur (a). Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
   constructor() public{
   }
   function getResult() public view returns(uint){
      uint a = 1; 
      uint b = 2;
      uint result = b / a; //arithmetic operation
      return result; // retournera 2
   }
}
```

### Modulo (%)

Renvoie le reste d’une division entière. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
   constructor() public{
   }
   function getResult() public view returns(uint){
      uint a = 1; 
      uint b = 2;
      uint result = b % a; //arithmetic operation
      return result; // retournera 0
   }
}
```

### Incrémentation (++)

Additionne 1 à une valeur. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
   constructor() public{
   }
   function getResult() public view returns(uint){
      uint a = 2; 
      a++; //arithmetic operation
      return result; // retournera 3
   }
}
```

### Décrémentation (--)

Soustrait 1 à une valeur. Par exemple :

```solidity
pragma solidity ^0.5.0;

contract SolidityTest {
   constructor() public{
   }
   function getResult() public view returns(uint){
      uint a = 2; 
      a--; //arithmetic operation
      return result; // retournera 1
   }
}
```