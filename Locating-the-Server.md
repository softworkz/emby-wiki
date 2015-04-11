Emby features a built-in Udp server, which allows clients to discover it automatically. 

Simply send a **udp broadcast message** on port **7359**, with the text "who is EmbyServer?".

You'll receive a message that is a Json structure containing three properties:

* Address
* Id
* Name