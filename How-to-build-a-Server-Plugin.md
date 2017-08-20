>Please see our [Development Policy](Development-Policy) before beginning development.

First install Emby Server, or download the code. Get the server up and running.

### Create your Visual Studio Solution (VS 2017+)

1. Create a .NET Standard 2.0 class library project. 

2. Go to Properties -> AssemblyInfo.cs. Change AssemblyVersion to "1.0.*" so that it auto-updates, and remove the AssemblyFileVersion line altogether. This will keep both the assembly and file version numbers in sync.

2. Make sure AssemblyInfo.cs has a Guid, e.g:

`[assembly: Guid("02CF7D91-16F4-48D4-BC97-16D89C16AA0A")]`

If not, copy that and generate a new GUID using Tools -> Create Guid.

3. Install the [Emby.Server.Core nuget package](https://www.nuget.org/packages/MediaBrowser.Server.Core/)

4. Create a class called PluginConfiguration, and have it inherit from MediaBrowser.Model.Plugins.BasePluginConfiguration.

5. Create a class called Plugin, and have it inherit from MediaBrowser.Common.Plugins.BasePlugin&lt;T&gt;, where T is the name of the PluginConfiguration class you just created.  You will need to implement its constructor like so:

> public Plugin(IApplicationPaths applicationPaths, IXmlSerializer xmlSerializer) : base(applicationPaths, xmlSerializer)

### Create the Build Event

Right click the project -> Properties. Create a post-build event that will copy the assembly to the server's plugins directory. For example:

`xcopy "$(TargetPath)" "%AppData%\MediaBrowser-Server\Plugins\" /y`

### Test the Plugin

Shutdown the server, rebuild your solution, and restart the server. At this point you should see your plugin in the Dashboard's Plugins menu.

### Add Functionality

To add real functionality to your plugin, you will need an entrypoint that can initialize and accept the various dependencies you may need in order to interact with the MB environment.

This is done by creating a class that implements the IServerEntryPoint interface.  See [Automatic Type Discovery](Automatic-Type-Discovery) for this and other types you can include in your plug-in. Its constructor can accept any number of injected dependencies - depending on what your plugin needs to access.  See [Dependency Injection](Dependency-Injection).

If your plugin will be a premium plugin, see IRequiresRegistration in [Other Interfaces](Other-Interfaces).

### Debugging

The quickest way to test code changes is to work without the debugger. If you do this, you can leave the server running at all times. Simply use the Rebuild command on your plugin project, and right click the server tray -> Restart Server. If that option is not visible you'll need to enable developer tools in the Dashboard under Advanced.