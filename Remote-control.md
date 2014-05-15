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

General commands are sent using /Sessions/{Id}/Command/{CommandName}

If arguments are required, the body of the request should be of contentType application/json and have the following structure:
> {
> Arguments:{
> "Name": "Value"
> }
> }

Below are the list of known core command **names**, along with the list of properties available in Arguments.

* MoveUp,
* MoveDown,
* MoveLeft,
* MoveRight,
* PageUp,
* PageDown,
* PreviousLetter (scroll list to previous letter),
* NextLetter (scroll list to next letter),
* ToggleOsd  (show or hide video player OSD),
* ToggleContextMenu (show or hide information relating to selected list item),
* Select (enter),
* Back,
* TakeScreenshot,
* SendKey (tbd),
* SendString (Enter text into application - Arguments: String),
* GoHome,
* GoToSettings,
* VolumeUp,
* VolumeDown,
* Mute,
* Unmute,
* ToggleMute,
* SetVolume (Arguments: Volume 0-100 scale),
* SetAudioStreamIndex = (Arguments: Index),
* SetSubtitleStreamIndex = (Arguments: Index. If -1 turn off subtitles),
* ToggleFullscreen ,
* DisplayContent (Arguments: ItemName, ItemId, ItemType),
* GoToSearch,
* DisplayMessage (Arguments: Header, Text, TimeoutMs - if timeout is omitted, message should be modal)