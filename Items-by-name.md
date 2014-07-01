Media items will contain lists of related items, such as Artists, Genres, Persons and Studios. These related items are referred to as "items by name" and can be retrieved by their name. The endpoints to retrieve a **single item by name** are:

`/Artists/{Name}`

`/AlbumArtists/{Name}`

`/Genres/{Name}`

`/GameGenres/{Name}`

`/MusicGenres/{Name}`

`/Persons/{Name}`

`/Studios/{Name}`

**All '?' and '/' characters must be replaced by dashes '-'.**

For example, you have an audio file with Akon as the artist. You want to allow the user to click on Akon and see artist information. To do this, use the following:

`/Artists/Akon?userId=xxx`

This will return an item with identical structure to normal library items. UserId is optional, and if included, will include user data such as like/dislike/favorite statuses. These item can also have images.

## Images

Images can be retrieved in the same fashion as media items using the object Id's.

## Querying for items by name

In addition to individual retrieval, there are querying endpoints that will return lists of these items. 

`/Artists`

`/Artists/AlbumArtists`

`/GameGenres`

`/Genres`

`/MusicGenres`

`/Persons`

`/Studios`

These can be retrieved from the entire library, or limited to a specific folder, or limited to specific item types. For example, the following query will return all movie genres within a user's library:

`/Genres?IncludeItemTypes=Movie&Recursive=true&userId=xxx`

As with media item querying, these endpoints also support **paging**, **filtering**, **sorting** and **configurable output fields**. See the build-in documentation for details.

## Item Counts
Each artist, genre, studio, person, etc, will have the following additional properties available, to indicate how many items in the library they apply to:

* TotalCount
* AdultVideoCount
* MovieCount
* SeriesCount
* EpisodeCount
* GameCount
* TrailerCount
* SongCount
* AlbumCount
* MusicVideoCount
