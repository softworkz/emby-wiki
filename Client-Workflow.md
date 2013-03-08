This page will describe the typical workflow for a Media Browser Client.

## Authenticate

* Make a call to /Users to get all users. Display them on a login screen

* The HasPassword property will indicate if a user has a password that requires entry

* Authenticate using /Users/{Id}/Authenticate. There is currently no response body sent back. A 200 status code indicates success, while anything in the 400 or 500 range indicates failure.

* For each user, if PrimaryImageTag has a value, that indicates the user has an image. The image can then be downloaded using /Users/{Id}/Images/{Type}. A separate topic on images will be coming soon.