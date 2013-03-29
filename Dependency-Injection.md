While you're building your classes for [automatic discovery](https://github.com/MediaBrowser/MediaBrowser/wiki/Automatic-Type-Discovery), many of these classes will require access to the core's internal services.

If your class depends on one of our services, all you have to do is add it to your constructor and an instance will be passed in that you can work with.

The following services are available for insertion into your constructors:

### ILogManager 
Create your own named logger. Log entries will appear in the application log file and will be prefixed with the name of the logger for ease of reading.

### IServerApplicationPaths
Contains a list of various application data paths

### IServerConfigurationManager
Read and write server configuration data (and the above app paths)

### IJsonSerializer
Get access to the core's json serializer.

### IXmlSerializer
Get access to the core's xml serializer.

### IProtobufSerializer
Get access to the core's protobuf serializer.

### ITaskManager 
Queue, execute and cancel scheduled tasks

### ILibraryManager 
Get information about the media library in a user-less fashion

### IUserManager
Get information about each user as well as their customized media libraries

### IBlurayExaminer
Get information about bluray folder structures

### IIsoManager
Mounts and unmounts iso files
