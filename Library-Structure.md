Contents:

* Movies
* TV Series
* Music
* Images
* Subtitles
* Trailers
* Theme Songs
* Theme Videos
* Excluding folders
* Shortcut files

## Movies

The **recommended** structure is to put each movie in it's own folder. 

<pre>/Movies
   /Home Alone (1990)
      Home Alone.avi

   /The Dark Knight (2008)
      The Dark Side.mkv</pre>

It is also possible to store movies together in one folder. 

<pre>/Movies
    Home Alone (1990).avi
    Casino Royale (2006).mkv
</pre>

#### ISO's, Dvd's and Blu-ray rips

Examples:

<pre>/Movies
   /Home Alone (1990)
      Home Alone.iso

   /The Dark Knight (2008)
      The Dark Side.img
</pre>


<pre>/Movies
   /Home Alone (1990)
     /VIDEO_TS

   /The Dark Knight (2008)
     /BDMV
</pre>

#### Multi-file and multi-disc movies

Multi-file and multi-disc movies are supported. The movie must have it's own folder containing all parts of the movie. Additionally, each video file or folder must be suffixed using one of the following conventions:

* cdX
* discX
* diskX
* dvdX
* partX
* ptX

Where X is the part number. Spaces are allowed before the number, for example, "part 7" is accepted. Here is a complete example of a multi-file movie:

<pre>
/Movies
   /Home Alone (1990)
      Home Alone - part1.mkv
      Home Alone - part2.mkv
      Home Alone - part3.mkv

</pre>

Multi-disc movie:
<pre>
/Movies
   /Home Alone (1990)
      /Home Alone Disc 1
          /VIDEO_TS
      /Home Alone Disc 2
          /VIDEO_TS

   /Rocky (1976)
      /Rocky Disc 1
          /BDMV
      /Rocky Disc 2
          /BDMV

</pre>

Please note that at this time, each part will have to be played individually. Displayed metadata will be based on information from the first part, and the additional parts will be made playable through a menu.


#### Box Sets

Movies can be grouped together into box sets.

<pre>/Movies
   /Lord of the Rings[boxset]
      /The Lord of the Rings - The Fellowship of The Ring
      /The Lord of the Rings - The Two Towers
      /The Lord of the Rings - The Return of The King
</pre>

In order to be detected as a boxset, the folder must have [boxset] within the name, or a collection.xml metadata file within it.

In addition to movies within the boxset folder, movies can also be added from elsewhere in the library using shortcut files (.lnk). Simply place a shortcut file that points to the movie folder within the boxset folder. **The path being pointed to from the shortcut must also exist in the library, using exactly the same path**. It is simply a link to a pre-existing library item.

**Shortcut example**:

<pre>
/Movies
   /Home Alone (1990)
     /Home Alone (1990).mkv

/Boxsets
   /Home Alone Collection [boxset]
     /homealone.lnk (points to /Home Alone (1990) folder)
</pre>

If Home Alone was added to the library as \\my-server\movies\Home Alone (1990), then **the path contained in the shortcut must point to** \\my-server\movies\Home Alone (1990), and not D:\Movies\Home Alone (1990)

####Special Features

Special features for movies can be stored in a specials folder under movie folders. **Nested folders are not supported**.

<pre>/Movies
   /Home Alone (1990)
     /Home Alone (1990).mkv
     /specials
         deleted-scenes.mkv
</pre>

####3D Videos

Any video can be marked as 3D by placing one of the following tags within the filename:

* [fsbs] - Full side by side
* [ftab] - Full top and bottom
* [hsbs] - Half side by side
* [htab] - Half top and bottom

This will indicate the 3D format, which will be needed when streaming video and extracting images. The MB2 conventions of [3d] and [sbs3d] are still supported and will default to HSBS.

Alternatively this can be done by editing metadata within the server dashboard.

## TV Series

The **recommended** folder structure is series/season/episode.

<pre>/TV Series
   /Seinfeld
     /Season 1
       S01E01 Seinfeld The Seinfeld Chronicles.mkv
       S01E02 Seinfeld The Stake Out.mkv

     /Season 2
       S02E05 Seinfeld The Apartment.mkv
       S02E06 Seinfeld Number Six.iso
</pre>

#### Episode file naming (Multi-episode supported)
Some of the supported naming conventions for episode files are:

* 01x02x03 episode name.avi 
* S01x02x03 episode name.avi
* S01E02E03 episode name.avi
* S01xE02xE03 episode name.avi
* S01E02-E03 episode name.avi
* S01E02-X03 episode name.avi
* 01x02 01x03 episode name.avi 
* 01x02 - 01x03 episode name.avi 
* 01x02 - x03 episode name.avi 
* S01x02.S01x03 episode name.avi 
* S01x02 - S01x03 episode name.avi
* show name 01x02x03 episode name.avi 
* show name S01x02x03 episode name.avi
* show name S01E02E03 episode name.avi
* show name S01xE02xE03 episode name.avi
* show name S01E02-E03 episode name.avi
* show name S01E02-X03 episode name.avi
* show name 01x02 01x03 episode name.avi 
* show name 01x02 - 01x03 episode name.avi 
* show name 01x02 - x03 episode name.avi 
* show name S01x02.S01x03 episode name.avi 
* show name S01x02 - S01x03 episode name.avi
* 01 episode name.avi 

_For all these examples the episode is detected as episode #2 and episode #3_

## Music 

The recommended folder structure for music is Artist\Album\Song

<pre>\Music
   \Artist Name
      \Album Name
         1- Song.mp3
         2- Song.mp3
</pre>

Any naming convention for audio files is acceptable. Track numbers are retrieved using ID3 tags.

## Music Videos
These are setup using a similar conventions as movies. When setting up the media collection, make sure to choose "Music Videos" as the type.

Once setup, you can optionally edit music videos and fill in their artist and album information. If you do, the music videos will appear on the artist's detail page.

Songs can be mixed together under one artist folder:

<pre>\Music Videos
   \Artist Name
      \Song Name
         artist-song.mp4
         artist-song1.mp4
</pre>

Or separated into their own song folders

<pre>\Music Videos
   \Artist Name
      \Song Name
         artist-song.mp4
</pre>

For images, both conventions utilize the same image file names as movies.

## Album soundtrack links
If you edit an album and fill a tmdb id, tvdb id, and/or gamesdb id, we'll be able to link soundtrack albums in your library to their corresponding movie, tv series or game. We'll then display this on the detail page for each item.

## Images

The following image files can be stored within folders of any type (movie, box set, series, season, etc). **All images support the jpg, jpeg, png and tbn extensions**.

#### Primary Image

* folder.ext
* poster.ext
* cover.ext
* default.ext
* movie.ext
* {moviename}-poster.ext

TV Series (in addition to above):

* show.ext

TV Seasons (in addition to above):

* seasonXX-poster.ext (in series folder)
* season-specials-poster.ext (in series folder)

Episodes):

* {name}.ext (in metadata sub-folder)
* {name}-thumb.ext (in season folder)

#### Backdrops:

* backdrop.ext, backdrop1.ext, backdrop2.ext, etc
* fanart.ext, fanart-1.ext, fanart-2.ext, etc
* {movie}-fanart.ext
* background.ext, background-1.ext, background-2.ext, etc
* art.ext, art-1.ext, art-2.ext, etc
* image files stored in an "extrafanart" sub-folder

TV Seasons (in addition to above):

* seasonXX-fanart.ext (in series folder)
* season-specials-fanart.ext (in series folder)

#### Additional image types
* banner.ext
* box.ext
* boxrear.ext
* clearart.png
* disc.ext or cdart.ext
* logo.png (clear logo)
* menu.ext
* thumb.ext (16*9 thumbnail)
* screenshot.ext, screenshot1.ext, screenshot2.ext, etc

## Subtitles

All video files can have external srt subtitles. The filename must match the video filename, or be suffixed with a language.

<pre>/Movies
   /Home Alone (1990)
      Home Alone.mkv
      Home Alone.srt
      Home Alone.spa.srt
      Home Alone.spanish.srt
</pre>

Languages can be specified using either the **three character ISO code**, which is preferred, or the full english name.

##Trailers

Trailers can be stored in a trailers sub-folder under **movie, box set, series, season or game** folders.

<pre>/Movies
   /Home Alone (1990)
     /trailers
         trailer.mkv
     Home Alone (1990).mkv
</pre>

Alternatively, trailers can also be stored alongside the main movie using the -trailer suffix.

<pre>/Movies
   /Home Alone (1990)
     Home Alone.mkv
     Home Alone-trailer.mp4
</pre>

## Theme Songs

Any folder (movie, season, series, box set, game, etc) can have theme songs. There are two supported conventions, the 'theme-music' sub-folder, or theme.xxx, where xxx is any valid audio extension.

<pre>/Movies
   /Home Alone (1990)
      /theme-music
          song1.mp3
          song2.wma
          song3.flac
      theme.mp3
</pre>


## Theme Videos

Any folder (movie, season, series, box set, game, etc) can have theme videos using a 'backdrops' sub-folder. (Theme videos were originally called video backdrops)

<pre>/Movies
   /Home Alone (1990)
      /backdrops
          video1.mkv
          video1.mp4
</pre>

## Excluding Folders

To exclude a folder from Media Browser , simply mark it hidden, or place a file inside named .ignore.

##Don't Fetch MetaData For An Item

To stop Media Browser from attempting to fetch metadata for any particular item you can uncheck the check box "Enable internet metadata providers for this item." In the Metadata Settings for the item in the Metadata Manager.

## Shortcut Files

Custom folders can be created containing shortcut files to media already existing in the library. For example, you may have an "All Movies" folder, as well as a "Kids Movies" folder. By placing a shortcut file within kids movies, it is possible add links to movies already in the library.

**The path being pointed to from the shortcut must also exist in the library, using exactly the same path**. It is simply a link to a pre-existing library item.

**Shortcut example**:

<pre>
/All Movies
   /Home Alone (1990)
     /Home Alone (1990).mkv

/Kids Movies
   /homealone.lnk (points to /Home Alone (1990) folder)
</pre>

If Home Alone was added to the library as \\my-server\movies\Home Alone (1990), then **the path contained in the shortcut must point to** \\my-server\movies\Home Alone (1990), and not D:\Movies\Home Alone (1990)