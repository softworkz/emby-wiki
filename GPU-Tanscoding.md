**This is currently an experimental feature. If you experience any issues you should reverse any changes you make to your MediaBrowser set-up.**  
Please report any issues you experience on the [GPU transcoding thread](http://mediabrowser.tv/community/index.php?/topic/10723-gpu-transcoding/?view=getnewpost).
***
# Prerequesties
GPU transcoding is currently achieved only for h264 video streams using Intel QuickSync technology. h264 is the video codec used for many remote devices you might be streaming to, such as ChromeCast, Roku, Kodi and Smart TV's

At present the system requirements are:  
* [Intel processor that supports Intel QuickSync](http://ark.intel.com/search/advanced?s=t&QuickSyncVideo=true) (As a rough guide these are i3, i5 and i7 desktop chips as well as a few embedded chips - BayTrail)
* MediaBrowser Server running on Microsoft Windows(1)

# Enabling GPU transcoding

If you're ready to give GPU transcoding a try, then please follow these steps...

## 1) Switch to the development branch of Media Browser  
1. From the web administration console, choose **Advanced > General > Automatic updates > Dev (Unstable)**
2. Perform an automatic update of MediaBrowser to get the latest Dev version.

If you are running MediaBrowser as a system service, you will need to stop and restart the service in order for the update to be applied.

## 2) Edit the transcoding configuration file
1. From the web administration console, choose **Playback > Transcoding**
2. Now press **Save** - Press this even though you haven't changed anything (It will ensure the configuration is written to disk).
3. Open the file `%APPDATA%\MediaBrowser-Server\config\encoding.xml`(2)
4. Look for the line: `<H264Encoder>libx264</H264Encoder>`
5. Change it to: `<H264Encoder>h264_qsv</H264Encoder>`
6. Save the file

## 3) Grab an updated ffmpeg.exe
A new ffmpeg.exe which includes support for Intel QuickSync encoding is required. You can either build it yourself using [this build script](https://github.com/mjb2000/media-autobuild_suite) or [download the latest .exe release from here](https://github.com/mjb2000/media-autobuild_suite/releases).

Once you have built or downloaded a new ffmpeg.exe:

1. Open the folder `%APPDATA%\MediaBrowser-Server\ffmpeg`
2. Open the most recent dated folder (Folders are named YYYYMMDD)
3. Rename `ffmpeg.exe` to `ffmpeg.exe.original`
4. Copy your new ffmpeg in to this folder

**NOTE:** If you have MediaBrowser Server automatic updates enabled, then your new ffmpeg might get replaced. This doesn't happen with every new release, but if you notice a new folder date in your \ffmpeg folder then you'll need to re-replace your ffmpeg.exe with the QuickSync compatible version.

## 4) Restart MediaBrowser
Remember, if you are running MediaBrowser as a system service you will need to stop and restart the service.

## 5) Check the result
Use a device that will require transcoding(3) and take a look at the most recent log file in `%APPDATA%\MediaBrowser-Server\logs`  
Hopefully you will see an increase in your FPS, or at least a fall in your CPU usage. You can also use [GPU-Z](http://www.techpowerup.com/downloads/SysInfo/GPU-Z/) to see your GPU usage (you should see a spike in GPU usage when Intel QuickSync is used).
***
# Notes
1. Mixed results on Windows 8 - Currently when the transcode does not require a change of frame size (for example 1920x1080 -> 1920x1080) then the QuickSync output occasionally jumps back-and-forth. This is not the case when the frame size is resized (for example 1920x1080 -> 1280x720)
2. This file is located in you profile directory. For example if you Windows username is JohnSmith then your MediaBrowser installation directory is usually `C:\Users\JohnSmith\AppData\Roaming\MediaBrowser-Server`. You can use `%APPDATA%` as a shortcut to this folder - Pasting this shortcut in to Windows Explorer will take you straight to the AppData\Roaming folder.
3. If your bandwidth setting on your remote device is quite high and your source file already uses h264 video, then it's possible the source file won't be transcoded. Try lowering your client bandwidth and this should for transcoding to occur.