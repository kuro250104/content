## Introduction

Le test est l'un des processus permettant de s'assurer que la fonctionnalité créée dans toute application fonctionne conformément à la logique métier et aux spécifications de codage. React recommande la bibliothèque React testing pour tester les composants React et jest test runner pour exécuter le test. La bibliothèque react-testing-library permet de vérifier les composants de manière isolée.

Il peut être installé dans l'application à l'aide de la commande ci-dessous.

```bash
npm install --save @testing-library/react @testing-library/jest-dom
```

## Create React app

Create React app configure la bibliothèque de test React et le gestionnaire de test jest par défaut. Ainsi, pour tester une application React créée à l'aide de Create React App, il suffit d'une commande.

```bash
cd /go/to/react/application 
npm test
```

La commande npm test est similaire à la commande npm build. Les deux recompilent au fur et à mesure que le développeur modifie le code. Une fois que la commande est exécutée dans l'invite de commande, elle émet les questions ci-dessous.

```bash
No tests found related to files changed since last commit.
Press `a` to run all tests, or run Jest with `--watchAll`.

Watch Usage
   > Press a to run all tests.
   > Press f to run only failed tests.
   > Press q to quit watch mode.
   > Press p to filter by a filename regex pattern.
   > Press t to filter by a test name regex pattern.
   > Press Enter to trigger a test run.  
```

En appuyant sur a, on essaiera d'exécuter tous les scripts de test et on résumera le résultat comme indiqué ci-dessous.

```bash
Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        4.312 s, estimated 12 s
Ran all test suites.

Watch Usage: Press w to show more. 
```

## Test dans une application personnalisée

Écrivons une application React personnalisée à l'aide du bundler Rollup et testons-la à l'aide de la bibliothèque de test React et de l'exécuteur de test jest dans ce chapitre.

Tout d'abord, créez une nouvelle application React, react-test-app en utilisant le bundler Rollup en suivant les instructions du chapitre Création d'une application React.

Next, install the testing library.

```bash
cd /go/to/react-test-app 
npm install --save @testing-library/react @testing-library/jest-dom
```

Ensuite, ouvrez l'application dans votre éditeur préféré.

Ensuite, créez un fichier, HelloWorld.test.js sous le dossier src/components pour écrire le test du composant HelloWorld et commencez à le modifier.

Ensuite, importez la bibliothèque react.

```js
import React from 'react';
```

Ensuite, importez la bibliothèque de test.

```js
import { render, screen } from '@testing-library/react'; import '@testing-library/jest-dom';
```

Ensuite, importez notre composant HelloWorld.

```js
import HelloWorld from './HelloWorld';
```

Ensuite, écrivez un test pour vérifier l'existence du texte Hello World dans le document.

```js
test('test scenario 1', () => {
    render(<HelloWorld />);
    const element = screen.getByText(/Hello World/i);
    expect(element).toBeInTheDocument();
});
```

Le code source complet du code de test est donné ci-dessous -

```js
import React from 'react';
import { render, screen } from '@testing-library/react';
import '@testing-library/jest-dom';
import HelloWorld from './HelloWorld';

test('test scenario 1', () => {
    render(<HelloWorld />);
    const element = screen.getByText(/Hello World/i);
    expect(element).toBeInTheDocument();
});
```

Ensuite, installez jest test runner, s'il n'est pas déjà installé dans le système.

```bash
npm install jest -g
```

Ensuite, exécutez la commande jest dans le dossier racine de l'application.

```bash
jest
```

Ensuite, exécutez la commande jest dans le dossier racine de l'application.

```bash
PASS  src/components/HelloWorld.test.js
    √ test scenario 1 (29 ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        5.148 s
Ran all test suites.
```