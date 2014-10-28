## Authorization Request Header

Add the following request header on every request:

> Authorization=MediaBrowser UserId="e8837bc1-ad67-520e-8cd2-f629e3155721", Client="Android", Device="Samsung Galaxy SIII", DeviceId="xxx", Version="1.0.0.0"

* Device is the product name of the device
* DeviceId is the device's unique id
* Client is the type of client (Android, Dashboard, Dlna, iOS, PC, WindowsPhone, WindowsRT, other)
* Version is the client application version
* UserId is the Id of the current logged in user (if there is one).

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

## User Login 

* Make a call to /Users/Public to get all public users.

* If there are records returned, the app has the option of displaying the users in a visual login screen. This is up to the application developer to decide. If there are no records returned then present a username/password text entry form.

* For each user, if PrimaryImageTag has a value, that indicates the user has an image. The image can then be downloaded using /Users/{Id}/Images/{Type}. See [images](https://github.com/MediaBrowser/MediaBrowser/wiki/Images).

* Each user has a HasPassword property. This is used to determine if the user should be prompted to input a password. The application must authenticate regardless of this value.

## Authenticating a user

* Authenticate using /Users/AuthenticateByName. A 200 status code indicates success, while anything in the 400 or 500 range indicates failure.

* The password must be sent in the body, in two different form fields (password & passwordMd5). password should be an **Sha1**, while passwordMd5 should be an **MD5**. 

* The return result object will have an AccessToken property. This should be included in all subsequent Http requests using the header "X-MediaBrowser-Token"

* If the user explicitly logs out, send a POST to /Sessions/Logout. This will revoke your access token. If the user closes the app without logging out, you can skip this and save the token for future use.

* During normal application usage, if any http requests fail with a 401 response status code, this is generally an indication that the access token has been revoked. The user should be redirected back to the login screen.

* For applications that support connectivity to multiple servers, the token should be saved along with the server's Id in order to avoid sending the wrong token to a particular server. The server Id is part of the SystemInfo object which can be retrieved from /System/Info.

## Parental Control

If user access is disabled due to parental controls, responses will contain **401** status codes and should be handled with the above workflow. 

A response header of **X-Application-Error-Code** will contain **ParentalControl**. This will allow applications to display message if they choose to.