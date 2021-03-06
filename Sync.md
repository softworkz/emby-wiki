Any client can report that it supports sync with two additions to their ClientCapabilities:

* Specify **SupportsSync** = true
* Specify DeviceProfile object

A DeviceProfile is the same structure that is used by Dlna Profiles. The default profile can be found here:

https://github.com/MediaBrowser/MediaBrowser/blob/master/MediaBrowser.Model/Dlna/Profiles/DefaultProfile.cs

For brevity, all Dlna-specific properties such as ProtocolInfo, Manufacturer/Model, etc. can be omitted.

To verify the server acknowledges your sync support, create a sync job using the web interface and test to make sure the device shows up as a selectable sync target.

## Determining user sync privileges

To determine if a user has sync privileges, check user.Policy.EnableSync.

## Sync Selections

Clients should make sync available from as many contexts as possible. This includes, but is not limited to:

* Detail screens
* List screens (single selection)
* List screens (multi-selection)
* Home screen (single selection)
* Home screen (category selection, e.g. Next Up, Latest Movies, etc).

All library items are eligible for sync and clients should not artificially filter them. Instead, simply check the **SupportsSync** property to determine if an item supports syncing. You will need to include **SyncInfo** as part of your requested fields in order to make this property available.

## Sync Dialog

This will discuss the menu that should be presented after a user has chosen to sync something.

Note: If using our api libraries, simply call SyncHelper.GetSyncOptions and it will return a list of all the choices that should be presented based on what the user has selected.

* **Name** - Display only if multiple items have been selected. If a single item or category, omit and the server will automatically assign a name.
* **Quality** - Only if syncing video content. See SyncHelper for examples.
* **Unwatched** - Only if syncing video content. See SyncHelper for examples.
* **SyncNewContent** - Only if syncing a folder or category. See SyncHelper for examples.
* **ItemLimit** - Only if syncing a folder or category. See SyncHelper for examples.

## Creating Sync Jobs

To create a sync job, send a Post to /Sync/Jobs. The **TargetId** property should be the client's reported **DeviceId**.

**Notes**:

* If the user chooses to sync a Genre, MusicGenre, GameGenre, Studio, or Person, then the ParentId property should also be supplied, in order to limit the scope of the sync to the section of the library they're currently browsing. The ParentId is the Id of the top level user view.

* If the user chooses to sync a special category (e.g. Latest, Resume, Next Up), then a ParentId should also be supplied (see above note).

A complete example is available in our ApiClient libraries. See CreateSyncJob.

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