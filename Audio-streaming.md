The base audio url is /Audio/{Id}/stream. Some players will have better results when the url has an audio file extension, so we also provide several aliases to account for that:

* /Audio/{Id}/stream
* /Audio/{Id}/stream.mp3
* /Audio/{Id}/stream.aac
* /Audio/{Id}/stream.ogg
* /Audio/{Id}/stream.wma
* /Audio/{Id}/stream.flac

Generally, it is recommend to use a url with the file extension that matches the format you wish to encode to.

Item **Id** is the only required parameter. 

All of the optional parameters can be viewed using the swagger documentation. If you are using a url without a file extension, then you must supply AudioCodec, or you'll receive an error.

## Direct Streaming

If the client device is capable of playing the file without encoding, it is recommended to use the **Static=true** parameter. This will stream the file directly without any processing, sparing the server's cpu, and allowing for easier seeking.

With direct streaming, it is recommended to either use a url file extension that matches the original file, or has no extension.
