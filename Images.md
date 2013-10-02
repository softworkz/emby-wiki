Image values are added to response objects to indicate what images an item has. For example, on the User object, there is a property called PrimaryImageTag. If this has a value, it means the user has a primary image.

An image should only downloaded if the object indicates the presence of an image. For example, you will receive a 404 error if you attempt to download a logo image for an item that doesn't have one.

## Downloading images

The url required to download images will vary depending on what kind of item you're downloading for. For example, for users, the url's are /Users/{Id}/Images/{Type} and /Users/{Id}/Images/{Type}/{Index}. For media items, it's /Items/{Id}/Images/{Type}, as well as /Items/{Id}/Images/{Type}/{Index}

Below are the **required** image parameters:

### Type
This is the type of image. These are the available types:

* Primary
* Art
* Backdrop
* Banner
* Logo
* Thumb
* Disc
* Box
* Screenshot
* Menu
* Chapter

### Index
If downloading a backdrop, screenshot, or chapter image, you will need to specify the index because the item could contain more than one. The item object will contain count properties indicating how many of each are available.

Aside from item Id, the image type is the only other required parameter. Index is required depending on the type of image requested. 

Below are the available **optional** parameters:

### Width, Height, MaxWidth, MaxHeight
Users will often download high resolution images. Steps should be taken to ensure that you are not retrieving these at full size. You can use any combination of these values. For example, if you specify a width of 80, you'll get the image at a fixed width of 80 and allow the height to vary, preserving aspect ratio. Specify both width and height to force an exact size. Specify MaxWidth and/or MaxHeight to create a size limit.

Most image types generally have a predictable aspect ratio. Primary is the one exception where it can vary. In order to combat this, we include a PrimaryImageAspectRatio property on items. A typical scenario might be to create an average AR for all the items in the list, and then force all images to that value.

### Tag
The image tag on the item object also doubles as a caching value. If you add this parameter back onto your image url, you will receive strong http caching headers. This allows you to cache the image forever, unconditionally, based on the url. If the image changes, the tag will also change, thus creating a whole new url.

This is an optional parameter. You do not have to specify the tag, but without it you will only receive conditional http response caching.

## Image Inheritance
We allow some images to be inherited from parent items, namely backdrops and logos.

If an item does not have backdrops or logos, there are properties that will indicate what parent images are available for inheritance:

* ParentLogoItemId - The id of an ancestor item with a logo
* ParentLogoImageTag - The cache tag of the ancestor logo image
* ParentArtItemId - The id of an ancestor item with an art image
* ParentArtImageTag - The cache tag of the ancestor art image
* ParentBackdropItemId - The id of an ancestor item with backdrop images
* ParentBackdropImageTags - The cache tags of the ancestor backdrop images

## Image Format

By default, images are returned in the original format, which generally will be either png or jpg. If the user has image enhancer plugins installed such as Cover Art, the default output format will be forced to png.

If a specific output format is needed, this can be controlled using the **format param**. Available values are:

* bmp
* gif
* jpp
* png

If forcing to jpg it's possible that some transparency will be lost. It's recommended to apply a background color of your choosing using the **backgroundColor param**, which accepts html color values, such as #000000 or red.

## Adding a Played Indicator

A played indicator overlay can be added onto the image using **AddPlayedIndicator=true**

## Adding a Percent Played Indicator

A percent played overlay can be added onto the image using **PercentPlayed=47**