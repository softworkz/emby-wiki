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

Here are some other properties that require a little more information:

### IsFolder, MediaType, Type
These allow you to determine how to categorize and display items. See [Browsing the Library](https://github.com/MediaBrowser/MediaBrowser/wiki/Browsing-the-Library)

### DisplayMediaType
This is a friendly version of MediaType that can be used for display purposes, if desired.

### AirDays, AirTime, Status
These are applicable Series only and will give you information about when episodes air.

### Album, AlbumArtist, Artist
These are applicable to audio files only.

### MediaStreams
This is applicable to Audio and Video only. This will provide detailed information about the audio, video and subtitle tracks embedded within the file.

### VideoType
This is applicable to Videos only. This will give you the type of video - VideoFile, Bluray, Dvd, HdDvd, Iso.

### SeriesId, SeriesName
These properties are applicable only to Episodes and Seasons. This will give you some basic information about the TV Series.

### OfficialRating
G, PG-13, R, TV-MA, etc.

### Path
This is the file system path of the item. This will generally not be needed by clients unless they're supporting direct play.

### IndexNumber
This serves different purposes depending on the type of item. For episodes this is the episode number. For seasons, this is the season number. For audio files, this is the track number.

### ParentIndexNumber
Similiar to IndexNumber, this serves different purposes depending on the type of item. For episodes this is the season number. For audio files, this is the disc number.

### PremiereDate 
This serves different purposes depending on the type of item. For episodes this is the air date. For series, this is the first air date. For audio files, this is the premiere date.

### AspectRatio
This is generally the original aspect ratio that the video was filmed in. The actual aspect ratio of the user's video can be found in the MediaStreams property.

### ProviderIds
This is a dictionary of provider id's for an item - Tmdb, Tvdb, TvCom, etc.

### CommunityRating
This is the Imdb, Tmdb, or Tvdb rating of the item. At this time we do not have the ability to identify the source.

### LocalTrailerCount, TrailerUrls
LocalTrailerCount is the number of downloaded local trailers that are available for an item. The actual trailer items can be retrieved separately using /Users/{UserId}/Items/{Id}/LocalTrailers.

TrailerUrls are a list of known online trailers. When supporting trailers, precedence should be given to downloaded trailers. It is up the client developer as to whether or not they just want to pick one, or present all of them in a list. The most common scenario is that the user will have just one local trailer.


* PrimaryImageAspectRatio
* UserData
* People