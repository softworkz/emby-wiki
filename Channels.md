Channels provide a way to add content from the internet into a user's library.

A list of available channels for a user can be downloaded using **/Channels?userId=xxxx**.

## Channel Features

Use **/Channels/{Id}/Features** to download an object describing the channel's capabilities. This object contains the following:

* CanSearch (not yet utilized)
* MediaTypes (Audio, Photo, Video)
* ContentTypes (Clip, Podcast, Trailer, Movie, Episode, Song)
* MaxPageSize (The maximum number of records that can be requested at a time)
* DefaultSortFields (Default available sort orders - Name, CommunityRating, PremiereDate, DateCreated, Runtime, PlayCount, CommunityPlayCount)
* SupportsSortOrderToggle (Indicates if ascending/descending orders are supported).
* CanFilter - Indicates if channel content can be filtered

## Channel Items

Channel content is returned using a hierarchical structure. Top level channel content can be retrieved using **/Channels/{Id}/Items?userId=xxx**.

From there, each sub-item can be examined using the **IsFolder** and **MediaType** properties.

If the item is a folder, it's content can be retrieved using **/Channels/{Id}/Items?userId=xxx&folderId=xxx**.

If the item is media, it's MediaType will be either Audio, Photo or Video.

## Images and Playback

Channels use the same type of object structure as normal library items. As a result, images and media playback can be handled using the same routines you've already written.

## Search

Coming soon.