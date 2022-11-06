L'héritage est un moyen d'étendre la fonctionnalité d'un contrat. Solidity prend en charge l'héritage simple et l'héritage multiple. Voici les principaux points forts.

- Un contrat dérivé peut accéder à tous les membres non privés, y compris les méthodes internes et les variables d'état. Mais son utilisation n'est pas autorisée.
- La substitution de fonctions est autorisée à condition que la signature de la fonction reste la même. En cas de différence entre les paramètres de sortie, la compilation échouera.
- On peut appeler la fonction d'un super contrat en utilisant le mot clé super ou le nom du super contrat.
- En cas d'héritage multiple, l'appel de la fonction à l'aide de super donne la préférence au contrat le plus dérivé.

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