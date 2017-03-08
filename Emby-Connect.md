Emby Connect is an **optional** service designed to make multi-server connectivity easier. For this reason, we recommend that you first implement multi-server switching in your app via manual address entry, and then later supplement that with Emby Connect.

The best way to manage multi-server connectivity is to always have a server Id in context, from which you can use to retrieve your saved credentials.

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