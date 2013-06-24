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