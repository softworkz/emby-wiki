Clients can easily remote control other clients. The first step is to make a call to **/Sessions**. 

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

* /Sessions/{Id}/Stop
* /Sessions/{Id}/Pause
* /Sessions/{Id}/Unpause
* /Sessions/{Id}/NextTrack
* /Sessions/{Id}/PreviousTrack
* /Sessions/{Id}/Seek?PositionTicks=xxx