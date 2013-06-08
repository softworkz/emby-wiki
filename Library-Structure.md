There are three main library categories:

* Moves
* TV Series
* Music

## Movies

The **recommended** structure is to put each movie in it's own folder.

Example:

<pre>/Movies
   /Home Alone (1990)
      Home Alone.avi

   /The Dark Knight (2008)
      The Dark Side.mkv</pre>

It is also possible to store movies together in one folder.
<br/><br/>
Example:

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

<br>

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


For local trailers MB3 Server also support a trailer file in the same folder as the movie, with the filename being the same as the movie but ending in -trailer. For example:

_Home Alone-trailer.mp4_

<pre>/Movies
   /Home Alone (1990)
     /Home Alone.mkv
     /Home Alone-trailer.mp4</pre>





<br>

####backdrop (Theme Video)

You can add that sub-folder and put in it a collection of trailer or custom intro, in the movie folder title you like, then when you enter that movie title, it will play in  a window.

Example of it:

<pre>/Movies
   /Home Alone (1990)
     /VIDEO_TS
     /backdrop</pre>

<br>

####theme-music (Theme songs)

This nice addition, consider when you browsing you collection, and when you enter a title, music will start, to do that, you have to create the sub-folder ‘theme-music’ AND/OR theme.mp3 in the same folder as a movie, as example for both:

<pre>/Movies
   /Home Alone (1990)
     /VIDEO_TS
     /theme-music</pre>


<pre>/Movies
/Home Alone (1990)
     /Home Alone.mkv
     /theme.mp3</pre>

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
#### Using TAG for TV

_[tvdbid=xxx]_

You can as well use the tag _[tvdbid=xxx]_ for the movie folder name, if you find you are not getting the correct metadata for a title, example of this:

<pre>/TV Series
   /Seinfeld [tvdbid=79169]
     /Season 1
     /Season 2
     /Season 3</pre>

Simply go the site [TVDB](http://http://thetvdb.com/) site and search that title, then when you click on it, you will find the ID movie on your browser for [Seinfeld](http://http://thetvdb.com/?tab=series&id=79169)

<br>
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
* fanart.jpg, then you can add fanart-1.jpg as many as you like, fanart-2.jpg, fanart-3.jpg .. etc.
* background.jpg then you can add background-1.jpg as many as you like, background-2, background-3 .. etc.