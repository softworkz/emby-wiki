The base video url is /Video/{Id}/stream. Some players will have better results when the url has a video file extension, so we also provide several aliases to account for that:

* /Videos/{Id}/stream
* /Videos/{Id}/stream.mp4
* /Videos/{Id}/stream.asf
* /Videos/{Id}/stream.ogv
* /Videos/{Id}/stream.ts
* /Videos/{Id}/stream.webm
* /Videos/{Id}/stream.wmv
* /Videos/{Id}/stream.mp4
* /Videos/{Id}/stream.m4v
* /Videos/{Id}/stream.mkv
* /Videos/{Id}/stream.mpeg
* /Videos/{Id}/stream.avi
* /Videos/{Id}/stream.m2ts

If using a url with an extension, the extension **should be based upon the output format**, rather than the input.

Generally, it is recommend to use a url with a file extension that matches the format you wish to encode to as many players will perform better seeing the file extension in the url.

The following parameters are required:

* Id
* MediaSourceId
* PlaySessionId - comes from the PlaybackInfo response as part of our MediaSource api. If you are not using the MediaSource api, then generate a random alpha-numeric string.

All of the optional parameters can be viewed using the swagger documentation. 

* AudioCodec
* AudioBitrate
* MaxAudioChannels
* AudioSampleRate
* VideoCodec
* VideoBitrate
* MaxWidth
* MaxHeight
* Profile (h264 profile)
* Level
* AudioStreamIndex
* SubtitleStreamIndex (if burning into the video)

## Direct Stream
To direct stream a video file, simply use the static=true parameter.

## Seeking
When direct streaming, the file will be served statically and client-side seeking will be possible. When transcoding, this will not be possible. In order to seek you'll have to stop the stream and start a new one using the StartTimeTicks parameter. 