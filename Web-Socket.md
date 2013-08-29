Clients are recommended to connect to the server's web socket in order to receive notifications of various system events, which can help reduce the need to repeatedly poll for data through the http api.

### Finding the web socket port

Make a call to /System/Info. WebSocketPortNumber is the port hosting the web socket. From there the connection url is:

`
ws://hostname:{websocketport}/mediabrowser
`

### Message format

All messages sent and received over the web socket are in the format of a json structure:

`
{
    MessageType: "RestartRequired",
    Data: ""
}
`

MessageType is the name of the event or action, Data is any related data. Data can be plain text, or a json structure itself, depending on MessageType.

### Identification message

As soon as the connection is established, an identification message should be sent by the client which includes the client name, device id, and application version. For example

`
{

    MessageType: "Identity",

    Data: "Dashboard|df787898fdsf7ds80|1.0.0.0"
}
`

The client name **must match** the value used in http authorization headers.

## Messages

Once connected and identified, you'll be able to receive the following MessageTypes from the web socket:

#### LibraryChanged
Data = A library update info structure. See [LibraryUpdateInfo.cs](https://github.com/MediaBrowser/MediaBrowser/blob/master/MediaBrowser.Model/Entities/LibraryUpdateInfo.cs)

#### RestartRequired
This indicates the server needs to be restarted. There is no data associated with this.

#### UserDeleted
Data = the user id that has been deleted

#### UserUpdated
Data = the user object that has been updated

#### Browse
A remote control browse command has been sent from the server. Data = a json object with the following properties:
* Context - (movies, tv, games, etc. this can be blank and clients are free to ignore it if using a generic presentation).
* ItemId
* ItemName
* ItemType

#### Play
A remote control play command has been sent from the server. Data = a json object with the following properties:
* ItemIds - an array of item id's to play
* PlayCommand - PlayNow, PlayNext or PlayLast
* StartPositionTicks - If supplied, this is the position in which the first title should start at.

#### Playstate
A remote control update playstate command has been sent from the server. Data = a json object with the following properties:
* Command - Stop, Pause, Unpause, NextTrack, PreviousTrack, Seek
* SeekPositionTicks - Used with the seek command.

#### NotificationAdded
#### NotificationUpdated
#### NotificationsMarkedRead

#### SystemCommand
Data = The command to execute - GoHome, GoToSettings, Mute, Unmute, ToggleMute, VolumeUp, VolumeDown.

#### MessageCommand
Data = a json structure with Header, Text and TimeoutMs properties. This is an instruction to display a message to the user. If a timeout is specified, the message should disappear after that duration. If TimeoutMs is not specified, the message should remain visible until the user confirms it. Clients are allowed flexibility and are permitted to ignore TimeoutMs if it is not feasible to implement.

## Dynamic Messages

In addition to the above messages, there are dynamic messages that can be sent on an interval when the client asks for them.

#### Sessions list

Send a web socket message to the server using **MessageType = "SessionsStart", Data = "1000,1000"**. The server will then send messages with **MessageType="Sessions"** containing the sessions list beginning in 1000ms, and every 1000ms thereafter. This is equivalent to the /Sessions api call without any filtering, which will have to be done client-side. This is useful to help **avoid the need for continuous polling** over the http interface, which comes at a much higher cost.

Adjust the intervals as desired, but **make sure to send a message using MessageType = "SessionsStop" when finished** The server will continue to send the messages until this happens.


## Playback check-ins

Playback check-ins can also be sent over the web socket, allowing the client to send them more often due to the reduced overhead.

#### Playback start
MessageType = "PlaybackStart", Data=ItemId

#### Playback progress
MessageType = "PlaybackProgress", Data="itemId|positionTicks|isPaused|isMuted"

For example, Data = "itemId|1000000|false|true". Position ticks must be part of the value, but empty is ok if it cannot be determined, e.g. "itemId||false|true".

#### Playback stopped
MessageType = "PlaybackStopped", Data="itemId|positionTicks"

## Context messages
As the user browses around you may send context messages to the server to let it know where the user is. The format is MessageType="Context", Data= "ItemType|ItemId|ItemName|context".

All values must be present, but empty values are ok. The context argument refers to the section of the ui being viewed, e.g. movies, tv, games, music, etc. This can also be empty if using a generic presentation.