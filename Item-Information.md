Library items have a number of interesting properties. Among these are, but not limited to:

* Name
* Id
* DateCreated
* Overview
* Taglines
* Genres
* RunTimeTicks
* ProductionYear
* Language
* ParentId
* Studios
* HoemPageUrl

When retrieving a single item, the entire object is returned. When querying for items, the return data will be stripped to include only a minimal amount of information. When querying, you can configure the fields that are returned in the output. See [browsing the Library.](https://github.com/MediaBrowser/MediaBrowser/wiki/Browsing-the-Library)

Here are some other properties along with their descriptions:

### AirDays, AirTime, Status
These are applicable to Series only and will give you information about when episodes air.

### Album, AlbumArtist, Artist
These are applicable to audio files only.

### AspectRatio
This is generally the original aspect ratio that the video was filmed in. The actual aspect ratio of the user's video can be found in the MediaStreams property.

### BackdropImageTags
This will tell you how many backdrop images are available for an item. See [images.](https://github.com/MediaBrowser/MediaBrowser/wiki/Images)

### Chapters
This is applicable to videos only. This will give you the list of chapter markers contained within the video.

### ChildCount
For folders, this indicates the number of child items available.

### CommunityRating
This is the Imdb, Tmdb, or Tvdb rating of the item. At this time we do not have the ability to identify the source.

### DisplayMediaType
This is a friendly version of MediaType that can be used for display purposes, if desired.

### EndDate
This is the date an item ended. Currently only used for people to represent death day.

### ImageTags
This will tell you what images are available for an item. See [images.](https://github.com/MediaBrowser/MediaBrowser/wiki/Images)

### IndexNumber
This serves different purposes depending on the type of item. For episodes this is the episode number. For seasons, this is the season number. For audio files, this is the track number.

### IsFolder, MediaType, Type
These allow you to determine how to categorize and display items. See [Browsing the Library](https://github.com/MediaBrowser/MediaBrowser/wiki/Browsing-the-Library)

### IsoType
This setting is applicable to videos only. If a video is an Iso this will give you the type - Dvd or BluRay.

### Locations
This contains any locations associated with the item.

### LocalTrailerCount, TrailerUrls
LocalTrailerCount is the number of downloaded local trailers that are available for an item. The actual trailer items can be retrieved separately using /Users/{UserId}/Items/{Id}/LocalTrailers.

TrailerUrls are a list of known online trailers. When supporting trailers, precedence should be given to downloaded trailers. It is up the client developer as to whether or not they just want to pick one, or present all of them in a list. The most common scenario is that the user will have just one local trailer.

### LocationType
This indicates if the item is a file system item, remote, or virtual.

### MediaStreams
This is applicable to Audio and Video only. This will provide detailed information about the audio, video and subtitle tracks embedded within the file.

### OfficialRating
G, PG-13, R, TV-MA, etc.

### OverviewHtml
An html version of the overview, possibly with links embedded.

### ParentIndexNumber
Similiar to IndexNumber, this serves different purposes depending on the type of item. For episodes this is the season number. For audio files, this is the disc number.

### ParentLogoItemId, ParentLogoImageTag, ParentBackdropItemId, ParentBackdropImageTags 
See [images.](https://github.com/MediaBrowser/MediaBrowser/wiki/Images)

### Path
This is the file system path of the item. This will generally not be needed by clients unless they're supporting direct play.

### People
These are the people involved in the item. Each person has Name, Role, Type and PrimaryImageTag properties. 

### PlayedPercentage
This is populated for folders to indicate the user's cumulative progress through all items in the folder.

### PremiereDate 
This serves different purposes depending on the type of item. For episodes this is the air date. For series, this is the first air date. For audio files, this is the premiere date.

### PrimaryImageAspectRatio
This is the aspect ratio of the primary image. Most image types have a predictable aspect ratio, but primary is the one exception. A typical use case when rendering a list of items is to determine the average AR, and then display them all using that value. See [images.](https://github.com/MediaBrowser/MediaBrowser/wiki/Images)

### ProviderIds
This is a dictionary of provider id's for an item - Tmdb, Tvdb, TvCom, etc.

### RecursiveItemCount
For folders, this indicates the number of items available, recursively.

### SeriesId, SeriesName
These properties are applicable only to Episodes and Seasons. This will give you some basic information about the TV Series.

### SpecialFeatureCount
This is applicable to Movies only. This will tell you how many special features are available. The actual special feature items can then be retrieved using /Users/{UserId}/Items/{Id}/SpecialFeatures.

### UserData
Contains user state for an item, such as personal rating and playstate.

### VideoFormat
This applicable to videos only. This will allow you to determine if a video is 3D. A value of Standard is 2D. Digital3D or Sbs3D represent 3D.

### VideoType
This is applicable to Videos only. This will give you the type of video - VideoFile, Bluray, Dvd, HdDvd, Iso.