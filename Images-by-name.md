The server will create an ImagesByName folder within it's program data folder, located at:

`C:\Users\{Username}\AppData\Roaming\MediaBrowser-Server\ImagesByName`

Inside this folder will be several sub-folders, including:

* Artist
* Genre
* MusicGenre
* GameGenre
* People
* Studio
* Year

As the server scans media it will create folders for genres, people, etc in these locations. You are then able to add images as desired using the conventions discussed in [library structure.](https://github.com/MediaBrowser/MediaBrowser/wiki/Library-Structure)

Note: If you place new images within the Genre or Studios folders, they will not show up until you restart the server.