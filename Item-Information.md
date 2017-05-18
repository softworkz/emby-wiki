Library items have a number of interesting properties. Among these are, but not limited to:

* Name
* Id
* Budget
* CriticRating
* CriticRatingSummary
* DateCreated
* GameSystem
* Genres
* GenreItems
* HomePageUrl
* IsHD
* Language
* Overview
* ParentId
* Path
* People
* Players
* ProductionYear
* Revenue
* RunTimeTicks
* SeasonCount
* SortName
* Studios
* Taglines
* Tags
* Type

When retrieving a single item, the entire object is returned. When querying for items, the return data will be stripped to include only a minimal amount of information. When querying, you can configure the fields that are returned in the output. See [browsing the Library.](Browsing-the-Library)

Here are some other properties along with their descriptions:

### AirDays, AirTime, Status
These are applicable to Series only and will give you information about when episodes air.

### Album, AlbumArtist, Artists, AlbumId, AlbumPrimaryImageTag
These are applicable to audio files and music albums only.

### AspectRatio
This is generally the original aspect ratio that the video was filmed in. The actual aspect ratio of the user's video can be found in the MediaStreams property.

### BackdropImageTags
This will tell you how many backdrop images are available for an item. See [images.](Images)

### Chapters
This is applicable to videos only. This will give you the list of chapter markers contained within the video.

### ChildCount
For folders, this indicates the number of child items available.

### CommunityRating
This is the Imdb, Tmdb, or Tvdb rating of the item. At this time we do not have the ability to identify the source.

### CumulativeRunTimeTicks
For folders, this represents the cumulative runtime.

### EndDate
This is the date an item ended. For Persons this represents death date. For series that have ended, this is the air date of the final episode.

### ImageTags
This will tell you what images are available for an item. See [images.](Images)

### IndexNumber
This serves different purposes depending on the type of item. For episodes this is the episode number. For seasons, this is the season number. For audio files, this is the track number.

### IndexNumberEnd
Denotes the ending index number, in case a file spans multiple episodes.

### IsFolder
This will tell you if the item is a media item, or if it's a folder containing other items. When navigating to an item, this will allow you to determine what type of display to present.

### MediaType
If an item is a media item, this will tell you what kind of media it is so that you can customize your display. The core has three known media types: Audio, Video, Game. Plugins may provide others.

### Type
This will tell you the exact object type of the item, in case you would like to customize further. For example, the Video media type has several implementations - Movie, Episode, Trailer, etc. Folder also has several - Series, Season, BoxSet, MusicArtist, MusicAlbum, etc.

### IsoType
This setting is applicable to videos only. If a video is an Iso this will give you the type - Dvd or BluRay.

### LocalTrailerCount, RemoteTrailers
LocalTrailerCount is the number of downloaded local trailers that are available for an item. The actual trailer items can be retrieved separately using /Users/{UserId}/Items/{Id}/LocalTrailers.

RemoteTrailers are a list of known online trailers. When supporting trailers, precedence should be given to downloaded trailers. It is up the client developer as to whether or not they just want to pick one, or present all of them in a list. The most common scenario is that the user will have just one local trailer.

### LocationType
This indicates if the item is a file system item, remote, or virtual.

FileSystem items are items the user has physical copies of on their file system. Remote items point to a url address. Virtual items entirely virtual and are not playable (e.g. missing episodes).

### MediaSources
Contains raw media information about the available media sources for this library item.

### MediaStreams
This is applicable to Audio and Video only. This will provide detailed information about the audio, video and subtitle tracks embedded within the file. **Note:** This has now been superseded by MediaSources. Going forward MediaStreams should only be used for display purposes.

### OfficialRating
G, PG-13, R, TV-MA, etc.

### OverviewHtml
An html version of the overview, possibly with links embedded.

### ParentIndexNumber
Similiar to IndexNumber, this serves different purposes depending on the type of item. For episodes this is the season number. For audio files, this is the disc number.

### ParentArtItemId, ParentArtImageTag, ParentLogoItemId, ParentLogoImageTag, ParentBackdropItemId, ParentBackdropImageTags 
See [images.](Images)

If an item does not have it's own art, backdrop or logo, these properties will contain information about parent items with those images in order to allow inheritance.

### PartCount
For multi-file videos this will indicate the number of parts.

### People
These are the people involved in the item. Each person has Name, Role, Type and PrimaryImageTag properties. 

### PlayedPercentage
This is populated for folders to indicate the user's cumulative progress through all items in the folder.

### PremiereDate 
This serves different purposes depending on the type of item. For episodes and series, this is the first air date. For movies, albums and songs, this is the release date. For persons this is date of birth. For artists, this is their formation date.

### OriginalPrimaryImageAspectRatio, PrimaryImageAspectRatio
This is the aspect ratio of the primary image. Most image types have a predictable aspect ratio, but primary is the one exception. A typical use case when rendering a list of items is to determine the average AR, and then display them all using that value. 

OriginalPrimaryImageAspectRatio ratio is the AR of the original image file. PrimaryImageAspectRatio is the AR after image enhancers have been applied (e.g. Cover Art).

See [images.](Images)

### ProductionLocations
This is a list of strings indicating filming locations. For Persons, this will have one entry and will contain their place of birth.

### ProviderIds
This is a dictionary of provider id's for an item - Tmdb, Tvdb, TvCom, etc.

A list of known provider id's can be found [here](https://github.com/MediaBrowser/MediaBrowser/blob/master/MediaBrowser.Model/Entities/MetadataProviders.cs), although plugins can inject additional ones.

### RecursiveItemCount
For folders, this indicates the number of items available, recursively.

### RecursiveUnplayedItemCount
For folders, this indicates the number of unplayed items available, recursively.

### SeriesId, SeriesName
These properties are applicable only to Episodes and Seasons. This will give you some basic information about the TV Series.

### SpecialFeatureCount
This is applicable to Movies and Series only. This will tell you how many special features are available. The actual special feature items can then be retrieved using /Users/{UserId}/Items/{Id}/SpecialFeatures.

### UserData
Contains user state for an item, such as personal rating and playstate.

### Video3DFormat
The 3D format, if applicable.

### VideoType
This is applicable to Videos only. This will give you the type of video - VideoFile, Bluray, Dvd, HdDvd, Iso.