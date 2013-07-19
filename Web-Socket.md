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

#### Play

#### UpdatePlaystate

#### NotificationAdded
#### NotificationUpdated
#### NotificationsMarkedRead