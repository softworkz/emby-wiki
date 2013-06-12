Clients can easily remote control other clients. The first step is to make a call to **/Sessions**. 

This will return a list of active sessions. This is testable via swagger and the properties returned should be self-explanatory, e.g. UserName, UserId, LastActivityDate, etc. 

NowViewingContext is the section of the client currently being viewed. Possible values are:

* movies
* music
* tv
* games
* (blank) for general and/or clients that are entirely folder-based.
