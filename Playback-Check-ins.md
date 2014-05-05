When a client is ready to start media playback, there are three API methods that are used to keep the server up to date with the users activity, and record the users current playback position.

## Playback Started

To let the server know playback started, make an HTTP POST call to **/Sessions/Playing**

The body of the request should be a JSON object with the following properties:

* QueueableMediaTypes (Array[string] - Audio,Video),
* CanSeek (boolean),
* ItemId (string) or Item {object},
* MediaSourceId (string),
* AudioStreamIndex (int, optional),
* SubtitleStreamIndex (int, optional),
* IsPaused (boolean),
* IsMuted (boolean),
* PositionTicks (long, optional),
* VolumeLevel (int, optional 0-100),
* PlayMethod (string) = ['Transcode' or 'DirectStream' or 'DirectPlay']

The content type of the request should be **application/json**.

Once this API call is made, the server dashboard will show the current item that the user is watching.

### ItemId vs Item

If the user is playing a server library item, simply supply the ItemId property and omit Item. If the user is playing content that is not part of the server library, it can still be reported by supplying an object containing information describing the media.

### Item Properties

* Name (string),
* MediaType (string - Audio, Video, Book, Game),
* RunTimeTicks (long, optional),
* PremiereDate (Date, optional),
* ProductionYear (int, optional),
* IndexNumber (int, optional),
* IndexNumberEnd (int, optional),
* ParentIndexNumber (int, optional),
* SeriesName (string),
* Album (string),
* Artists (Array[string])

## Playback Progress

To report progress make an HTTP POST call to **/Sessions/Playing/Progress**

The contents of the request are identical to the playback start message.

Playback progress should be reported as often as is reasonable based on the device and connection to the server. The server dashboard will show a users current activity for several minutes after each progress update, so it's best to not let too much time pass between updates.  

## Playback Stopped

Once playback is stopped, make a call using the HTTP DELETE method to /Users/{UserId}/PlayingItems/{Id}

**UserId**, **MediaSourceId** and **Id** are required values.

As with Playback Progress, you should add the **PositionTicks** argument to this API call.

After this API call is made, the server dashboard will update to reflect that the user is not currently playing an item.

## Manually marking watched/unwatched

An Item can be marked watched manually by sending a POST to 

/Users/{UserId}/PlayedItems/{Id}

To mark an item unwatched, send a DELETE to

/Users/{UserId}/PlayedItems/{Id}

## More Info

For more information on these three methods, consult the Swagger API documentation. The [MediaBrowser.ApiClient](https://github.com/MediaBrowser/MediaBrowser.ApiClient) repository also has examples of these methods.