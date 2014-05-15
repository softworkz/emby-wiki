Clients can easily remote control other clients. The first step is to make a call to **/Sessions**. Add the **ControllableByUserId** param to only receive sessions that are controllable by a given user.

An example session is:

```json
  {
    "CanSeek": false,
    "SupportedCommands": [
      "MoveUp",
      "MoveDown",
      "MoveLeft",
      "MoveRight",
      "PageUp",
      "PageDown",
      "PreviousLetter",
      "NextLetter",
      "ToggleOsd",
      "ToggleContextMenu",
      "Select",
      "Back",
      "TakeScreenshot",
      "SendKey",
      "SendString",
      "GoHome",
      "GoToSettings",
      "VolumeUp",
      "VolumeDown",
      "Mute",
      "Unmute",
      "ToggleMute",
      "SetVolume",
      "SetAudioStreamIndex",
      "SetSubtitleStreamIndex",
      "ToggleFullscreen",
      "DisplayContent",
      "GoToSearch",
      "DisplayMessage"
    ],
    "RemoteEndPoint": "192.168.1.4",
    "QueueableMediaTypes": [
      "Video"
    ],
    "PlayableMediaTypes": [
      "Audio",
      "Video",
      "Game",
      "Photo",
      "Book"
    ],
    "Id": "4de66e1e6b8a4cae89542dc6f7ee7623",
    "UserId": "e8837bc1ad67520e8cd2f629e3155721",
    "UserPrimaryImageTag": "605eed331af1e1a8770643ee6fd1c2b9",
    "UserName": "Luke",
    "AdditionalUsers": [],
    "ApplicationVersion": "3.0.5243.22734",
    "Client": "Media Browser Theater",
    "LastActivityDate": "2014-05-15T09:52:52.5898360Z",
    "NowViewingItem": {
      "Name": "Partridge",
      "Id": "0f8d0805a66f7ed429ecd8890146c7c3",
      "Type": "Episode",
      "MediaType": "Video",
      "RunTimeTicks": 12882240000,
      "PrimaryImageTag": "d7c02f11a99ba4b7381e86bb602596c1",
      "PrimaryImageItemId": "0f8d0805a66f7ed429ecd8890146c7c3",
      "LogoImageTag": "108e85fbb573fc406652374b785ec6be",
      "LogoItemId": "09bed955402d0bf2d59c2e9cee67beed",
      "ThumbImageTag": "01760cf565aaba7cd9ac5350bb46383b",
      "ThumbItemId": "09bed955402d0bf2d59c2e9cee67beed",
      "BackdropImageTag": "a6aeacb6a86f13e8c6a582ebf03b3f2a",
      "BackdropItemId": "09bed955402d0bf2d59c2e9cee67beed",
      "PremiereDate": "2013-04-04T04:00:00.0000000Z",
      "ProductionYear": 2013,
      "IndexNumber": 17,
      "ParentIndexNumber": 5,
      "SeriesName": "Parks and Recreation",
      "Artists": [],
      "MediaStreams": [],
      "Chapters": []
    },
    "DeviceName": "LIVINGROOM-PC",
    "IsPaused": false,
    "IsMuted": false,
    "DeviceId": "LIVINGROOM-PC",
    "SupportsRemoteControl": false,
    "PlayState": {
      "CanSeek": false,
      "IsPaused": false,
      "IsMuted": false
    }
  }
```

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