After you have developed a plug-in for MediaBrowser, the next step is to get it into the catalog so users can install it.  Please be sure your plug-in adheres to our [Development Policy](Development-Policy) before placing it in the catalog.  It will be removed by an administrator if it violates this policy.

- First, request a developer id from the MB team by emailing admin AT mediabrowser3 DOT com or posting in the dev forum that you are ready to publish.

- Once you have your credentials you'll need to go to: http://www.mb3admin.com/admin/ and login with the user and password you were provided.

- Then go to the "Packages" area.  This is where you will define your plug-ins (as a user-installed package) and upload versions of them.

![Package Admin](http://www.mb3admin.com/images/packageadmin2.jpg)

Create a New Package to define your plug-in and fill in the fields appropriately.

![New Package](http://www.mb3admin.com/images/editpackage2.jpg)

- **Name** - The name that will appear for this plug-in in the catalog
- **GUID** - The Assembly unique id.  Paste this from your assemblyinfo.cs file.  It is used to identify this item for updates
- **Short Description** - A one line description of the plug-in
- **Overview** - A full description of the plug-in and its features.  This can be html.
- **Website** - A link to a developer website for more information.
- **Thumb Image** - This is the image that will be shown in the main catalog page.  It should be a 16x9 tile.
- **Preview Image** - This is the image that will show at the top of the catalog detail page for this item.  It can be a screen shot or other graphic.
- **Target System** - Select which system this plug-in is installed on (Server, MB Classic or MB Theater).
- **Package Type** - For plug-ins this should be "Userinstalled".
- **Cagegory** - Select the category of plug-in this is.
- **Tile Color** - This is the color for the background of the tile on the catalog page (behind the text).
- **Target File Name** - This is the name of the file that will be placed in the plugins folder on the target system when it is installed by the user.  It should be the name of your dll assembly including .dll.
- **Premium Plug-in** - Check this if users will be required to register this plug-in (pay for it).  All premium plug-ins will automatically have a 14-day free trial after first install.
- **Feature ID** - Enter the string that you will use to validate against for registration.
- **Price** - The price for registering this plug-in.  This full amount will be directed to your PayPal account.
- **Registration Information** - Optionally enter any additional information you would like to appear in the registration section on the plug-in detail page.

Once your package is defined, you can create and upload versions for them.  Expand the package by clicking the '>' next to it and click New Version.  Fill out the fields in this for with the appropriate information:

![Package Admin](http://www.mb3admin.com/images/editversion.jpg)

- **Version** - This is the full version number of this version of the plug-in.  Enter the exact version that will be reported from your dll via AssemblyInfo.
- **Version Class** - This is the update class of this version.  You can release different versions of your plug-ins as Dev, Beta or release classes.  Users will only see the ones for the level which they have set for this plug-in.
- **Description** - Enter details about this particular version.  Short bullets on what has changed or been fixed.  This information will display in the change log area of the catalog page.
- **Required Version** - Optionally enter a version number for the minimum supported version of the target system.  If this is a server plug-in, enter the server version, if for MBC, then the MBC version, etc.  The system will fill this in automatically with the latest version of the target system but you can change it.  It can also be a partial version to allow matches for anything above that partial.  e.g. 3.0.4890.

Then select the dll file from your local computer and save.  This will upload the dll and make it available in the plug-in catalog.