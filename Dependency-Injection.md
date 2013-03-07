While you're building your classes for [automatic discovery](https://github.com/MediaBrowser/MediaBrowser/wiki/Automatic-Type-Discovery), many of these classes will require access to the core's internal services.

All you have to do is declare your a class's dependencies within it's constructor and we'll resolve them and pass in the appropriate instance.

The following services are available for insertion into your constructors:

### ILogManager 
Create your own named logger. Log entries will appear in the application log file and will be prefixed with the name of the logger for ease of reading.

### IServerApplicationPaths
Contains a list of various application data paths

### IServerConfigurationManager
Holds server configuration (and the above app paths)

### IIsoManager
Mounts and unmounts .iso files

### ITaskManager 
Manages scheduled tasks

### ILibraryManager 
Get information about the media library in a user-less fashion

### IUserManager
Get information about each user as well as their customized media libraries

### IBlurayExaminer
Get information about bluray folder structures

### IJsonSerializer
### IXmlSerializer
### IProtobufSerializer