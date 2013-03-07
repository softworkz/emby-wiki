While you're building your classes for [automatic discovery](https://github.com/MediaBrowser/MediaBrowser/wiki/Automatic-Type-Discovery), many of these classes will require access to the core's internal services.

All you have to do is declare your a class's dependencies within it's constructor and we'll resolve them and pass in the appropriate instance.

The following services are available for insertion into your constructors:

* ILogManager - create your own named logger
* IServerApplicationPaths - contains a list of various application data paths
* IServerConfigurationManager - holds server configuration (and the above app paths)
* IIsoManager - mounts and unmounts .iso files
* ITaskManager - manages scheduled tasks
* ILibraryManager - get information about the media library, without respect to user
* IUserManager - get information about each user as well as their customized media libraries
* IBlurayExaminer - get information about bluray folder structures
* IJsonSerializer
* IXmlSerializer
* IProtobufSerializer