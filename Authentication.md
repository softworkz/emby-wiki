Media Browser libraries are user-based, so the first step in the client workflow is to authenticate the user.

## User Login

* Make a call to /Users/Public to get all public users. Also make a call to /Server/Configuration to get the server configuration.

* Depending on the results, you should either display the users visually, or present a traditional username/password text entry form.

* **Only display the users visually if at least one public user is returned, and configuration.ManualLoginClients does not have an entry pertaining to your client**. Current values are Mobile, MediaBrowserTheater, and Roku.

* The HasPassword property will indicate if a user has a password that requires entry, but always display the password field on a manual entry form.

* Clients are free to completely forego a visible user list and simply present a traditional login form. In this case, none of the above api calls will be necessary.

## Authenticating a user

* Authenticate using /Users/{Name}/AuthenticateByName. There is currently no response body sent back. A 200 status code indicates success, while anything in the 400 or 500 range indicates failure.

* The password must be sent in the body, and must be an **Sha1**.

* For each user, if PrimaryImageTag has a value, that indicates the user has an image. The image can then be downloaded using /Users/{Id}/Images/{Type}. See [images](https://github.com/MediaBrowser/MediaBrowser/wiki/Images).

* Once you've authenticated, you are free to offer "Remember login" settings so that this screen does not have to be presented in the future.

## Authorization Request Header

Add the following request header on every request:

> Authorization=MediaBrowser UserId="e8837bc1-ad67-520e-8cd2-f629e3155721", Client="Android", Device="Samsung Galaxy SIII", DeviceId="xxx", Version="1.0.0.0"

* Device is the product name of the device
* DeviceId is the device's unique id
* Client is the type of client (Android, Dashboard, Dlna, iOS, PC, WindowsPhone, WindowsRT, other)
* Version is the client application version

The dashboard currently displays customized icons for the following clients:

* Android
* Dashboard
* Dlna
* iOS
* Media Browser Theater
* Media Browser Classic
* Roku
* Windows Phone
* Windows RT