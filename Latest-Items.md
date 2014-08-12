Lists of latest items can be retrieved using

`/Users/{UserId}/Items/Latest`

It supports many of the usual querying parameters:

* StartIndex
* Limit
* Fields
* ParentId
* IsPlayed
* IncludeItemTypes

It also has an additional param, **GroupItems (default true)**. If true, items from the same container will be grouped into one and the container will be returned. The ChildCount property will be used to hold the group count.

## Example - Show latest movies

This will display the latest 20 unplayed movies:

`/Users/{UserId}/Items/Latest?IncludeItemTypes=Movie&Limit=20&IsPlayed=false`

## Example - Show latest episodes (with grouping)

This will display the latest 20 unplayed episodes:

`/Users/{UserId}/Items/Latest?IncludeItemTypes=Episode&Limit=20&IsPlayed=false&GroupItems=true`

The result will then be a list of Series groupings. Now suppose the user clicks a Series in order to see the 4 episodes behind the grouping. This is achieved via:

`/Users/{UserId}/Items/Latest?Limit=4&IsPlayed=false&GroupItems=false&ParentId={SeriesId}`