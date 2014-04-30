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
* VideoType (VideoFile, Dvd, etc)

The following is the algorithm to determine the optimal MediaSource:

## Direct Play
If the client device is capable of playing the file without encoding, and if the device has direct access to the media over the network, it is recommended to bypass the server altogether and just play the file directly. This will spare the server's cpu and generally will result in the best possible performance. You should examine media info to help make this determination.

## Direct Streaming

If the client device is capable of playing the file without encoding, it is recommended to use the **Static=true** parameter. This will stream the file statically without any processing, sparing the server's cpu, and allowing for easier seeking during playback. You should examine media info to help make this determination.

With direct streaming, it is also recommended to use either a file extension that matches the original file, or use the alias with no extension.

## Encoding
If none of these options apply, then the server's encoding features should be utilized. Please see the encoding articles for details.

## Seeking
Client-side seeking will not be available when transcoding. In order to seek you'll have to stop the stream and start a new one using the StartTimeTicks parameter. When direct streaming, the file will be served statically and client-side seeking will be possible.

Note that the server caches transcoding output if the process completes before playback is stopped. This will allow the output to be served statically the next time the item is played.