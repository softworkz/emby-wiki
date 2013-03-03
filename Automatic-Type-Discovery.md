Media Browser will discover a number of Types in your plugin project automatically, without you having to do anything to wire them up. All you need to do is implement the appropriate interface and it will become part of the system.

The following interfaces are available for implementation:

### IServerEntryPoint

If you need to run initialization code at server start-up, implement this interface. The class will remain in memory for the lifetime of the server, so if you need to keep state, this is the place to put it. Keep in mind you can have as many of these as you need, allowing you to break larger plugins into smaller pieces.

### IRestfulService

Implement this interface to define your own API endpoint. A full guide for this is coming soon.

### IScheduledTask

Implement this interface to create a scheduled task that will appear in the Dashboard's Scheduled Tasks area. You'll define the default triggers that cause the task to run. The user will then be able to re-configure as desired, as well as run the task on demand.

### IIntroProvider

Intros are played before video files. Implement this interface to define your own provider for intro files.

### IPluginConfigurationPage

If your plugin requires an html configuration page within the Dashboard, implement this interface. A full guide for this is coming soon.

### IImageEnhancer

This interface will allow you to intercept image delivery through the api, if you wish to draw content over or otherwise enhance an image before it's written to the response stream.

### IResolverIgnoreRule

Implement this interface to create a rule allowing certain paths in the media library to be ignored. For example, the Video Backdrops plugin uses a "backdrops" folder within each Movie and Tv Series. It then implements IResolverIgnoreRule to prevent those folders from being displayed by Media Browser clients.

### IWeatherProvider

The server's default weather provider is WorldWeatherOnline.com, but plugins are free to create new ones by implementing this interface.

### IItemRepository, IUserRepository, IUserDataRepository, IDisplayPreferencesRepository

Media Browser uses a sqlite database to store application data. If there's a plugin developer who feels an alternate storage medium would be more appropriate, they are welcome to implement this interface and create their own.