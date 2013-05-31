## Organize your Library

It best to organized you media library in a way that MB3 Server will recognized them in the correct way.
Doing that will insure that the metadata and fan art's will be correct for your titles.

Let explain the 3 main library categories as:

* Moves
* TV Series
* Music

There are others castigators library media of course like Documentaries, Home video, Music Videos, and a like.
I will explain later on how to manage these library as well.

## Movie Library

You can put all your movies titles in one top folder as "Movies", then your titles to be:
_movies name (year).ext_.

Example:

<pre>/Movies
    Home Alone (1990).avi
    Casino Royale (2006).mkv
</pre>

<br>
But that not the best way to organized your movies titles, the **recommended structure**, that every titles have it _individual folders_.

Example:

<pre>/Movies
   /Home Alone (1990)
      Home Alone.avi

   /The Dark Knight (2008)
      The Dark Side.mkv
</pre>
<br>

#### Image format & Disc format

Also you can use _image format_ (ISO, IMG .. etc) and _disc format_ (dvd/bluray rips):

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

<br>

#### Using TAG for Movies

_[tmdbid=xxxx]_

You can as well use the tag _[tmdbid=xxxx]_ for the movie folder name, if you find you are not getting the correct metadata for a title, example of this:

<pre>/Movies
   /Home Alone (1990)[tmdbid=771]
      Home Alone.mkv
</pre>

Or

<pre>/Movies
   /Home Alone [tmdbid=771]
      Home Alone.mkv
</pre>

Simply go the site [IMDB](http://www.themoviedb.org/) site and search that title, then when you click on it, you will find the ID movie on your browser for [Home Alone](http://www.themoviedb.org/movie/771-home-alone)
<br>
<br>

_[DontFetchMeta]_

Another tag as _[DontFetchMeta]_ you can use that in the top folder as:

<pre>D:\Home Movie [DontFetchMeta]</pre>

Or to any individual titles as:

<pre>/Movies
   /Home Alone [dontfetchmeta]
      Home Alone.iso</pre>

The above tag will till MB3 server to not fetch any metadata for that titles or titles within the top folder, so either you can create your own custom metadata or edit it from the server dashboard index.



#### Using box sets collections


Simply create a name for the collection, as example _Lord of the Rings_ and the tag _[boxset]_ to it, then add your bpx sets titles for Lord of the Rings to it:

<pre>/Movies
   /Lord of the Rings[boxset]
      /The Lord of the Rings - The Fellowship of The Ring
      /The Lord of the Rings - The Two Towers
      /The Lord of the Rings - The Return of The King</pre>


![SetBox Collection](http://i661.photobucket.com/albums/uu339/abobader/MediaBrowser3-Abo/abogithubmb3s1_zps0f31d4cc.jpg)




####Using other sub-folders names supporting:

####Specials

You can put in that folder the extra that comes within your dvd/bluray contents, also if your movie within 2 parts, to put like part 2 on it for now.

####Trailers

For your custom trailers for a title for that movie.

Example for above as:

<pre>/Movies
   /Home Alone (1990)
     /VIDEO_TS
     /Trailers
     /Specials

   /The Dark Knight (2008)
     /Trailers</pre>


<br>
<br>


## TV Library

TV Series need to have _Season_ name in the sub-folder of the show, then in that sub-folder, as example _Season 1_ the episodes numbers, as example:

<pre>/TV Series
   /Seinfeld
     /Season 1
       /S01E01 Seinfeld The Seinfeld Chronicles.mkv
       /S01E02 Seinfeld The Stake Out.mkv

     /Season 2
       /S02E05 Seinfeld The Apartment.mkv</pre>


You can named the episodes numbering in many way, even if you have multiple episodes in one file, as:

* Seinfeld s01e01-e02.avi
* S01x02 - S01x03 Seinfeld.avi

Some of the supported numbering for episodes name are:

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

You can start with show name then episodes if you like, all supported.
Also you can use "-", ".", "x", and "X" to indicated the episodes numbers from the season number.

* Example for Seasons name: S01, 01 (is show as Season 1)
* Example for episodes numbers: 02, E02 (is show as Episode 2)

_So the above will be: Season 1 Episode number 2_

<br>

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
* fanart.jpg, then you can add fanart-1.jpg
* background.jpg then you can add background-1.jpg


