The base audio url is /Audio/{Id}/stream. Some players will have better results when the url has an audio file extension, so we also provide several aliases to account for that:

* /Audio/{Id}/stream
* /Audio/{Id}/stream.mp3
* /Audio/{Id}/stream.aac
* /Audio/{Id}/stream.ogg
* /Audio/{Id}/stream.wma
* /Audio/{Id}/stream.flac

Generally, it is recommend to use a url with a file extension that matches the format you wish to encode to.

Item **Id** is the only required parameter. 

All of the optional parameters can be viewed using the swagger documentation. If you are using a url without a file extension, then you must supply AudioCodec, or you'll receive an error.

## More Information
[Streaming Guidelines](https://github.com/MediaBrowser/MediaBrowser/wiki/Streaming-Guidelines)