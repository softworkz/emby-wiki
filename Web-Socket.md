Clients are recommended to connect to the server's web socket in order to receive notifications of various system events, which can help reduce the need to repeatedly poll for data through the http api.

The web socket is also the preferred protocol from which to receive remote control commands.

### Connecting to the web socket

Once connected to the server, simply take the server's http address, and change the protocol to ws:// or wss://.

`
ws://{host}?api_key={authenticationtoken}&deviceId={deviceId}
`

To construct the url, perform a string replacement on the http url rather than building it manually. This will allow your app to support addresses without ports, as well as http/https.

Replace the following:

http: -> ws:

https: -> wss:

### Message format

All messages sent and received over the web socket are in the format of a json structure:

`
{
    MessageType: "RestartRequired",
    Data: ""
}
`

MessageType is the name of the event or action, Data is any related data. Data can be plain text, or a json structure itself, depending on MessageType.

## Messages

Once connected and identified, you'll be able to receive the following MessageTypes from the web socket:

#### GeneralCommand
See below section on commands.

#### UserDataChanged
A user changed their personal rating for an item, or their playstate was updated. Data = a json object with the following properties:
* UserId
* UserDataList - a list of updated user data objects

#### UserDeleted
Data = the user id that has been deleted

#### UserUpdated
Data = the user object that has been updated

#### NotificationAdded
A user has new notifications. Presentations should refresh their notification list.

#### NotificationsMarkedRead
A user has marked notifications read. Presentations should refresh their notification list.

#### RestartRequired
This indicates the server needs to be restarted. There is no data associated with this.

#### ServerRestarting, ServerShuttingDown
This will tell you when the server is restarting or shutting down.

#### Play
A remote control play command has been sent from the server. Data = a json object with the following properties:
* ItemIds - an array of item id's to play
* PlayCommand - PlayNow, PlayNext or PlayLast
* StartPositionTicks - If supplied, this is the position in which the first title should start at.
* MediaSourceId - If supplied, this is the media source that should be used for the first item
* AudioStreamIndex - If supplied, this is the audio stream that should be used for the first item
* SubtitleStreamIndex - If supplied, this is the subtitle stream that should be used for the first item
* StartIndex - If supplied, and if playing a list of items, this is the index of the first item that should be played.

#### Playstate
A remote control update playstate command has been sent from the server. Data = a json object with the following properties:
* Command - Stop, Pause, Unpause, NextTrack, PreviousTrack, Seek
* SeekPositionTicks - Used with the seek command.

## General Commands

Most remote control commands are implemented in a pass-through fashion. That is the server simply takes the command and passes it directly to the client without modification.

The standard web socket message format is utilized. The Data property is an object describing the remote control command. The command will have two properties:

* Name
* Arguments.

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
* PlayTrailers (Arguments: ItemId),
* PlayMediaSource - used to indicate support for receiving the play command along with a specified MediaSourceId, AudioStreamIndex and SubtitleStreamIndex

## Examples

Sample code that parses web server messages can be found here:

https://github.com/MediaBrowser/Emby.ApiClient/blob/master/MediaBrowser.ApiInteraction/ApiWebSocket.cs#L399