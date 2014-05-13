Clients can easily remote control other clients. The first step is to make a call to **/Sessions**. Add the **ControllableByUserId** param to only receive sessions that are controllable by a given user.

This will return a list of active sessions. This is testable via swagger and the properties returned should be self-explanatory, e.g. UserName, UserId, LastActivityDate, etc. 

###Sending a play command

You can instruct a client to play something by posting to the following url:

/Sessions/{Id}/Playing

The following values should be included within post data:

* ItemIds - A comma-delimited list of item id's
* StartPositionTicks - The starting position of the first item. 
* PlayCommand - PlayNow, PlayNext or PlayLast

Note: StartPositionTicks is ignored when PlayCommand is PlayNext or PlayLast.

###Sending a playstate command

The following commands are available:

* /Sessions/{Id}/Playing/Stop
* /Sessions/{Id}/Playing/Pause
* /Sessions/{Id}/Playing/Unpause
* /Sessions/{Id}/Playing/NextTrack
* /Sessions/{Id}/Playing/PreviousTrack
* /Sessions/{Id}/Playing/Seek?PositionTicks=xxx

###Sending a general command

The following commands are available:

* /Sessions/{Id}/Command/GoHome
* /Sessions/{Id}/Command/GoToSettings
* /Sessions/{Id}/Command/Mute
* /Sessions/{Id}/Command/Unmute
* /Sessions/{Id}/Command/ToggleMute
* /Sessions/{Id}/Command/VolumeUp
* /Sessions/{Id}/Command/VolumeDown