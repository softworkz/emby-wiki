This info applies to both audio and video playback.

## Direct Play
If the client device is capable of playing the file without encoding, and if the device has direct access to the media over the network, it is recommended to bypass the server altogether and just play the file directly. This will spare the server's cpu and generally will result in the best possible performance. You should examine the MediaStreams property to help make this determination.

## Direct Play
If the client device is capable of playing the file without encoding, and if the device has direct access to the media over the network, it is recommended to bypass the server altogether and just play the file directly. This will spare the server's cpu and generally will result in the best possible performance. You should examine media info to help make this determination.

## Direct Streaming

If the client device is capable of playing the file without encoding, it is recommended to use the **Static=true** parameter. This will stream the file statically without any processing, sparing the server's cpu, and allowing for easier seeking during playback. You should examine media info to help make this determination.

With direct streaming, it is also recommended to use either a file extension that matches the original file, or use the alias with no extension.

## Stream Copy

If direct play and direct stream are not possible, the next best alternative is stream copy. This will avoid encoding and simply swap the video container. This is achieved by passing "copy" as the codec value for audio and/or video, e.g. AudioCodec=copy&VideoCodec=copy.

## Encoding
If none of these options apply, then the server's encoding features should be utilized.

## Seeking
Client-side seeking will not be available when transcoding. In order to seek you'll have to stop the stream and start a new one using the StartTimeTicks parameter. When direct streaming, the file will be served statically and client-side seeking will be possible.

Note that the server caches transcoding output if the process completes before playback is stopped. This will allow the output to be served statically the next time the item is played.