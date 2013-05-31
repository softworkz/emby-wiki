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



####Using box sets collections


Simply create a name for the collection, as example _Lord of the Rings_ and the tag _[boxset]_ to it, then add your bpx sets titles for Lord of the Rings to it:

<pre>/Movies
   /Lord of the Rings[boxset]
      /The Lord of the Rings - The Fellowship of The Ring
      /The Lord of the Rings - The Two Towers
      /The Lord of the Rings - The Return of The King</pre>

<br>
![SetBox Collection](http://i661.photobucket.com/albums/uu339/abobader/MediaBrowser3-Abo/abogithubmb3s1_zps0f31d4cc.jpg)

<br>
<br>

####Using other sub-folders names supporting:

####Specials

You can put in that folder the extra that comes within your dvd/bluray contents, also if your movie within 2 parts, to put like part 2 on it for now.

####Trailers

For your custom trailers for a title for that movie.

