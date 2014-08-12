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