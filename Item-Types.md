Media Browser has a number of core library item types. Api consumers can detect these types to customize their displays and/or query for these types individually to create virtual views.

The following core types are available:

### Audio
This is an audio file.

### Video
This is a generic video file.

### Folder
This is a generic folder.

### Episode, Movie, Trailer
These are specialized representations of Video.

### BoxSet, MusicAlbum, MusicArtist, Season, Series
These are specialized representations of Folder.

## Plugin Types

Plugins are able to register their own custom types as well. When this happens the plugin developer will publish information to help you customize your display for the new types. You can also ignore them and treat them generically.

The following are some known plugin types. Plugin developers are free to add theirs to this wiki page, along with links to their documentation.

### ConsoleFolder, Game
These types are added by [GameBrowser](https://github.com/RedshirtMB/gamebrowser-mb3) to represent a game system folder, and a Game, respectively.