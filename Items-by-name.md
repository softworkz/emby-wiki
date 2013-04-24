In addition to library items, there are other related items that can be retrieved by name. These are:

* Genre
* Person
* Studio
* Artist

These can be retrieved individually on a per-name basis, e.g.

`/Persons/{Name}`

This will return an item with identical structure to normal library items. From there images can be downloaded as necessary. See the built-in documentation for all the related endpoints and parameters.

## Querying for items by name

In addition to individual retrieval, there are querying endpoints that will return lists of these items. 

`/Artists`

`/Genres`

`/Persons`

`/Studios`

These can be retrieved from the entire library, or limited to a specific folder, or limited to specific item types. For example, the following query will return all movie genres within a user's library:

`/Genres?IncludeItemTypes=Movie&Recursive=true&userId=xxx`

As with media item querying, these endpoints also support **paging**, **filtering**, **sorting** and **configurable output fields**. See the build-in documentation for details.