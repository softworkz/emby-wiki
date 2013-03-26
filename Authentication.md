Media Browser libraries are user-based, so the first step in the client workflow is to authenticate the user.

## User Login

* Make a call to /Users to get all users. Display them on a login screen

* The HasPassword property will indicate if a user has a password that requires entry

* Authenticate using /Users/{Id}/Authenticate. There is currently no response body sent back. A 200 status code indicates success, while anything in the 400 or 500 range indicates failure.

* The password must be sent in the body, and must be an **Sha1**.

* For each user, if PrimaryImageTag has a value, that indicates the user has an image. The image can then be downloaded using /Users/{Id}/Images/{Type}. See [images](https://github.com/MediaBrowser/MediaBrowser/wiki/Images).

* Once you've authenticated, you are free to offer "Remember login" settings so that this screen does not have to be presented in the future. Given that we're a simple personal media player, we do not use any kind of security tokens so there won't be any session expiration.

## Authorization Request Header

At the moment this is used only for logging purposes. After authentication, add the following request header on every request:

> Authorization=MediaBrowser UserId="e8837bc1-ad67-520e-8cd2-f629e3155721", Client="Android", Device="Samsung Galaxy SIII", DeviceId="xxx"

* Device is the product name of the device
* DeviceId is the device's unique id
* Client is the type of client (Android, Dashboard, Dlna, iOS, PC, WindowsPhone, WindowsRT, other)

The dashboard currently displays customized icons for the following clients:

* Android
* Dashboard
* Dlna
* iOS
* Media Browser Theater
* Media Browser Classic
* Windows Phone
* Windows RT

## User Interfaces vs Utilities
While all api consumers are encouraged to report themselves using the request headers, only clients with user interfaces and logged in users need to authenticate and supply a user Id in the header.