When a client is ready to start media playback, there are three API methods that are used to keep the server up to date with the users activity, and record the users current playback position.

## Playback Started

To let the server know playback started, make an HTTP POST call to /Users/{UserId}/PlayingItems/{Id}

**UserId** and **Id** are required values.

Once this API call is made, the server dashboard will show the current item that the user is watching.

## Playback Progress

To report progress make an HTTP POST call to /Users/{UserId}/PlayingItems/{Id}/Progress

**UserId** and **Id** are required values.

If the client media player has the current position available, then the **PositionTicks** argument should be added to the URL. 1 tick = 10,000 ms. 

example:  
`http://localhost:8096/mediabrowser/Users/4fe34e3c20fb9a161b5bc16e77b135a7/`  `PlayingItems/bede2ced958abb58cccda473a0f2afec/Progress?PositionTicks=7281356`

Playback progress should be reported as often as is reasonable based on the device and connection to the server. The server dashboard will show a users current activity for several minutes after each progress update, so it's best to not let too much time pass between updates.  

## Playback Stopped

Once playback is stopped, make a call using the HTTP DELETE method to /Users/{UserId}/PlayingItems/{Id}

**UserId** and **Id** are required values.

As with Playback Progress, you should add the **PositionTicks** argument to this API call.

After this API call is made, the server dashboard will update to reflect that the user is not currently playing an item.

## More Info

For more information on these three methods, consult the Swagger API documentation. The [MediaBrowser.ApiClient](https://github.com/MediaBrowser/MediaBrowser.ApiClient) repository also has examples of these methods.