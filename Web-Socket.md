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

As soon as the connection is established, an identification message should be sent by the client which includes the client name, device id, application version and device name. For example

`
{

    MessageType: "Identity",

    Data: "Dashboard|df787898fdsf7ds80|1.0.0.0|nexus7"
}
`

The client name **must match** the value used in http authorization headers.

## Messages

Once connected and identified, you'll be able to receive the following MessageTypes from the web socket:

#### UserDataChanged
A user changed their personal rating for an item, or their playstate was updated. Data = a json object with the following properties:
* UserId
* UserDataList - a list of updated user data objects

#### UserDeleted
Data = the user id that has been deleted

#### UserUpdated
Data = the user object that has been updated

#### NotificationAdded
#### NotificationUpdated
#### NotificationsMarkedRead

#### RestartRequired
This indicates the server needs to be restarted. There is no data associated with this.

#### ServerRestarting, ServerShuttingDown
This will tell you when the server is restarting or shutting down.

#### Play
A remote control play command has been sent from the server. Data = a json object with the following properties:
* ItemIds - an array of item id's to play
* PlayCommand - PlayNow, PlayNext or PlayLast
* StartPositionTicks - If supplied, this is the position in which the first title should start at.

#### Playstate
A remote control update playstate command has been sent from the server. Data = a json object with the following properties:
* Command - Stop, Pause, Unpause, NextTrack, PreviousTrack, Seek
* SeekPositionTicks - Used with the seek command.

## Playback check-ins

Playback check-ins can also be sent over the web socket, allowing the client to send them more often due to the reduced overhead.

See the playback check-in article.