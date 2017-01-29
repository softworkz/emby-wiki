The web app is primarily built with plain JavaScript.

It also utilizes [Emby.ApiClient.Javascript](https://github.com/MediaBrowser/MediaBrowser.ApiClient.Javascript) for all communication with Emby server.

If you'd like to contribute, here is the procedure to follow. This works both when running from source and using the installed Emby Server.

## Clone the Standalone Web App Repository
Clone the **master** branch of this repository:

https://github.com/MediaBrowser/emby-web-mobile

**Note** - when you clone, make sure to specifically indicate the master branch

## Configure Emby Server
Shutdown the server, open the system configuration file, and set the set the **DashboardSourcePath** configuration setting to the src sub-directory of the web app repository that you just cloned.

You'll also want to set **EnableDashboardResponseCaching to false**. Without this you'll have to clear your browser cache in between testing changes.

Once complete you'll be able to keep the server running, modify source files and simply refresh the browser.