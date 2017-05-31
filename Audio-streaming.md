Emby has a single audio API endpoint that supports both direct play as well as transcoding. You specify your supported formats as part of the URL, and the server will decide between direct play and transcoding.

The following are the available params:

* UserId (required)
* DeviceId (required)
* api_key (required)
* MaxStreamingBitrate (required)
* Container = comma delimited list of supported audio containers
* MaxSampleRate = max supported audio sample rate, e.g. 48000
* PlaySessionId (required) this should be generated client-side and is intended to be a unique value per stream URL
* TranscodingProtocol = hls or omit this for progressive (see notes below).
* TranscodingContainer = hls audio transcoding supports ts, aac or mp3.
* AudioCodec = The audio codec to use when transcoding.
* EnableRedirection = true/false. Allow redirects to external stream URL's
* EnableRemoteMedia = true/false. If true, all external domains will be allowed. If false, only cloud synced domains will be allowed.

Below is a sample URL:

/Audio/{ItemId}/universal?UserId=xxx&DeviceId=xxx&MaxStreamingBitrate=140000000&Container=opus,mp3,aac,m4a,flac,webma,webm,wav,ogg,aac,mp3,mpa,wav,wma,mp2,ogg,oga,webma,ape,opus,flac,m4a&TranscodingContainer=ts&TranscodingProtocol=hls&AudioCodec=aac&MaxSampleRate=48000&PlaySessionId=1496213367201

## Notes On Transcoding

It is highly recommended that client players support HLS audio. HLS audio will guarantee that seeking is always client-side. Using progressive transcoding will result in much more complicated seeking.


### Legacy API

The base audio url is /Audio/{Id}/stream. Some players will have better results when the url has an audio file extension, so we also provide several aliases to account for that:

* /Audio/{Id}/stream
* /Audio/{Id}/stream.mp3
* /Audio/{Id}/stream.aac
* /Audio/{Id}/stream.ogg
* /Audio/{Id}/stream.oga
* /Audio/{Id}/stream.webma
* /Audio/{Id}/stream.wma
* /Audio/{Id}/stream.flac

If using a url with an extension, the extension **should be based upon the output format**, rather than the input.

Generally, it is recommend to use a url with a file extension that matches the format you wish to encode to as many players will perform better seeing the file extension in the url.

Item **Id** and **MediaSourceId** are the only required parameters.

All of the optional parameters can be viewed using the swagger documentation. Generally, you will also want to supply:

* AudioCodec
* AudioBitrate
* MaxAudioChannels
* AudioSampleRate

## Direct Stream
To direct stream an audio file, simply use the static=true parameter.

## Seeking
When direct streaming, the file will be served statically and client-side seeking will be possible. When transcoding, this will not be possible. In order to seek you'll have to stop the stream and start a new one using the StartTimeTicks parameter. 