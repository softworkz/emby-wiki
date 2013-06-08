Contents:

* Moves
* TV Series
* Music
* Images
* Subtitles
* Theme Songs
* Theme Videos

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

#### ISO's and folder rips

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

#### Box Sets

Movies can be grouped together into box sets.

<pre>/Movies
   /Lord of the Rings[boxset]
      /The Lord of the Rings - The Fellowship of The Ring
      /The Lord of the Rings - The Two Towers
      /The Lord of the Rings - The Return of The King
</pre>

####Special Features

Special features for movies can be stored in a specials folder under movie folders.

<pre>/Movies
   /Home Alone (1990)
     /Home Alone (1990).mkv
     /specials
         deleted-scenes.mkv
</pre>

####Trailers

Trailers can be stored in a trailers folder under **movie or box set** folders.

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

## TV Series

The **recommended** folder structure is series/season/episode.

<pre>/TV Series
   /Seinfeld
     /Season 1
       S01E01 Seinfeld The Seinfeld Chronicles.mkv
       S01E02 Seinfeld The Stake Out.mkv

     /Season 2
       S02E05 Seinfeld The Apartment.mkv
</pre>

#### Episode file naming
Some of the supported naming conventions for episode files are:

* 01x02x03 show name.avi 
* S01x01x03 show name.avi
* S01E02E03 show name.avi
* S01xE01xE02 show name.avi
* 01x02x03 show name.avi 
* S01x01X03 show name.avi
* 01x02 01x03 show name.avi 
* 01x02 - 01x03 show name.avi 
* S01x02.S01x03 show name.avi 
* S01x02 - S01x03 show name.avi
* S01E02-E03 show name.avi
* S01xE01xE02 show name.avi

#### Multi-episode files
Multi-episode files are supporting using the following naming conventions:

* Seinfeld s01e01-e02.avi
* Seinfeld 1x01-x02.avi

## Music 

The recommended folder structure for music is Artist\Album\Song

<pre>\Music
   \Artist Name
      \Album Name
         1- Song.mp3
         2- Song.mp3
</pre>

Any naming convention for audio files is acceptable. Track numbers are retrieved using ID3 tags.

## Images

The following image files can be stored within folders of any type.

#### Primary Image

* folder.jpg/jpeg/png
* poster.jpg/jpeg/png
* cover.jpg/jpeg/png
* default.jpg/jpeg/png

#### Backdrops:

* backdrop.jpg/jpeg/png, backdrop1.jpg/jpeg/png, backdrop2.jpg/jpeg/png, etc
* fanart.jpg/jpeg/png, fanart-1.jpg/jpeg/png, fanart-2.jpg/jpeg/png, etc
* background.jpg/jpeg/png, background-1.jpg/jpeg/png, background-2.jpg/jpeg/png, etc

#### Banner
* banner.jpg/jpeg/png

#### Box
* box.jpg/jpeg/png

#### Box Rear
* boxrear.jpg/jpeg/png

#### Clear Art
* art.jpg/jpeg/png

#### Logo
* logo.jpg/jpeg/png

#### Menu
* menu.jpg/jpeg/png

#### Thumb
* thumb.jpg/jpeg/png

#### Screenshots:

* screenshot.jpg/jpeg/png, screenshot1.jpg/jpeg/png, screenshot2.jpg/jpeg/png, etc

## Subtitles

All video files can have external srt subtitles. The filename must match the video filename, or be suffixed with a language.

<pre>/Movies
   /Home Alone (1990)
      Home Alone.mkv
      Home Alone.srt
      Home Alone.spa.srt
      Home Alone.spanish.srt
</pre>

Languages can be specified either using the **three character ISO code**, which is preferred, or the full english name.