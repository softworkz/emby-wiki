This info applies to both audio and video playback.

## Direct Play
If the client device is capable of playing the file without encoding, and if the device has direct access to the media over the network, it is recommended to bypass the server altogether and just play the file directly. This will spare the server's cpu and generally will result in the best possible performance. You should examine the MediaStreams property to help make this determination.

## Direct Streaming

If the client device is capable of playing the file without encoding, it is recommended to use the **Static=true** parameter. This will stream the file statically without any processing, sparing the server's cpu, and allowing for easier seeking during playback. You should examine the MediaStreams property to help make this determination.

With direct streaming, it is also recommended to use either a file extension that matches the original file, or use the alias with no extension.

## Encoding
If none of these options apply, then the server's encoding features should be utilized.