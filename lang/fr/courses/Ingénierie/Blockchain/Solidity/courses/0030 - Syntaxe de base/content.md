Un fichier source de Solidity peut contenir un nombre quelconque de définitions de contrats, de directives d'importation et de directives de pragmatisme.

Commençons par un simple fichier source de Solidity. Voici un exemple de fichier Solidity :

```solidity
pragma solidity >=0.4.0 <0.6.0;
contract SimpleStorage {
    uint storedData;
    function set(uint x) public {
        storedData = x;
    }
    function get() public view returns (uint) {
        return storedData;
    }
}
```

## Pragma

La première ligne est une directive pragma qui indique que le code source est écrit pour la version 0.4.0 de Solidity ou toute autre version plus récente qui ne casse pas la fonctionnalité jusqu'à, mais sans inclure, la version 0.6.0.

Une directive pragma est toujours locale à un fichier source et si vous importez un autre fichier, le pragma de ce fichier ne s'appliquera pas automatiquement au fichier d'importation.

Ainsi, une directive pragma pour un fichier qui ne compilera pas avant la version 0.4.0 et qui ne fonctionnera pas non plus sur un compilateur à partir de la version 0.5.0 sera écrite comme suit :

```solidity
pragma solidity ^0.4.0;
```

Ici, la deuxième condition est ajoutée en utilisant ^.

## Contrat

Un contrat Solidity est un ensemble de code (ses fonctions) et de données (son état) qui réside à une adresse spécifique sur l'Ethereum blockchain.

La ligne **uintstoredData** déclare une variable d'état appelée **storedData** de type **uint** et les fonctions **set** et **get** peuvent être utilisées pour modifier ou récupérer la valeur de la variable.

## Importation de fichiers

Bien que l'exemple ci-dessus ne comporte pas d'instruction d'importation, Solidity prend en charge les instructions d'importation qui sont très similaires à celles disponibles en JavaScript.

L'instruction suivante importe tous les symboles globaux de "filename".

```solidity
import "filename";
```

L'exemple suivant crée un nouveau symbole global **symbolName** dont les membres sont tous les symboles globaux de "filename".

```solidity
import * as symbolName from "filename";
```

Pour importer un fichier **x** du même répertoire que le fichier actuel, utilisez ```import "./x" as x ;``` . Si vous utilisez ```import "x" as x ;``` à la place, un fichier différent pourrait être référencé dans un "répertoire d'inclusion" global.

## Mots clés réservés

Voici les mots-clés réservés dans Solidity :

- abstract
- after
- alias
- apply
- auto
- case
- catch
- copyof
- default
- define
- final
- immutable
- implements
- in
- inline
- let
- macro
- match
- mutable
- null
- of
- override
- partial
- promise
- reference
- relocatable
- sealed
- sizeof
- static
- supports
- switch
- try
- typedef
- typeof
- unchecked