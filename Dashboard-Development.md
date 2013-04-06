The dashboard is built with **jQuery** and **jQuery mobile**.

It also utilizes [MediaBrowser.ApiClient.Javascript](https://github.com/MediaBrowser/MediaBrowser.ApiClient.Javascript) for all communication with MB server.

The html code is located within the dashboard-ui folder of the Dashboard project. This is copied to the build output folder, so all html, javascript, css and image files **must be marked as "copy if newer"**.

If you'd like to contribute, there's two ways you can modify dashboard code:

## Visual Studio
The preferred way to work within the dashboard is directly within visual studio. In between changes you will need to stop the server and use the rebuild command on the plugin project.

You may choose to set the **DashboardSourcePath **configuration setting to your dashboard-ui source folder for easier development. This will remove the need to restart the server after making markup changes.

## Installed Server
If you don't have visual studio, you can still work with the dashboard.

Simply shutdown the server, open the system configuration file, and set the set the **DashboardSourcePath** configuration setting to your dashboard-ui source folder.

You'll also want to set **EnableDashboardResponseCaching to false**. Without this you'll have to clear your browser cache in between testing changes.

Once complete you'll be able to keep the server running, modify dashboard-ui files and simply refresh the browser.