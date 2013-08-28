First install Media Browser Server, or download the code. Get the server up and running.

### Create your Visual Studio 2012 Solution

>QuickStart -> The below steps outline the complete process but you can also download our server plug-in template for a quick start to creating add-on functionality to MB Server.  Just download [this file](http://www.mediabrowser3.com/downloads/ServerPluginCollection.zip) into your Visual Studio 2012/Templates/ProjectTemplates folder.  Then re-start VS and create a new project based on the "Server Plug-in with Collection Folder" template.  Then all you will need to do is add the Server Nuget package and confirm your post-build event is copying to where your server data folder resides.

1. Create a class library project

2. Go to Properties -> AssemblyInfo.cs. Change AssemblyVersion to "1.0.*" so that it auto-udpates, and remove the AssemblyFileVersion line altogether. This will keep both the assembly and file version numbers in sync.

2. Make sure AssemblyInfo.cs has a Guid, e.g:

`[assembly: Guid("{02CF7D91-16F4-48D4-BC97-16D89C16AA0A}")]`

If not, copy that and generate a new GUID using Tools -> Create Guid.

3. Install the [MediaBrowser.Server.Core nuget package](https://www.nuget.org/packages/MediaBrowser.Server.Core/)

4. Create a class called PluginConfiguration, and have it inherit from MediaBrowser.Model.Plugins.BasePluginConfiguration.

5. Create a class called Plugin, and have it inherit from MediaBrowser.Common.Plugins.BasePlugin-T, where T is the name of the PluginConfiguration class you just created.  You will need to implement its constructor like so:

> public Plugin(IApplicationPaths applicationPaths, IXmlSerializer xmlSerializer) : base(applicationPaths, xmlSerializer)

### Create the Build Event

Right click the project -> Properties. Create a post-build event that will copy the assembly to the server's plugins directory. For example:

`xcopy "$(TargetPath)" "%AppData%\MediaBrowser-Server\Plugins\" /y`

### Test the Plugin

Shutdown the server, rebuild your solution, and restart the server. At this point you should see your plugin in the Dashboard's Plugins menu.

### Add Functionality

To add real functionality to your plugin, you will need an entrypoint that can initialize and accept the various dependencies you may need in order to interact with the MB environment.

This is done by creating a class that implements the IServerEntryPoint interface.  See [Automatic Type Discovery](https://github.com/MediaBrowser/MediaBrowser/wiki/Automatic-Type-Discovery) for this and other types you can include in your plug-in. Its constructor can accept any number of injected dependencies - depending on what your plugin needs to access.  See [Dependency Injection](https://github.com/MediaBrowser/MediaBrowser/wiki/Dependency-Injection).

If your plugin will be a premium plugin, see IRequiresRegistration in [Other Interfaces](https://github.com/MediaBrowser/MediaBrowser/wiki/Other-Interfaces).

### Debugging

The quickest way to test code changes is to work without the debugger. If you do this, you can leave the server running at all times. Simply use the Rebuild command on your plugin project, and right click the server tray -> Restart Server. If that option is not visible you'll need to enable developer tools in the Dashboard under Advanced.