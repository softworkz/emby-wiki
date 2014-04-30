Media Browser has a number of core library item types. The type can be determined by examining the Type property of a Dto. Api consumers can detect these types to customize their displays and/or query for these types individually to create virtual views.

The following core types are available:

### Audio
This is an audio file.

### Video
This is a generic video file.

### Folder
This is a generic folder.

### Episode, Movie, Trailer, AdultVideo, MusicVideo
These are specialized representations of Video.

### BoxSet, MusicAlbum, MusicArtist, Season, Series
These are specialized representations of Folder.

### Game,GameSystem
Game is a media item and GameSystem is folder containing games.

### Book
A media item that represents a book.

## Type Detection
Try to avoid this as much as possible and instead look at the properties of the item to determine your courses of action. This will allow your code to continue to function as new types are added.

Basic media types are Audio, Video, Game, Book and Photo. Checking item.MediaType is preferred over item.Type when basic media information is all that's needed.