GridFS est la spécification MongoDB pour le stockage et la récupération de fichiers volumineux tels que des images, des fichiers audio, des fichiers vidéo, etc. Il s'agit en quelque sorte d'un système de fichiers pour stocker des fichiers, mais ses données sont stockées dans des collections MongoDB. GridFS a la capacité de stocker des fichiers dont la taille dépasse la limite de 16 Mo fixée pour les documents.

GridFS divise un fichier en morceaux et stocke chaque morceau de données dans un document séparé, chacun ayant une taille maximale de 255k.

GridFS utilise par défaut deux collections ```fs.files``` et ```fs.chunks``` pour stocker les métadonnées du fichier et les chunks. Chaque chunk est identifié par son champ unique _id ObjectId. Le ```fs.files``` sert de document parent. Le champ files_id dans le document fs.chunks relie le chunk à son parent.

Voici un exemple de document de la collection ```fs.files```.

```
{
    "filename": "test.txt",
    "chunkSize": NumberInt(261120),
    "uploadDate": ISODate("2014-04-13T11:32:33.557Z"),
    "md5": "7b762939321e146569b07f72c62cca4f",
    "length": NumberInt(646)
}
```

Le document précise le nom du fichier, la taille du morceau, la date de téléchargement et la longueur.

Voici un exemple de document de fs.chunks.

```
{
    "files_id": ObjectId("534a75d19f54bfec8a2fe44b"),
    "n": NumberInt(0),
    "data": "Mongo Binary Data"
}
```

## Ajouter des fichiers à GridFS

Maintenant, nous allons stocker un fichier mp3 à l'aide de GridFS en utilisant la commande put. Pour cela, nous allons utiliser l'utilitaire mongofiles.exe présent dans le dossier bin du dossier d'installation de MongoDB.

Ouvrez votre invite de commande, naviguez jusqu'à ```mongofiles.exe``` dans le dossier bin du dossier d'installation de MongoDB et saisissez le code suivant -

```
>mongofiles.exe -d gridfs put song.mp3
```

Ici, gridfs est le nom de la base de données dans laquelle le fichier sera stocké. Si la base de données n'est pas présente, MongoDB créera automatiquement un nouveau document à la volée. Song.mp3 est le nom du fichier téléchargé. Pour voir le document du fichier dans la base de données, vous pouvez utiliser find query -

```
>db.fs.files.find()
```

La commande ci-dessus a renvoyé le document suivant -

```
{
    _id: ObjectId('534a811bf8b4aa4d33fdf94d'), 
    filename: "song.mp3", 
    chunkSize: 261120, 
    uploadDate: new Date(1397391643474), md5: "e4f53379c909f7bed2e9d631e15c1c41",
    length: 10401959 
}
```

Nous pouvons également voir tous les chunks présents dans la collection fs.chunks liés au fichier stocké avec le code suivant, en utilisant l'id du document retourné dans la requête précédente -

```
>db.fs.chunks.find({files_id:ObjectId('534a811bf8b4aa4d33fdf94d')})
```

Dans mon cas, la requête a retourné 40 documents, ce qui signifie que l'ensemble du document mp3 a été divisé en 40 morceaux de données.