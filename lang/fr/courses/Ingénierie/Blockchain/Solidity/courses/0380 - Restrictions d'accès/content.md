L'accès restreint à un contrat est une pratique courante. Par défaut, l'état d'un contrat est en lecture seule, sauf s'il est spécifié comme public.

Nous pouvons restreindre qui peut modifier l'état du contrat ou appeler les fonctions d'un contrat en utilisant des modificateurs. Nous allons créer et utiliser plusieurs modificateurs, comme expliqué ci-dessous.

- ```onlyBy``` - une fois utilisé sur une fonction, seul l'appelant mentionné peut appeler cette fonction.
- ```onlyAfter``` - une fois utilisé sur une fonction, cette fonction peut être appelée après une certaine période de temps.
- ```costs``` - une fois utilisé sur une fonction, l'appelant peut appeler cette fonction uniquement si une certaine valeur est fournie.

## Exemple

```solidity
pragma solidity ^0.5.0;

contract Test {
    address public owner = msg.sender;
    uint public creationTime = now;

    modifier onlyBy(address _account) {
        require(
            msg.sender == _account,
            "Sender not authorized."
        );
        _;
    }
    function changeOwner(address _newOwner) public onlyBy(owner) {
        owner = _newOwner;
    }
    modifier onlyAfter(uint _time) {
        require(
            now >= _time,
            "Function called too early."
        );
        _;
    }
    function disown() public onlyBy(owner) onlyAfter(creationTime + 6 weeks) {
        delete owner;
    }
    modifier costs(uint _amount) {
        require(
            msg.value >= _amount,
            "Not enough Ether provided."
        );
        _;
        if (msg.value > _amount)
            msg.sender.transfer(msg.value - _amount);
    }
    function forceOwnerChange(address _newOwner) public payable costs(200 ether) {
        owner = _newOwner;
        if (uint(owner) & 0 == 1) return;        
    }
}
```