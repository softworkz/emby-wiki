Media Browser will discover a number of Types in your plugin project automatically, without you having to do anything to wire them up. All you need to do is implement the appropriate interface and it will become part of the system.

The following interfaces are available for implementation:

### IServerEntryPoint

If you need to run initialization code at server start-up, implement this interface. The class will remain in memory for the lifetime of the server, so if you need to keep state, this is the place to put it. Keep in mind you can have as many of these as you need, allowing you to break larger plugins into smaller pieces.

### IRestfulService

Implement this interface to define your own API endpoint. More info on this coming soon.

### IScheduledTask

Implement this interface to create a scheduled task that will appear in the Dashboard's Scheduled Tasks area. You'll define the default triggers that cause the task to run. The user will then be able to re-configure as desired, as well as run the task on demand.

### IIntroProvider

Intros are played before video files. Implement this interface to define your own provider for intro files.

### IPluginConfigurationPage

If your plugin requires an html configuration page within the Dashboard, implement this interface. A full guide for this is coming soon.

