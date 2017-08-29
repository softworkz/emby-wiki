>Please see our [Development Policy](Development-Policy) before beginning development.

First install Emby Server, and get it up and running.

## Overview
This will be done using Visual Studio 2017+. Emby Server runs on three different runtimes: the .NET framework, Mono, and .NET Core 2.0. 

To achieve triple compatibility with all three runtimes, you can choose between two approaches.

**Single Portable Assembly** - With this approach, you will create a class library project that targets .NET Standard 1.3. The set of .NET api's that will be available are very limited, but in return you can produce a single binary that will work on all three runtimes. You should make every effort possible to utilize this approach.

**Dual Assemblies** - With this approach, you will create a class library project that targets both .NET Standard 2.0 and .NET Framework 4.6. You'll have access to all .NET api's, but your publishing process will be more complex. Building the plugin will produce two assemblies, one for .NET Standard 2.0, and one for .NET 4.6. The .NET Standard assembly will be used by Emby Server on .NET Core, while the .NET 4.6 assembly will be used by Emby Server on the .NET Framework and Mono.

## Create your Visual Studio Solution (VS 2017+)

1. Create a .NET Standard 1.3 class library project. 

2. Install the [Emby.Server.Core nuget package](https://www.nuget.org/packages/MediaBrowser.Server.Core/)

3. Create a class called PluginConfiguration, and have it inherit from MediaBrowser.Model.Plugins.BasePluginConfiguration.

4. Create a class called Plugin, and have it inherit from MediaBrowser.Common.Plugins.BasePlugin&lt;T&gt;, where T is the name of the PluginConfiguration class you just created.  You will need to implement its constructor like so:

> public Plugin(IApplicationPaths applicationPaths, IXmlSerializer xmlSerializer) : base(applicationPaths, xmlSerializer)

5. Create a random GUID using visual studio's Create Guid tool under the Tools menu. In Plugin.cs, override the Id property, and return the guid you just created. This will be the Id for the plugin and can never be changed.

**Important** - If migrating an existing plugin solution from Visual Studio 2015, then the plugin Id value should come from the AssemblyGuid located in AssemblyInfo.cs of your 2015 project.

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