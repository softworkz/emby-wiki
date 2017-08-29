>Please see our [Development Policy](Development-Policy) before beginning development.

First install Emby Server, or download the code. Get the server up and running.

### Create your Visual Studio Solution (VS 2017+)

1. Create a .NET Standard 1.3 class library project. 

2. Install the [Emby.Server.Core nuget package](https://www.nuget.org/packages/MediaBrowser.Server.Core/)

3. Create a class called PluginConfiguration, and have it inherit from MediaBrowser.Model.Plugins.BasePluginConfiguration.

4. Create a class called Plugin, and have it inherit from MediaBrowser.Common.Plugins.BasePlugin&lt;T&gt;, where T is the name of the PluginConfiguration class you just created.  You will need to implement its constructor like so:

> public Plugin(IApplicationPaths applicationPaths, IXmlSerializer xmlSerializer) : base(applicationPaths, xmlSerializer)

5. Create a random GUID using visual studio's Create Guid tool under the Tools menu. In Plugin.cs, override the Id property, and return the guid you just created. This will be the Id for the plugin and can never be changed.

## Create a Post-Build Event

Right click the project -> Properties. Create a post-build event that will copy the assembly to the server's plugins directory. For example:

`xcopy "$(TargetPath)" "%AppData%\MediaBrowser-Server\Plugins\" /y`

## Test the Plugin

Shutdown the server, rebuild your solution, and restart the server. At this point you should see your plugin in the Dashboard's Plugins menu.

## Add Functionality

To add real functionality to your plugin, you will need an entrypoint that can initialize and accept the various dependencies you may need in order to interact with the MB environment.

This is done by creating a class that implements the IServerEntryPoint interface.  See [Automatic Type Discovery](Automatic-Type-Discovery) for this and other types you can include in your plug-in. Its constructor can accept any number of injected dependencies - depending on what your plugin needs to access.  See [Dependency Injection](Dependency-Injection).

If your plugin will be a premium plugin, see IRequiresRegistration in [Other Interfaces](Other-Interfaces).

## Debugging

The quickest way to test code changes is to work without the debugger. If you do this, you can leave the server running at all times. Simply use the Rebuild command on your plugin project, and right click the server tray -> Restart Server. If that option is not visible you'll need to enable developer tools in the Dashboard under Advanced.