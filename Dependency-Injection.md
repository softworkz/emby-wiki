While you're building your classes for [automatic discovery](https://github.com/MediaBrowser/MediaBrowser/wiki/Automatic-Type-Discovery), many of these classes will require access to the core's internal services.

All you have to do is declare your a class's dependencies within it's constructor and we'll resolve them and pass in the appropriate instance.

The following services are available for insertion into your constructors: