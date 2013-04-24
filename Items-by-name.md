Media items will contain lists of related items, such as Artists, Genres, Persons and Studious. These related items are referred to as "items by name" and can be retrieved by their name. The endpoints are:

`/Artists/{Name}`

`/Genres/{Name}`

`/Persons/{Name}`

`/Studios/{Name}`

For example, you have an audio file with Akon as the artist. You want to allow the user to click on Akon and see artist information. To do this, use the following:

`/Artists/Akon?userId=xxx`

This will return an item with identical structure to normal library items. UserId is optional, and if included, will include user data such as like/dislike/favorite statuses. These item can also have images.

## Querying for items by name

In addition to individual retrieval, there are querying endpoints that will return lists of these items. 

`/Artists`

`/Genres`

`/Persons`

`/Studios`

These can be retrieved from the entire library, or limited to a specific folder, or limited to specific item types. For example, the following query will return all movie genres within a user's library:

`/Genres?IncludeItemTypes=Movie&Recursive=true&userId=xxx`

As with media item querying, these endpoints also support **paging**, **filtering**, **sorting** and **configurable output fields**. See the build-in documentation for details.

## Images

The image endpoint locations are different, but function identically:

* /Artists/{Name}/Images/{Type}
* /Artists/{Name}/Images/{Type}/{Index}
* /Genres/{Name}/Images/{Type}
* /Genres/{Name}/Images/{Type}/{Index}
* /Persons/{Name}/Images/{Type}
* /Persons/{Name}/Images/{Type}/{Index}
* /Studios/{Name}/Images/{Type}
* /Studios/{Name}/Images/{Type}/{Index}