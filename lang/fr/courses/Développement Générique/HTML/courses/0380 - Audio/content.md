Le langage HTML permet d’insérer des fichiers audio au sein d’une page web.

## Formats audios en HTML

Comme pour les vidéos, le langage HTML prend en charge 3 formats audios :

| **Navigateur** | **Type de media** |
| --- | --- |
| MP3 | audio/mpeg |
| OGG | audio/ogg |
| WAV | audio/wav |

## Formats et prise en charge des navigateurs

Le tableau ci-dessous résume la prise en charge des trois formats selon le navigateur :

| Navigateur | **MP3** | **WAV** | **OGG** |
| --- | --- | --- | --- |
| Edge/IE | Oui | Non | Non |
| Chrome | Oui | Oui | Oui |
| Firefox | Oui | Oui | Oui |
| Safari | Oui | Oui | Non |
| Opera | Oui | Oui | Oui |

## Prise en charge par les navigateurs

La prise en charge des fichiers audios par le HTML étant relativement récente - elle n’existait pas avant la version 5 du langage - l’élément ```<audio>``` n’est pas supporté par les anciennes versions des navigateurs Internet.

Le tableau ci-dessous résume, pour les navigateurs les plus couramment utilisés, la version à partir de laquelle l’audio est pris en charge :

| **Navigateur** | **Version** |
| --- | --- |
| Chrome | 4.0 |
| Edge/IE | 9.0 |
| Firefox | 3.5 |
| Safari | 4.0 |
| Opera | 10.5 |

## L'élément ```<audio>```

Pour insérer un fichier au sein d’une page web, l’élément ```<audio></audio>``` doit être utilisé. Cet élément est accompagné de l’attribut ```controls``` permettant d’afficher un bouton play/pause ainsi que le contrôle du volume. 

Ensuite, pour inclure le fichier audio, cela fonctionne exactement comme pour l’insertion d’une vidéo. L’élément ```<source>``` est utilisé, accompagné de l’attribut ```src```, qui prend en valeur le chemin d’accès au fichier audio. L’attribut ```type``` est également utilisé, recevant en valeur *audio/format_de_l’audio*.

Exemple :

```html
<audio controls>
    <source src="chat.ogg" type="audio/ogg">
    <source src="chat.mp3" type="audio/mpeg">
</audio>
```
