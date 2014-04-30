This info applies to both audio and video playback.

## MediaSources
The first step towards playing content is to examine the MediaSources property. The server allows multiple sources for a single content item, so it is up to the client to choose the optimal source. 

Each MediaSource has the following properties that can be examined:

* Bitrate (represents the total file bitrate)
* Container (mkv, mp4, etc)
* LocationType (FileSystem, Remote, etc)
* MediaStreams
* Path
* Size (in bytes)
* VideoType (VideoFile, Dvd, Iso, Bluray)

Before we discuss the algorithm to examine MediaSources, let us first define a few terms:

**Direct Play** - The client plays the file by accessing the file system directly using the Path property. The server is bypassed with this mechanism. Whenever possible this is the most desirable form of playback.

**Direct Stream** - The client streams the file from the server **as-is**, in it's original format, without any encoding or remuxing applied. Aside from Direct Play, this is the next most desirable playback method.

**Transcode** - The client streams the file from the server with encoding applied in order to convert it to a format that it can understand.


## MediaSource choice:
The following is the algorithm to determine the optimal MediaSource:

### Step 1: Direct Play
Using the above information, determine the number of MediaSources that can be **direct played**.
* If none, proceed to step 2
* If one, play that source
* If multiple, present a selection screen

### Step 2: Direct Stream
Using the above information, determine the number of MediaSources that can be **direct played**.
* If none, proceed to step 2
* If one, play that source
* If multiple, present a selection screen

## Seeking
Client-side seeking will not be available when transcoding. In order to seek you'll have to stop the stream and start a new one using the StartTimeTicks parameter. When direct streaming, the file will be served statically and client-side seeking will be possible.