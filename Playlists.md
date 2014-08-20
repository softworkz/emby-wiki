### Creating Playlists

Send a POST to /Playlists?UserId=xxx&Name=xxx

There are two additional params, one of which must be specified:

* MediaType (Audio/Video)
* Ids - A comma delimited list of item id's to add to the playlist. MediaType can be omitted is this is supplied.

### Retrieving Playlists

Playlists for a user can be queried like any other type. The item type is Playlist.

The MediaType property of the playlist will indicate either Audio or Video.

### Playlist Items

Playlist items can be retrieved in the same manner as retrieving items of a Folder. A SortName should not be specified in order to preserve the playlis's original sorting.