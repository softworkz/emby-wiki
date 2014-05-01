Media Browser supports the Http Live Streaming protocol, also known as HLS.

The url is:

* /Videos/{Id}/stream.m3u8

For a complete list or parameters, see the built-in documentation.

## Baseline Stream

To include a baseline, audio-only stream in the HLS master playlist, use the following parameters:

* AppendBaselineStream
* BaselineStreamAudioBitRate

For example, AppendBaselineStream=true&BaselineStreamAudioBitRate=64000