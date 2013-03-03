Media Browser will discover a number of Types in your plugin project automatically, without you having to do anything to wire them up. All you need to do is implement the interface and it will become part of the system.

The following interfaces are available for implementation:

### IScheduledTask

Implement this interface to create a scheduled task that will appear in the Dashboard's Scheduled Tasks page. You'll define the default triggers which cause the task to run. The user will then be able to reconfigure as desired, as well as run the task on demand.