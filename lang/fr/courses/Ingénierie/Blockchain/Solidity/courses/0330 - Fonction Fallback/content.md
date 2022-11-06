La fonction Fallback est une fonction spéciale disponible pour un contrat. Elle possède les caractéristiques suivantes :

- Elle est appelée lorsqu'une fonction inexistante est appelée sur le contrat.
- Elle doit être marquée comme externe.
- Elle n'a pas de nom.
- Elle n'a pas d'arguments
- Elle ne peut renvoyer aucun élément.
- Elle peut être définie une fois par contrat.
- Si elle n'est pas marquée payable, elle lèvera une exception si le contrat reçoit de l'éther simple sans données.

L'exemple suivant montre le concept d'une fonction de repli par contrat.

## Exemple

```solidity
pragma solidity ^0.5.0;

contract Test {
    uint public x ;
    function() external { x = 1; }    
}
contract Sink {
    function() external payable { }
}
contract Caller {
    function callTest(Test test) public returns (bool) {
        (bool success,) = address(test).call(abi.encodeWithSignature("nonExistingFunction()"));
        require(success);
        // test.x is now 1

        address payable testPayable = address(uint160(address(test)));

        // Sending ether to Test contract,
        // the transfer will fail, i.e. this returns false here.
        return (testPayable.send(2 ether));
    }
    function callSink(Sink sink) public returns (bool) {
        address payable sinkPayable = address(sink);
        return (sinkPayable.send(2 ether));
    }
}
```