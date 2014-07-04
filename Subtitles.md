Text subtitles can be downloaded separately for an item using:

/Videos/{Id}/{MediaSourceId}/Subtitles/{Index}/Stream.srt
/Videos/{Id}/{MediaSourceId}/Subtitles/{Index}/Stream.vtt

Subtitle media streams have an **IsTextSubtitleStream** property. If this is true, they can be downloaded in any of the formats listed above.

If starting from an offset, simply supply the **StartPositionTicks** query string parameter.