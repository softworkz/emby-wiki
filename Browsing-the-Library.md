This page will detail how to retrieve items for display and browsing purposes.

## Displaying a Folder
After authentication, the next step is generally to start displaying the user's library.

## User Views

User views represent the user's top level categories, and can be retrieved from:

* /Users/{UserId}/Views

The items from a view can then be retrieved generically using:

* /Users/{UserId}/Items?parentId={ViewId}

All views support this style of generic navigation. Each item will have several properties to determine how to display it, e.g. **IsFolder**, **MediaType** and **Type**.

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

## Query-based views
If you would like to present virtual views based on queries, the api will allow you to do that. Use the Recursive=true param to search recursively. Here are a few examples:

### Display resumeable items, limit to 20 results and sort by date played
> http://localhost:8096/mediabrowser/Users/e8837bc1ad67520e8cd2f629e3155721/Items?Limit=20&Recursive=true&SortBy=DatePlayed&SortOrder=Descending&Filters=IsResumable

### Display all Movies
> http://localhost:8096/mediabrowser/Users/e8837bc1ad67520e8cd2f629e3155721/Items?Recursive=true&IncludeItemTypes=Movie

### Display all Episodes
> http://localhost:8096/mediabrowser/Users/e8837bc1ad67520e8cd2f629e3155721/Items?Recursive=true&IncludeItemTypes=Episode