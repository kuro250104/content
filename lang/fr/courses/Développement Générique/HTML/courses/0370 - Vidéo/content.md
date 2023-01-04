S’il est un format d’élément multimédia devenu très populaire ces 10 dernières années, c’est bien le format vidéo. Il en existe de plus en plus, et il existe de plus en plus de sites web qui en contiennent. 

Le langage HTML permet donc aux développeurs web d’ajouter des vidéos sur les pages web.

## L'élément video

Pour insérer une vidéo dans une page web - si cette vidéo ne provient pas directement d’une source externe telle que YouTube - l’élément ```<video></video>``` doit être utilisé.

Cet élément est accompagné de l’attribut ```controls```, qui ne reçoit aucune valeur, mais qui permet d’ajouter des contrôles de vidéo, tels que lecture, pause et la gestion du volume.

__Remarque__ : L’élément ```<video></video>``` est un conteneur. C’est à l’intérieur de cet élément que les vidéos sont affichées.

Ensuite, pour indiquer au navigateur quelle vidéo afficher, l’élément ```<source>``` doit être utilisé. Cet élément s’accompagne des attribut ```src```, qui reçoit en valeur le chemin d’accès à la vidéo, et ```type```, qui reçoit en valeur vidéo/format.

__Remarque__ : Il est recommandé d’inclure plusieurs formats pour une même vidéo. Ainsi le navigateur de l’utilisateur peut-il choisir le format qu’il prend en charge. 

Exemple :

```html
<video width="320" height="240" controls>
    <source src="moto.mp4" type="video/mp4">
    <source src="moto.ogg" type="video/ogg">
    Votre navigateur ne peut pas lire cette vidéo.
</video>
```

## Lecture automatique

Le langage HTML permet de lire une vidéo automatiquement lors du premier chargement de la page. Pour ce faire, il faut inclure l’attribut ```autoplay``` dans l’élément ```<video>```. Cet attribut ne reçoit aucune valeur.

__Remarque__ : La lecture automatique de vidéo ne fonctionne pas sur les appareils mobiles. 

Exemple :

```html
<video width="320" height="240" controls>
    <source src="moto.mp4" type="video/mp4">
    <source src="moto.ogg" type="video/ogg">
    Votre navigateur ne peut pas écouter ce son.
</video>
```

## Formats vidéo HTML

Le tableau ci-dessous dresse la liste des formats vidéos pris en charge en fonction du navigateur :

| Navigateur | **MP3** | **WAV** | **OGG** |
| --- | --- | --- | --- |
| Edge/IE | Oui | Oui | Oui |
| Chrome | Oui | Oui | Oui |
| Firefox | Oui | Oui | Oui |
| Safari | Oui | Oui | Non |
| Opera | Oui | Oui | Oui |
