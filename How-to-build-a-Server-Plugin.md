First install Media Browser Server, or download the code. Get the server up and running.

### Create your Visual Studio 2012 Solution

1. In your new project, go to Properties -> AssemblyInfo.cs. Change AssemblyVersion to "1.0.*" so that it auto-udpates, and remove the AssemblyFileVersion line altogether. This will keep both the assembly and file version numbers in sync.

2. Make sure AssemblyInfo.cs has a Guid, e.g:

`[assembly: Guid("{02CF7D91-16F4-48D4-BC97-16D89C16AA0A}")]`

If not, copy that and generate a new GUID using Tools -> Create Guid.

3. Install the [MediaBrowser.Server.Core nuget package](https://www.nuget.org/packages/MediaBrowser.Server.Core/)

4. Create a class called PluginConfiguration, and have it inherit from MediaBrowser.Model.Plugins.BasePluginConfiguration.

5. Create a class called Plugin, and have it inherit from MediaBrowser.Common.Plugins.BasePlugin-T, where T is the name of the PluginConfiguration class you just created.

### Create the Build Event

Right click the project -> Properties. Create a post-build event that will copy the assembly to the server's plugins directory. For example:

`xcopy "$(TargetPath)" "C:\ProgramData\MediaBrowser-Server\Plugins\" /y`

### Test the Plugin

Shutdown the server, rebuild your solution, and restart the server. At this point you should see your plugin in the Dashboard's Plugins menu.