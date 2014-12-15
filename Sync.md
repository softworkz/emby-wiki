Any client can report that it supports sync with two additions to their ClientCapabilities:

* Specify **SupportsSync** = true
* Specify DeviceProfile object

A DeviceProfile is the same structure that is used by Dlna Profiles. The default profile can be found here:

https://github.com/MediaBrowser/MediaBrowser/blob/master/MediaBrowser.Model/Dlna/Profiles/DefaultProfile.cs

For brevity, all Dlna-specific properties such as ProtocolInfo, Manufacturer/Model, etc. can be omitted.

## Determining user sync privileges

Coming soon.

## Creating Sync Jobs

Coming soon.

## Running sync jobs

All of the client-side code needed to run sync jobs is provided in our Api libraries. The MultiServerSync operation will handle both sync and camera upload for all authenticated servers. It is available in both .NET and Java:

https://github.com/MediaBrowser/MediaBrowser.ApiClient
https://github.com/MediaBrowser/MediaBrowser.ApiClient.Java

If using another language it will need to be ported.

## Client-side sync management

Coming soon.

## Online access

Coming soon.

## Offline access

Coming soon.