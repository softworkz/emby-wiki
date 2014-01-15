Begin live tv support by making a call to **/LiveTv/Info**. The ActiveServiceName will tell you if there is a live tv service plugin installed on the server.

### Channels

Query for tv channels using **/LiveTv/Channels**. The most interesting channel properties are:

* Name
* Number
* ChannelType
* CurrentProgram

Channel images use the same api endpoints as regular library items, e.g. **/Items/{Id}/Images/Primary**. Channels also can have user data allowing users to like or favorite them which will help influence suggested programs.