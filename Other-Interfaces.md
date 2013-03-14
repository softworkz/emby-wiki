These are other interfaces that you can implement in your plug-in classes to implement their respective functionality.

##IRequiresRegistration

Implement this interface on your server entry point or any other class that needs to validate registration information.  There is one method in this interface:

     Task LoadRegistrationInfoAsync()

This method should be implemented to load a MBRegistrationRecord by using the PluginSecurityManager.GetRegistrationStatus call with the feature id that is to be validated.  You should always re-load the registration record whenever this method is invoked - even if the information was previously loaded - as this method will be called whenever the environment has changed such that registration should be re-evaluated.

###Example:
        public async Task LoadRegistrationInfoAsync()
        {
            Plugin.Instance.Registration = await PluginSecurityManager.GetRegistrationStatus("CoverArt4", "CoverArt3").ConfigureAwait(false);
        }
