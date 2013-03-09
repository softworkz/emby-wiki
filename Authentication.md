Media Browser libraries are user-based, so the first step in the client workflow is to authenticate the user.

## User Login

* Make a call to /Users to get all users. Display them on a login screen

* The HasPassword property will indicate if a user has a password that requires entry

* Authenticate using /Users/{Id}/Authenticate. There is currently no response body sent back. A 200 status code indicates success, while anything in the 400 or 500 range indicates failure.

* For each user, if PrimaryImageTag has a value, that indicates the user has an image. The image can then be downloaded using /Users/{Id}/Images/{Type}. See [images](https://github.com/MediaBrowser/MediaBrowser/wiki/Images).

* Once you've authenticated, you are free to offer "Remember login" settings so that this screen does not have to be presented in the future. Given that we're a simple personal media player, we do not use any kind of security tokens so there won't be any session expiration.

## Authorization Request Header

Coming soon.

There are two ways to provide library browsing, either file-system based or using virtual views based on queries.

