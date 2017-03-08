Emby Connect is an **optional** service designed to make multi-server connectivity easier. For this reason, we recommend that you first implement multi-server switching in your app via manual address entry, and then later supplement that with Emby Connect.

The best way to manage multi-server connectivity is to always have a ServerId in context, from which you can use to retrieve your saved server information. In other words, avoid a single global value related to a logged in server, because a user can login to multiple servers simultaneously.

## Login

Emby Connect has two login methods:

* Pin code sign in (designed for TV apps)
* Traditional username/password sign in (designed for mobile, tablet and desktop apps)

### Login with username & password

Send a POST to https://connect.emby.media/service/user/authenticate

The content type should be application/json, and here is an example structure:

`{
                    nameOrEmail: username,
                    rawpw: password
                }`

The request headers should contain the following:

* X-Application header, formatted as AppName/AppVersion

A successful response will contain application/json content, and include the following properties:

* ConnectAccessToken
* ConnectUserId

## Get a list of servers for a user

Send a GET to https://connect.emby.media/service/servers?userId={ConnectUserId}

The request headers should contain the following:
* X-Application (discussed above)
* X-Connect-UserToken (the ConnectUserToken value)