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
