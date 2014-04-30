The base audio url is /Audio/{Id}/stream. Some players will have better results when the url has an audio file extension, so we also provide several aliases to account for that:

* /Audio/{Id}/stream
* /Audio/{Id}/stream.mp3
* /Audio/{Id}/stream.aac
* /Audio/{Id}/stream.ogg
* /Audio/{Id}/stream.oga
* /Audio/{Id}/stream.webma
* /Audio/{Id}/stream.wma
* /Audio/{Id}/stream.flac

Generally, it is recommend to use a url with a file extension that matches the format you wish to encode to as many players will perform better seeing the file extension in the url.

Item **Id** and **MediaSourceId** are the only required parameters.

All of the optional parameters can be viewed using the swagger documentation. 

## Seeking
When direct streaming, the file will be served statically and client-side seeking will be possible. When transcoding, this will not be possible. In order to seek you'll have to stop the stream and start a new one using the StartTimeTicks parameter. 