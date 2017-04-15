Emby supports the HTTP Live Streaming protocol, also known as HLS.

The url is:

* /Videos/{Id}/master.m3u8

The required paramaters are:

* Id (in path)
* MediaSourceId
* DeviceId

For a complete list of parameters, see the built-in documentation.

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

## Post Playback

After playback is complete, it is necessary to inform the server to stop any related HLS transcoding. This is accomplished via an HTTP DELETE to:

/Videos/ActiveEncodings?DeviceId=xxx

## External Documentation
* [HLS Documentation and Guides at Apple](https://developer.apple.com/streaming/)
* [IETF Internet Draft for HTTP Live Streaming](https://datatracker.ietf.org/doc/html/draft-pantos-http-live-streaming)