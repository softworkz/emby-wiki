First install Media Browser Server, or download the code. Get the server up and running.

## Create your Visual Studio 2012 Solution

1. In your new project, go to Properties -> AssemblyInfo.cs. Change AssemblyVersion to "1.0.*" so that it auto-udpates, and remove the AssemblyFileVersion line altogether. This will keep both the assembly and file version numbers in sync.

2. Make sure AssemblyInfo.cs has a Guid, e.g. [assembly: Guid("{02CF7D91-16F4-48D4-BC97-16D89C16AA0A}")]. If not, copy this line and generate a new GUID using Tools -> Create Guid.

3. Install the [MediaBrowser.Server.Core nuget package](https://www.nuget.org/packages/MediaBrowser.Server.Core/)