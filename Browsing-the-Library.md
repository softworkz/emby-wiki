This page will detail how to retrieve items for display and browsing purposes.

## Displaying a Folder
After authentication, the next step is generally to start displaying the user's library.

## User Views

User views represent the user's top level categories, and can be retrieved from:

* /Users/{UserId}/Views

The items from a view can then be retrieved generically using:

* /Users/{UserId}/Items?parentId={ViewId}

All views support this style of generic navigation. Each item will have several properties to determine how to display it, e.g. **IsFolder** (true/false), **MediaType** (Audio/Video/Photo/Book/Game) and **Type**.

See Item-Information

## Customized Presentations

While it's possible to display user views using generic navigation, often you'll want to customize based on the view type. Each view has a **CollectionType** property to indicate the view type. Available values are:

* movies
* tvshows
* music
* games
* books
* musicvideos
* homevideos
* livetv
* channels

If **CollectionType** is null, it indicates a mixed movie/tv folder that should be displayed generically.

A customized view can then be built by retrieving data pertaining to that view, e.g. latest movies, all movies, upcoming episodes, etc.

Displaying a customized view of live tv or channels will require use of the specific api's for those features.

## Sorting
Use the SortBy param to supply the fields to sort on. This supports multiple sort orders using a comma delimited list. Use SortOrder to specify ascending or descending order. The following example sorts by Artist, and then Album, in Ascending order:

> http://localhost:8096/emby/Users/e8837bc1ad67520e8cd2f629e3155721/Items?ParentId=20aef3be-ebda-f0d4-0096-8d179783e918&SortBy=Artist,Album&SortOrder=Ascending

Multiple sort orders are supported. For example, let's say you'd like to sort albums by release date descending, then by sort name ascending. Your params would look like:

> SortBy=ProductionYear,PremiereDate,SortName&SortOrder=Descending,Descending,Ascending

## Fields

When you request a single item using the /Users/{UserId}/Items/{Id} api, you will get back the entire item. When requesting lists of items, the data coming back will be much smaller in order to make it easier to retrieve large result sets.

If you want to add additional fields to the items, use the fields param, which is a comma-delimited list of fields to include in the output. See the swagger documentation for a full listing of available fields. Here is an example which adds SortName and PrimaryImageAspectRatio:

> http://localhost:8096/emby/Users/e8837bc1ad67520e8cd2f629e3155721/Items?ParentId=20aef3be-ebda-f0d4-0096-8d179783e918&Fields=PrimaryImageAspectRatio,SortName

## Query-based views
If you would like to present virtual views based on queries, the api will allow you to do that. Use the Recursive=true param to search recursively. Here are a few examples:

### Display resumeable items, limit to 20 results and sort by date played
> http://localhost:8096/emby/Users/e8837bc1ad67520e8cd2f629e3155721/Items?Limit=20&Recursive=true&SortBy=DatePlayed&SortOrder=Descending&Filters=IsResumable

### Display all Movies
> http://localhost:8096/emby/Users/e8837bc1ad67520e8cd2f629e3155721/Items?Recursive=true&IncludeItemTypes=Movie

### Display all Episodes
> http://localhost:8096/emby/Users/e8837bc1ad67520e8cd2f629e3155721/Items?Recursive=true&IncludeItemTypes=Episode