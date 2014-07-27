Media Browser features a built-in Udp server, which allows clients to discover it automatically. 

Simply send a **udp broadcast message** on port **7359**, with the text "who is MediaBrowserServer_v2?".

You'll receive a message in the format of:

`MediaBrowserServer|192.168.1.1:1234|xxx`

Where xxx is the ServerId