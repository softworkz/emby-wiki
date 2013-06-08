There are three main library categories:

* Moves
* TV Series
* Music

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
         /deleted-scenes.mkv
</pre>

####Trailers

Trailers can be stored in a trailers folder under **movie or box set** folders.

<pre>/Movies
   /Home Alone (1990)
     /Home Alone (1990).mkv
     /trailers
         /trailer.mkv
</pre>

Alternatively, trailers can also be stored alongside the main movie using the -trailer suffix.

<pre>/Movies
   /Home Alone (1990)
     /Home Alone.mkv
     /Home Alone-trailer.mp4
</pre>

## TV Library

The recommended folder structure is series/season/episode.

<pre>/TV Series
   /Seinfeld
     /Season 1
       /S01E01 Seinfeld The Seinfeld Chronicles.mkv
       /S01E02 Seinfeld The Stake Out.mkv

     /Season 2
       /S02E05 Seinfeld The Apartment.mkv
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

## Music Library


Best to really ID3 tags your collection for best result, the supported structure normally is:

<pre>\Music
   \Artist Name
      \Album Name
         \Songs files</pre>


<pre>\Music
   \ABBA
      \Super Trouper
         \Lay All Your Love On Me.mp3</pre>


<br>
If you like, you can organized your collection as simple as:

<pre>\Music
   \Artist Name
      \Songs files</pre>

<pre>\Music
   \ABBA
      \Lay All Your Love On Me.mp3
      \The Winner Takes It All.mp3</pre>

_For the above to work right (Artist folder name, then all his songs collections in it) you must fully ID3 tags your songs files._

<br>

<br>


## Artwork - Fan art

#### For Primary Image names (poster, cover):

* folder.jpg/png
* poster.jpg/png
* cover.jpg/png
* default.jpg/png


#### For Backdrops names:

* backdrop.jpg, then you can add as many as you like, backdrop1.jpg, backdrop2.jpg .. etc.
* fanart.jpg, then you can add fanart-1.jpg as many as you like, fanart-2.jpg, fanart-3.jpg .. etc.
* background.jpg then you can add background-1.jpg as many as you like, background-2, background-3 .. etc.