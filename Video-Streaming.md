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