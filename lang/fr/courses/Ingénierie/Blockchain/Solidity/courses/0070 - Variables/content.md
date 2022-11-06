Solidity prend en charge trois types de variables :

- **Variables d'état (State Variables)** - Variables dont les valeurs sont stockées en permanence dans une mémoire de contrat.
- **Variables locales (Local Variables)** - Variables dont les valeurs sont présentes jusqu'à ce que la fonction soit exécutée.
- **Variables globales (Global Variables)** - Variables spéciales existant dans l'espace de noms global utilisées pour obtenir des informations sur la blockchain.

Solidity est un langage à typage statique, ce qui signifie que le type de variable d'état ou locale doit être spécifié lors de la déclaration. Chaque variable déclarée a toujours une valeur par défaut basée sur son type. Il n'y a pas de concept de "undefined" ou "null".

## Variable d'état

Variables dont les valeurs sont stockées de façon permanente dans une mémoire de contrat.

```solidity
pragma solidity ^0.5.0;
contract SolidityTest {
    uint storedData;      // State variable
    constructor() public {
        storedData = 10;   // Using State variable
    }
}
```

## Variable locale

Variable dont les valeurs ne sont disponibles qu'à l'intérieur de la fonction dans laquelle elle est définie. Les paramètres de fonction sont toujours locaux à cette fonction.

```solidity
pragma solidity ^0.5.0;
contract SolidityTest {
    uint storedData; // State variable
    constructor() public {
        storedData = 10;   
    }
    function getResult() public view returns(uint){
        uint a = 1; // local variable
        uint b = 2;
        uint result = a + b;
        return result; //access the local variable
    }
}
```

Exemple : 

```solidity
pragma solidity ^0.5.0;
contract SolidityTest {
    uint storedData; // State variable
    constructor() public {
        storedData = 10;   
    }
    function getResult() public view returns(uint){
        uint a = 1; // local variable
        uint b = 2;
        uint result = a + b;
        return storedData; //access the state variable
    }
}
```

Exécutez le programme ci-dessus en suivant les étapes fournies dans le chapitre “Créer une application”.

Sortie :

```bash
0: uint256: 10
```

## Variables globales

Il s'agit de variables spéciales qui existent dans l'espace de travail global et qui fournissent des informations sur les propriétés de la blockchain et des transactions.

| **Name** | **Returns** |
| --- | --- |
| blockhash(uint blockNumber) returns (bytes32) | Hachage du bloc donné - ne fonctionne que pour les 256 blocs les plus récents, à l'exclusion des blocs actuels. |
| block.coinbase (address payable) | Adresse du mineur du bloc actuel |
| block.difficulty (uint) | Difficulté du bloc actuel |
| block.gaslimit (uint) | Limite de gaz du bloc actuel |
| block.number (uint) | Numéro du bloc actuel |
| block.timestamp (uint) | Horodatage du bloc actuel en secondes depuis l'époque unix. |
| gasleft() returns (uint256) | Gaz résiduel |
| msg.data (bytes calldata) | Données d'appel complètes |
| msg.sender (address payable) | Expéditeur du message (appelant actuel) |
| msg.sig (bytes4) | Les quatre premiers octets des données d'appel (identifiant de la fonction). |
| msg.value (uint) | Nombre de wei envoyés avec le message |
| now (uint) | Horodatage du bloc actuel |
| tx.gasprice (uint) | Prix du gaz de la transaction |
| tx.origin (address payable) | Expéditeur de la transaction |

## Noms des variables de Solidity

Lorsque vous nommez vos variables dans Solidity, gardez à l'esprit les règles suivantes :

- Vous ne devez pas utiliser l'un des mots-clés réservés de Solidity comme nom de variable. Ces mots-clés sont mentionnés dans le cours sur les “Types”. Par exemple, les noms de variables “break” ou “boolean” ne sont pas valides.
- Les noms de variables Solidity ne doivent pas commencer par un chiffre (0-9). Ils doivent commencer par une lettre ou un caractère de soulignement. Par exemple, 123test est un nom de variable invalide, mais **_123test** est un nom valide.
- Les noms de variables Solidity sont sensibles à la casse. Par exemple, **Name** et **name** sont deux variables différentes.