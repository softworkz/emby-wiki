Image values are added to response Dto's to indicate an item has images. For example, on the User object, there is a property called PrimaryImageTag. If this has a value, it means the user has a primary image.

An image should only downloaded if the object indicates the presence of an image. For example, you will receive a 404 error if you attempt to download a logo image for an item that doesn't have one.

## Downloading images

The url required to download images will vary depending on what kind of item you're downloading for. For example, for users, the url's are /Users/{Id}/Images/{Type} and /Users/{Id}/Images/{Type}/{Index}. For media items, it's /Items/{Id}/Images/{Type}, as well as /Items/{Id}/Images/{Type}/{Index}

Below are the required and optional image parameters:

### Type
This is the type of image. These are the available types:

        Primary,
        Art,
        Backdrop,
        Banner,
        Logo,
        Thumb,
        Disc,
        Box,
        Screenshot,
        Menu,
        ChapterImage