Begin live tv support by making a call to **/LiveTv/Info**. 

The IsEnabled property will tell you if Live Tv is installed and enabled on the server. The EnabledUsers property contains a list of user id's that have access to live tv.

### Channels

Query for tv channels using **/LiveTv/Channels**. The most interesting channel properties are:

* Name
* Number
* ChannelType
* CurrentProgram

Channel images use the same api endpoints as regular library items, e.g. **/Items/{Id}/Images/Primary**. Channels also can have user data allowing users to like or favorite them which will help influence suggested programs.

### Recording Groups

To display recordings by group, first get the list of groups using **/LiveTv/Recordings/Groups**. Each group has a Name, Id and RecordingCount.

### Recordings

Recordings can be queried using **/LiveTv/Recordings**. Some of the available query params are:

* ChannelId
* IsInProgress
* GroupId
* SeriesTimerId


### Recording Info

Most of the data attached to recordings is self-explanatory and will not be rehashed here. They are very similar to library items. Only the properties requiring explanation are listed below.

* Status, StatusName - The recording status. StatusName is a displayable value.
* CompletionPercentage - Only applicable if in progress.
* Path - The physical path to the recording file (if available). Some clients may prefer to play the file directly.
* MediaStreams - Only available for completed recordings.

## Name & EpisodeTitle
For programs, recordings and timers that are part of a series, **Name will always equal the series name**, while EpisodeTitle is the title of the episode. Please note that **EpisodeTitle will not always be available**.

## Recording Playback
Playback should be nearly identical to library items. Clients can use the Path property to play directly, if possible, and/or examine MediaStreams to determine the ideal streaming method.

## Timers
A timer represents a single scheduled recording in the future. Timers can be queried using **/LiveTv/Timers**. If desired they can be filtered based on **ChannelId** or **SeriesTimerId**. A single time can be retrieved by Id using **/LiveTv/Timers/{Id}**. 

To schedule a new timer, first make a call to **/LiveTv/Timers/Defaults**. This will return a default timer object. If the timer is based on a program, pass **ProgramId** on the query string. The default timer will be populated with default times and padding values based on configuration. To create or update a timer, POST to **/LiveTv/Timers** or **/LiveTv/Timers/{Id}**.