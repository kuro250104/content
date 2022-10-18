Le PHP est un langage de programmation informatique. Tout comme les autres, il est nécessaire de créer des fichiers qui vont contenir le code réalisé afin qu’il puisse ensuite être interprété par une machine. Les fichiers contenants du PHP doivent posséder l’extension ```.php``` afin de signifier leurs types aux ordinateurs, de telle sorte à ce que ceux-ci puissent les interpréter.

Une fois l’extension définie, il faut délimiter le code à interpréter au sein d’un fichier PHP. Pour cela, il faut placer l’ensemble du code PHP entre la balise ouvrante ```<?php``` et la balise fermante ```?>```. Tout le code situé au milieu de ces deux balises sera supposé être du PHP et donc interprété comme tel par la machine.

Il faut ici noter deux notions importantes :

- Un fichier PHP ne contient pas obligatoirement uniquement du PHP. Il peut par exemple contenir du HTML, ou bien encore du CSS. Il ne faut donc pas être étonné de trouver du code “étranger” au sein d’un fichier PHP. Il n’est d’ailleurs pas rare de transformer un fichier HTML en PHP lorsque l’on souhaite ajouter du PHP au sein d’un fichier HTML existant. Pour ce faire, il suffit de changer l’extension du fichier de ```.html``` à ```.php```.
- Il est possible d’intégrer plusieurs balises ouvrantes et fermantes au sein d’un seul et même fichier PHP. La seule règle concernant ce point réside dans le fait de bien respecter l’ordre d’utilisation de celles-ci : Toute balise ouverte doit être fermée avant d’en ouvrir une autre !

Il reste néanmoins possible de réaliser des fichiers en PHP uniquement. Dans ce cadre-là, il arrive qu’il ne faille pas mettre de balise fermante en fin de fichier, mais uniquement une balise ouvrante au début de celui-ci. La règle de l’extension en ```.php``` reste inchangée.

En développant en PHP, et en fonction des projets à concevoir, il est possible que le code à rédiger soit bien trop important pour n’être contenu que dans un seul et même fichier. Il faut donc bien noter qu’il est convenable de créer autant de fichiers PHP que souhaité.