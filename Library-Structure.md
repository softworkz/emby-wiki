### Movies 
The recommended structure is to put each movie in it's own folder.
 
`
/Movies
   /Home Alone (1990)
      Home Alone.avi

   /The Dark Knight (2008)
      The Dark Side.mkv

`

It is also possible to store movies together in one folder.
/Movies
  Home Alone (1990).avi
  Casino Royale (2006).mkv
 
ISO's, Dvd's and Blu-ray rips
 
Examples:
/Movies /Home Alone (1990) 
   Home Alone.iso 
 
/The Dark Knight (2008)
   The Dark Side.img
 
/Movies /Home Alone (1990) 
   /VIDEO_TS
 
/The Dark Knight (2008)
   /BDMV
 
Multi-resolution movies
 
Multiple resolutions of the same content can be stored in a single movie folder.

/Movies
  /300
    /300 - 1080p.mkv
    /300 - 720p.mkv

Each version must begin with the folder name, followed by " - ". If this requirement is not met, they will be treated as separate videos. Alternatively they can be grouped together manually using the server's web interface.  

Multi-file and multi-disc movies
Multi-file and multi-disc movies are supported by the server and some client apps (MB Classic does not yet support multi-part items). The movie must have it's own folder containing all parts of the movie. Additionally, each video file or folder must be suffixed using one of the following conventions:
    cdX
    discX
    diskX
    dvdX
    partX
    ptX
Where X is the part number. Spaces are allowed before the number, for example, "part 7" is accepted. Here is a complete example of a multi-file movie:
/Movies /Home Alone (1990) 
   Home Alone - part1.mkv
   Home Alone - part2.mkv
   Home Alone - part3.mkv
 
Multi-disc movie:
/Movies /Home Alone (1990)
    /Home Alone Disc 1 
       /VIDEO_TS 
   /Home Alone Disc 2 
      /VIDEO_TS 
 
/Rocky (1976)
    /Rocky Disc 1
      /BDMV
   /Rocky Disc 2
      /BDMV 
 
Please note that at this time, each part will have to be played individually. Displayed metadata will be based on information from the first part, and the additional parts will be made playable through a menu.
 
Special Features
Special features for movies can be stored in a specials folder under movie folders. Nested folders are not supported.
 
/Movies
/Home Alone (1990)
   /Home Alone (1990).mkv
   /specials
      deleted-scenes.mkv 
 
3D Videos
Any video can be marked as 3D by placing one of the following tags within the filename:
[fsbs] - Full side by side
[ftab] - Full top and bottom
[hsbs] - Half side by side
[htab] - Half top and bottom
This will indicate the 3D format, which will be needed when streaming video and extracting images. The MB2 conventions of [3d] and [sbs3d] are still supported and will default to HSBS.
Alternatively this can be done by editing metadata within the server dashboard.