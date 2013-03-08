This page will describe the typical workflow for a Media Browser Client.

Documentation for all of the url's mentioned here can be seen viewed using the server's built-in documentation. Some of these url's can be tested directly within the swagger documentation feature.

## Authenticate

* Make a call to /Users to get all users. Display them on a login screen

* The HasPassword property will indicate if a user has a password that requires entry

* Authenticate using /Users/{Id}/Authenticate. There is currently no response body sent back. A 200 status code indicates success, while anything in the 400 or 500 range indicates failure.

* For each user, if PrimaryImageTag has a value, that indicates the user has an image. The image can then be downloaded using /Users/{Id}/Images/{Type}. See [images](https://github.com/MediaBrowser/MediaBrowser/wiki/Images)

* Once you've authenticated, you are free to offer "Remember login" settings so that this screen does not have to be presented in the future. Given that we're a simple personal media player, we do not use any kind of security tokens so there won't be any session expiration.