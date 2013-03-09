This page will detail how to retrieve items for display and browsing purposes.

There are three important properties which all library items have that will allow you to determine how to handle them:

### IsFolder
This will tell you if the item is a media item, or if it's a folder containing other items. When navigating to an item, this will allow you to determine what type of display to present.

### MediaType
If an item is a media item, this will tell you what kind of media it is so that you can customize your display. The core has three known media types: Audio, Video, Game. Plugins may provide others.

### Type
This will tell you the exact object type of the item, in case you would like to customize further. For example, the Video media type has several implementations - Movie, Episode, Trailer, etc. Folder also has several - Series, Season, BoxSet, MusicArtist, MusicAlbum, etc.