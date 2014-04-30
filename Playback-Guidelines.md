This info applies to both audio and video playback.

## MediaSources
The first step towards playing content is to examine the MediaSources property. The server allows multiple sources for a single content item. It is up to the client to choose the optimal source based on it's own requirements. 

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
Clients that never direct play may skip this step. Using the above information, determine the number of MediaSources that can be **direct played**.

* If none, proceed to step 2
* If one, play that source
* If multiple, present a selection screen

### Step 2: Direct Stream

Given the following criteria:
* User defined max bitrate (quality setting)

Find the first MediaSource that can the client is capable of direct streaming that falls within the bitrate setting. All MediaSource properties will need to be examined in order to make this determination based on client capabilities.

If any are found, play the first matching source. If none, proceed to step 3.

### Step 2: Transcoding

If transcoding is needed, the first step is to determine the optimal source.

**For Audio**: Simply take the first MediaSource

**For Video**: Choose the first MediaSource containing a VideoCodec the client natively understands (usually h264). This will make the transcoding process more efficient. If none are found, simply take the first MediaSource.

Once the MediaSource is chosen, it is time to proceed to the streaming phase. See the articles on Audio streaming, Video streaming and Http Live streaming.