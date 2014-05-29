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