## Authorization Request Header

Add the following request header on every request:

> Authorization=MediaBrowser UserId="e8837bc1-ad67-520e-8cd2-f629e3155721", Client="Android", Device="Samsung Galaxy SIII", DeviceId="xxx", Version="1.0.0.0"

* Device is the product name of the device
* DeviceId is the device's unique id
* Client is the type of client (Android, Dashboard, Dlna, iOS, PC, WindowsPhone, WindowsRT, other)
* Version is the client application version

The dashboard currently displays customized icons for the following clients:

* Android
* Chromecast
* Dashboard
* Dlna
* iOS
* Media Browser Theater
* Media Browser Classic
* Roku
* Windows Phone
* Windows RT
* Xbmc

## User Login - Mobile Clients

* Display a login form with username and password fields.

## User Login - TV Clients

* Make a call to /Users/Public to get all public users.

* If there are records returned, the app should display users visually. If there are no records returned then present a username/password text entry form.

* For each user, if PrimaryImageTag has a value, that indicates the user has an image. The image can then be downloaded using /Users/{Id}/Images/{Type}. See [images](https://github.com/MediaBrowser/MediaBrowser/wiki/Images).

## Authenticating a user

* Authenticate using /Users/AuthenticateByName. There is currently no response body sent back. A 200 status code indicates success, while anything in the 400 or 500 range indicates failure.

* The password must be sent in the body, and must be an **Sha1**.

* Once you've authenticated, you are free to offer "Remember login" settings so that this screen does not have to be presented in the future.

* Each user has a HasPassword property, indicating if a password input should be presented when a user is selected.

