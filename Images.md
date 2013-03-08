Image values are added to response Dto's to indicate what images an item has. For example, on the User object, there is a property called PrimaryImageTag. If this has a value, it means the user has a primary image.

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
* ChapterImage

### Index
If downloading a backdrop, screenshot, or chapter image, you will need to specify the index because the item could contain more than one. The item object will contain count properties indicating how many of each are available.

Aside from item Id, the image type is the only other required parameters. Index is required depending on the type of image requested. Below are the available **optional** parameters:

### Width, Height, MaxWidth, MaxHeight
Users will often download high resolution images. Steps should be taken to ensure that you are not downloading these at full size. You can use any combination of these values. For example, if you specify a width of 80, you'll get the image at that fixed width and allow the height to vary, preserving aspect ratio. Specify both width and height to force an exact size. Specify max width and/or max height to create a size limit.

Most image types generally have a predictable aspect ratio. Primary is the one exception where it can vary. In order to combat this, we include a PrimaryImageAspectRatio property on items. A typical scenario might be to create an average AR for all the items in the list, and then force all images to that value.

### Tag
The image tag on the item object also doubles as a caching value. If you add this parameter back onto your image url, you will receive strong http caching headers. This allows you to cache the image forever, unconditionally. If the image changes, the tag will also change, thus creating a whole new url.

This is an optional parameter. You do not have to specify the tag, but without it you will only receive conditional http response caching.
