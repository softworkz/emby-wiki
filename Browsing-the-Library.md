This page will detail how to retrieve items for display and browsing purposes.

## Displaying a Folder
After authentication, the next step is generally to display the contents of the user's root folder.

Displaying a folder generally requires two calls to the api. While not required, you'll usually want to start with a call to retrieve the folder itself, using one of the following:
* /Users/{UserId}/Items/Root
* /Users/{UserId}/Items/{Id}

This will give you some information on the folder itself, including the number of child items, as well as the number of recursive child items. 

The next step will be to construct a query to retrieve the children of the folder. At minimum you will need to supply the UserId and ParentId, which is the Id of the folder. Here is a sample url to do that:

> http://localhost:8096/mediabrowser/Users/e8837bc1ad67520e8cd2f629e3155721/Items?ParentId=20aef3be-ebda-f0d4-0096-8d179783e918

## Sorting
Use the SortBy param to supply the fields to sort on. This supports multiple sort orders using a comma delimited list. Use SortOrder to specify ascending or descending order. The following example sorts by Artist, and then Album, in Ascending order:

> http://localhost:8096/mediabrowser/Users/e8837bc1ad67520e8cd2f629e3155721/Items?ParentId=20aef3be-ebda-f0d4-0096-8d179783e918&SortBy=Artist,Album&SortOrder=Ascending

## Fields

When you request a single item using the /Users/{UserId}/Items/{Id} api, you will get back the entire item. When requesting lists of items, the data coming back will be much smaller in order to make it easier to retrieve large result sets.

If you want to add additional fields to the items, use the fields param, which is a comma-delimited list of fields to include in the output. See the swagger documentation for a full listing of available fields. Here is an example which adds SortName and PrimaryImageAspectRatio:

> http://localhost:8096/mediabrowser/Users/e8837bc1ad67520e8cd2f629e3155721/Items?ParentId=20aef3be-ebda-f0d4-0096-8d179783e918&Fields=PrimaryImageAspectRatio,SortName

## Identifying Items

There are three important properties which all library items have that will allow you to determine how to display them:

### IsFolder
This will tell you if the item is a media item, or if it's a folder containing other items. When navigating to an item, this will allow you to determine what type of display to present.

### MediaType
If an item is a media item, this will tell you what kind of media it is so that you can customize your display. The core has three known media types: Audio, Video, Game. Plugins may provide others.

### Type
This will tell you the exact object type of the item, in case you would like to customize further. For example, the Video media type has several implementations - Movie, Episode, Trailer, etc. Folder also has several - Series, Season, BoxSet, MusicArtist, MusicAlbum, etc.