The base video url is /Video/{Id}/stream. Some players will have better results when the url has a video file extension, so we also provide several aliases to account for that:

* /Videos/{Id}/stream
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

Generally, it is recommend to use a url with a file extension that matches the format you wish to encode to.

Item Id is the only required parameter.

All of the optional parameters can be viewed using the swagger documentation. If you are using a url without a file extension, then you must supply both VideoCodec, and AudioCodec or you'll receive an error.

## Formats
Unlike audio, some of these formats have limitations that prevent them from being practical for encoding. If you are encoding, you **must** choose one of these aliases:

* /Videos/{Id}/stream
* /Videos/{Id}/stream.asf
* /Videos/{Id}/stream.ogv
* /Videos/{Id}/stream.ts
* /Videos/{Id}/stream.webm

Even though the server is capable of encoding to all of the formats listed at the beginning, most clients are not able to play them until the transcoding completes. In order to solve this, **you must choose asf, ogv, ts, or webm**. Ts should generally be the starting point, as that will provide H264.

When direct streaming this limitation does not apply.

## More Information
[Playback Guidelines](https://github.com/MediaBrowser/MediaBrowser/wiki/Playback-Guidelines)