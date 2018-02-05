This document will cover the core concepts of the Live Tv api but will not rehash each individual parameter. Developers should read this documentation along with testing it out in Swagger. 

Begin live tv support by making a call to **/LiveTv/Info**. 

The IsEnabled property will tell you if Live Tv is installed and enabled on the server. The EnabledUsers property contains a list of user id's that have access to live tv.

## Channels

Query for tv channels using **/LiveTv/Channels**. The most interesting channel properties are:

* Name
* Number
* ChannelType
* CurrentProgram (must be specified via optional field)

Additionally, channels share many of the same properties that are documented in [Item Information](Item-Information)

Channel images use the same api endpoints as regular library items, e.g. **/Items/{Id}/Images/Primary**. Channels also can have user data allowing users to like or favorite them which will help influence suggested programs.

## Programs (EPG data)

Query for programs using **/LiveTv/Programs**. The most interesting program properties are:

* Name
* EpisodeTitle
* OfficialRating
* RunTimeTicks
* StartDate
* EndDate
* IsMovie
* IsSports
* IsNews
* IsKids
* IsSeries
* ChannelId

## Name & EpisodeTitle
For programs and timers that are part of a series, **Name will always equal the series name**, while EpisodeTitle is the title of the episode. Please note that **EpisodeTitle will not always be available**.

## Recording Playback
Playback should be nearly identical to library items. Clients can use the Path property to play directly, if possible, and/or examine MediaStreams to determine the ideal streaming method.

## Timers
A timer represents a single scheduled recording in the future. Timers can be queried using **/LiveTv/Timers**. If desired they can be filtered based on **ChannelId** or **SeriesTimerId**. A single timer can be retrieved by Id using **/LiveTv/Timers/{Id}**. 

When displaying timers, use the ProgramInfo property to display information about the event, including an image. Be sure to handle the situation where this property is null though. (e.g. manual timer or program info not available yet).

To schedule a new timer, first make a call to **/LiveTv/Timers/Defaults**. This will return a default timer object. If the timer is based on a program, pass **ProgramId** on the query string. The default timer will be populated with default times and padding values based on configuration. To create or update a timer, POST the object to **/LiveTv/Timers** or **/LiveTv/Timers/{Id}**.

## Series Timers
A series timer represents a scheduled sequence of recordings. SeriesTimers can be queried using **/LiveTv/SeriesTimers**. They can be sorted by Name or Priority.

To schedule a new series timer, first make a call to **/LiveTv/Timers/Defaults**. This will return a default timer object. If the timer is based on a program, pass **ProgramId** on the query string. The default timer will be populated with default times and padding values based on configuration. To create or update a timer, POST the object to **/LiveTv/SeriesTimers** or **/LiveTv/SeriesTimers/{Id}**.