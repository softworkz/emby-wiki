## Direct Streaming

If the client device is capable of playing the file without encoding, it is recommended to use the **Static=true** parameter. This will stream the file statically without any processing, sparing the server's cpu, and allowing for easier seeking during playback. You should examine the MediaStreams property to make this determination.

With direct streaming, it is also recommended to use either a file extension that matches the original file, or use the alias with no extension.