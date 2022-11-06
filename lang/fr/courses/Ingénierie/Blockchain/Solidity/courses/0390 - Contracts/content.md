Un contrat dans Solidity est similaire à une classe en C++. Un contrat a les propriétés suivantes :

- **Constructeur** - Une fonction spéciale déclarée avec le mot clé constructor qui sera exécutée une fois par contrat et qui est invoquée lorsqu'un contrat est créé.
- **Variables d'état** - Variables par contrat pour stocker l'état du contrat.
- **Fonctions** - Fonctions par contrat qui peuvent modifier les variables d'état pour modifier l'état d'un contrat.

## Quantificateurs de visibilité

Voici différents quantificateurs de visibilité pour les fonctions/variables d'état d'un contrat :

- **external** - Les fonctions externes sont destinées à être appelées par d'autres contrats. Elles ne peuvent pas être utilisées pour un appel interne. Pour appeler une fonction externe dans un contrat, il faut appeler this.function_name(). Les variables d'état ne peuvent pas être marquées comme externes.
- **public** - Les fonctions/variables publiques peuvent être utilisées à la fois en externe et en interne. Pour une variable d'état publique, Solidity crée automatiquement une fonction getter.
- **internal** - Les fonctions/variables internes ne peuvent être utilisées qu'en interne ou par des contrats dérivés.
- **private** - Les fonctions/variables privées ne peuvent être utilisées qu'en interne et pas même par des contrats dérivés.

## Exemple

```solidity
pragma solidity ^0.5.0;

contract C {
    //private state variable
    uint private data;
    
    //public state variable
    uint public info;

    //constructor
    constructor() public {
        info = 10;
    }
    //private function
    function increment(uint a) private pure returns(uint) { return a + 1; }
    
    //public function
    function updateData(uint a) public { data = a; }
    function getData() public view returns(uint) { return data; }
    function compute(uint a, uint b) internal pure returns (uint) { return a + b; }
}
//External Contract
contract D {
    function readData() public returns(uint) {
        C c = new C();
        c.updateData(7);         
        return c.getData();
    }
}
//Derived Contract
contract E is C {
    uint private result;
    C private c;
    
    constructor() public {
        c = new C();
    }  
    function getComputedResult() public {      
        result = compute(3, 5); 
    }
    function getResult() public view returns(uint) { return result; }
    function getData() public view returns(uint) { return c.info(); }
}
```

Exécutez les différentes méthodes des Contrats. Pour ```E.getComputedResult()``` suivi de ```E.getResult()``` montre :

## Rendu

```solidity
0: uint256: 8
```