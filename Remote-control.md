Clients can easily remote control other clients. The first step is to make a call to **/Sessions**. Add the **ControllableByUserId** param to only receive sessions that are controllable by a given user.

This will return a list of active sessions. This is testable via swagger and the properties returned should be self-explanatory, e.g. UserName, UserId, LastActivityDate, etc. 

NowViewingContext is the section of the application currently being viewed. Possible values are:

* movies
* music
* tv
* games
* (blank) for general and/or clients that are entirely folder-based.

###Sending a browse command

You can instruct a client to browse to something by posting to the following url:

/Sessions/{Id}/Viewing

The following values should be included within post data:

* ItemId - The id of the item to browse to
* ItemName - The name of the item to browse to
* ItemType - The type of the item to browse to
* Context (optional). movies, tv, music, games. Clients may choose to ignore this.

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

###Sending a system command

The following commands are available:

* /Sessions/{Id}/Command/GoHome
* /Sessions/{Id}/Command/GoToSettings
* /Sessions/{Id}/Command/Mute
* /Sessions/{Id}/Command/Unmute
* /Sessions/{Id}/Command/ToggleMute
* /Sessions/{Id}/Command/VolumeUp
* /Sessions/{Id}/Command/VolumeDown

###Sending a message command

This will tell the client to display a message to the user.

* /Sessions/{Id}/Message?text=xxx&header=xxx&timeoutms=5000

If timeoutMs is omitted, the message will be considered modal and the user will be required to confirm it.

Clients are allowed some flexibility here. They are allowed to ignore both header and timeoutMs if these are not feasible to implement.