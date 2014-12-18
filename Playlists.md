### Creating Playlists

Send a POST to /Playlists?UserId=xxx&Name=xxx

There are two additional params, one of which must be specified:

* MediaType (Audio/Video)
* Ids - A comma delimited list of item id's to add to the playlist. MediaType can be omitted if this is supplied.

### Retrieving Playlists

Playlists for a user can be queried like any other type. The item type is Playlist.

The MediaType property of the playlist will indicate either Audio or Video.

### Playlist Items

There is a dedicated endpoint to retrieve the list of playlist items:

/Playlists/{Id}/Items

The following params are accepted:

* Id
* UserId
* StartIndex
* Limit
* Fields

Each playlist item will have a **PlaylistItemId** property. This property is required in order to remove the item from the playlist.

### Adding to Playlists

Send a POST to /Playlists/{Id}/Items

In addition, supply:

* Ids - A comma delimited list of item id's to add to the playlist.
* UserId

### Removing from Playlists

Send a DELETE to /Playlists/{Id}/Items

In addition, supply:

* EntryIds - A comma delimited list of the PlaylistItemId property of each item to remove from the playlist.