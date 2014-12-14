Any client can report that it supports sync with two additions to their ClientCapabilities:

* Specify **SupportsSync** = true
* Specify DeviceProfile object

A DeviceProfile is the same structure that is used by Dlna Profiles. The default profile can be found here:

https://github.com/MediaBrowser/MediaBrowser/blob/master/MediaBrowser.Model/Dlna/Profiles/DefaultProfile.cs

For brevity, all Dlna-specific properties such as ProtocolInfo, Manufacturer/Model, etc. can be omitted.

## Creating Sync Jobs

Coming soon.