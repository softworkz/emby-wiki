The base video url is /Video/{Id}/stream. Some players will have better results when the url has a video file extension, so we also provide several aliases to account for that:

* /Video/{Id}/stream
* /Video/{Id}/stream.asf
* /Video/{Id}/stream.ogv
* /Video/{Id}/stream.ts
* /Video/{Id}/stream.webm
* /Video/{Id}/stream.wmv
* /Video/{Id}/stream.mp4
* /Video/{Id}/stream.m4v
* /Video/{Id}/stream.mkv
* /Video/{Id}/stream.mpeg
* /Video/{Id}/stream.avi

Generally, it is recommend to use a url with a file extension that matches the format you wish to encode to.

Item Id is the only required parameter.

All of the optional parameters can be viewed using the swagger documentation. If you are using a url without a file extension, then you must supply both VideoCodec, and AudioCodec or you'll receive an error.

## Formats
Unlike audio, some of these formats have limitations that prevent them from being practical for encoding. If you are encoding, you **must** choose one of these aliases:

* /Video/{Id}/stream
* /Video/{Id}/stream.asf
* /Video/{Id}/stream.ogv
* /Video/{Id}/stream.ts
* /Video/{Id}/stream.webm

Even though the server is capable of encoding to all of the formats listed at the beginning, most clients are not able to play them until the transcoding completes. In order to solve this, **you must choose asf, ogv, ts, or webm**.

When direct streaming this limitation does not apply.

## More Information
[Streaming Guidelines](https://github.com/MediaBrowser/MediaBrowser/wiki/Streaming-Guidelines)