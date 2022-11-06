Ce cours explique comment configurer le compilateur Solidity sur une machine CentOS.

## Méthode 1 - npm / Node.js

C'est le moyen le plus rapide d'installer le compilateur Solidity sur votre machine CentoS. Voici les étapes de l'installation du compilateur Solidity

### Installer Node.js

Assurez-vous d'abord que node.js est disponible sur votre machine CentOS. S'il n'est pas disponible, installez-le à l'aide des commandes suivantes

```bash
# Installez d'abord epel-release
sudo yum install epel-release

# Maintenant, installez nodejs
sudo yum install nodejs

# Ensuite installez npm (Nodejs Package Manager )
sudo yum install npm

# Enfin, vérifiez l'installation
npm --version
```

Si tout a été installé, vous obtiendrez une sortie comme celle-ci :

```bash
3.10.10
```

__Remarque__ : Si ce type d’installation ne correspond pas à votre système, vous pouvez trouver différentes manières d’installer Node.js, notamment sur leur site web officiel.

### Installer solc

Une fois que le gestionnaire de paquets Node.js est installé, vous pouvez procéder à l'installation du compilateur Solidity comme suit :

```bash
sudo npm install -g solc
```

La commande ci-dessus installera le programme **solcjs** et le rendra disponible globalement dans tout le système. Maintenant, vous pouvez tester votre compilateur Solidity en lançant la commande suivante :

```bash
# installer solc
sudonpm install -g solcjs - $sudonpm install -g solc

# vérifier l'installation
solcjs-version
```

Si tout se passe bien, vous obtiendrez quelque chose comme suit :

```bash
0.5.2+commit.1df8f40c.Emscripten.clang
```

Vous êtes maintenant prêt à utiliser **solcjs** qui a moins de fonctionnalités que le compilateur Solidity standard mais qui vous donnera un bon point de départ.

__Remarque__ : Tout comme pour Node.js, n’hésitez pas à consulter le site officiel de **solcjs** si toutefois ce guide d’installation ne correspond pas à votre système.

## Méthode 2 - Image Docker

Vous pouvez extraire une image Docker et l'utiliser pour commencer à programmer avec Solidity. Voici les étapes simples à suivre. Voici la commande pour extraire une image Docker de Solidity.

```bash
docker pull ethereum/solc:stable
```

Une fois l'image Docker téléchargée, nous pouvons le vérifier en utilisant la commande suivante :

```bash
docker run ethereum/solc:stable-version
```

Ceci imprimera quelque chose comme suit :

```bash
docker run ethereum/solc:stable -version

solc, le compilateur solidity commandlineinterfaceVersion : 0.5.2+commit.1df8f40c.Linux.g++
```

## Méthode 3 : Installation des paquets binaires

Si vous souhaitez installer un compilateur complet sur votre machine Linux, veuillez consulter le site officiel Installer le compilateur Solidity.