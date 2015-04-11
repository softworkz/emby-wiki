![GPU Trnascoding](http://emby.media/community/uploads/inline/5895/54b7997749d17_GPU.jpg)
![Intel nVidia](http://emby.media/community/uploads/inline/5895/54b799cd222e3_IntelNvidia.jpg)

**This is currently an experimental feature. If you experience any issues you should reverse any changes you make to your Emby set-up.**  
Please report any issues you experience on the [GPU transcoding thread](http://emby.media/community/index.php?/topic/10723-gpu-transcoding/?view=getnewpost).
***
# Scope
GPU transcoding is currently achieved only for h264 video streams using either **Intel QuickSync or nVidia NVENC** technology. h264 is the video codec used for many remote devices you might be streaming to, such as ChromeCast, Roku, Kodi and Smart TV's. 

Emby also uses libvpx to encode video (webm format) for HTML5 devices. It is not currently possible to use GPU acceleration for libvpx.

# Prerequesties
At present the system requirements are:  
* [Intel processor that supports Intel QuickSync](http://ark.intel.com/search/advanced?s=t&QuickSyncVideo=true) (As a rough guide these are i3, i5 and i7 desktop chips as well as a few embedded chips - BayTrail)
* -or-
* [nVidia graphics card that support NVENC](https://developer.nvidia.com/nvidia-video-codec-sdk#gpulist) (These are the Kepler and Maxwell based GPUs - there are high-end and desktop variants of these cards(4))
* Emby Server running on Microsoft Windows(1)

## Latest drivers
Nearly all issues reported on the forum have been resolved by ensuring the latest drivers are used. 
* For desktops, check for the latest drivers from Intel and nVidia.
* For laptops, you will need to get the driver from your laptop manufacturer.

Don't rely on automatic driver update tools, there have been reports on these failing to obtain the latest driver for the GPU.

# Enabling GPU transcoding

If you're ready to give GPU transcoding a try, then please follow these steps...

**Please note:** The current Dev release of Emby does not contain some tweaks to the code necessary for QuickSync to run reliably. For now you may be able to undertake some initial testing, but you may experience issues unless you build Emby yourself from [my fork of the code](https://github.com/mjb2000/MediaBrowser) or replace your [MediaBrowser.Api.Dll with my version](https://github.com/mjb2000/MediaBrowser/releases/download/3.0.5508.29225/MediaBrowser.Api.dll). **DLL for MB Dev v3.0.5508.29225**

## 1) Switch to the development branch of Emby  
1. From the web administration console, choose **Advanced > General > Automatic updates > Dev (Unstable)**
2. Perform an automatic update of Emby to get the latest Dev version.

If you are running Emby as a system service, you will need to stop and restart the service in order for the update to be applied.

## 2) Edit the transcoding configuration file
1. From the web administration console, choose **Playback > Transcoding**
2. Now press **Save** - Press this even though you haven't changed anything (It will ensure the configuration is written to disk).
3. Open the file `%APPDATA%\MediaBrowser-Server\config\encoding.xml`(2)
4. Look for the line: `<H264Encoder>libx264</H264Encoder>`
5. For Intel Quicksync change it to: `<H264Encoder>h264_qsv</H264Encoder>`
6. For nVidia NVENC change it to: `<H264Encoder>libnvenc</H264Encoder>`
7. Save the file

## 3) Grab an updated ffmpeg.exe
A new ffmpeg.exe which includes support for Intel QuickSync and nVidia NVENC encoding is required. You can either build it yourself using [this build script](https://github.com/mjb2000/media-autobuild_suite) or [download the latest .exe release from here](https://github.com/mjb2000/FFmpeg/releases/download/n2.5-dev/ffmpeg.exe).

Once you have built or downloaded a new ffmpeg.exe:

1. Open the folder `%APPDATA%\MediaBrowser-Server\ffmpeg`
2. Open the most recent dated folder (Folders are named YYYYMMDD)
3. Rename `ffmpeg.exe` to `ffmpeg.exe.original`
4. Copy your new ffmpeg in to this folder

**NOTE:** If you have Emby Server automatic updates enabled, then your new ffmpeg might get replaced. This doesn't happen with every new release, but if you notice a new folder date in your \ffmpeg folder then you'll need to re-replace your ffmpeg.exe with the QuickSync compatible version.

## 4) Restart Emby
Remember, if you are running Emby as a system service you will need to stop and restart the service.

## 5) Check the result
Use a device that will require transcoding(3) and take a look at the most recent log file in `%APPDATA%\MediaBrowser-Server\logs`  
Hopefully you will see an increase in your FPS, or at least a fall in your CPU usage. You can also use [GPU-Z](http://www.techpowerup.com/downloads/SysInfo/GPU-Z/) to see your GPU usage (you should see a spike in GPU usage when Intel QuickSync is used).

## 6) Allowing updates
**This is an optional step that you might want to take if you have been able to get GPU transcoding working successfully using the steps listed above.**

By default, when Emby is updated, it will also update the ffmpeg.exe - this will remove the GPU enabled version you have added. To prevent this...

* Create the following folder `%APPDATA%\MediaBrowser-Server\ffmpeg\gpu` (This new  'GPU' folder should be alongside the original date-based folder)
* Download both [ffmpeg.exe](https://github.com/mjb2000/FFmpeg/releases/download/n2.5-dev/ffmpeg.exe) and [ffprobe.exe](https://github.com/mjb2000/FFmpeg/releases/download/n2.5-dev/ffprobe.exe) in to this new GPU folder.
* Edit your Emby Server shortcut.
  * Change the 'ImagePath':Change the 'Trarget':
     * From: `C:\Users\MY_USER_NAME\AppData\Roaming\MediaBrowser-Server\System\MediaBrowser.ServerApplication.exe`
     * To: `C:\Users\MY_USER_NAME\AppData\Roaming\MediaBrowser-Server\System\MediaBrowser.ServerApplication.exe -ffmpeg "C:\Users\MY_USER_NAME\AppData\Roaming\MediaBrowser-Server\ffmpeg\gpu\ffmpeg.exe" -ffprobe "C:\Users\MY_USER_NAME\AppData\Roaming\MediaBrowser-Server\ffmpeg\gpu\ffprobe.exe"`
* Edit your MediaBroser Server Windows Service.
  * Open RegEdit and navigate to 
  * Change the 'ImagePath':
     * From: `"C:\Users\MY_USER_NAME\AppData\Roaming\MediaBrowser-Server\system\MediaBrowser.ServerApplication.exe" -service`
     * To: `"C:\Users\MY_USER_NAME\AppData\Roaming\MediaBrowser-Server\system\MediaBrowser.ServerApplication.exe" -service -ffmpeg "C:\Users\MY_USER_NAME\AppData\Roaming\MediaBrowser-Server\ffmpeg\gpu\ffmpeg.exe" -ffprobe "C:\Users\MY_USER_NAME\AppData\Roaming\MediaBrowser-Server\ffmpeg\gpu\ffprobe.exe"`

These updates allow you to use a custom location for ffmpeg. Since you are using a customer ffmpeg, Emby will not download a replacement version.

**REMEMBER: At the moment, we are using a custom version of MediaBrowser.Api.Dll as well as ffmpeg. This solution prevents your ffmpeg.exe being overwritten, but WILL NOT prevent the .Dll being overwritten. It is likely that the requirement for a separate .Dll will only be short-term, although the overwriting of ffmpeg.exe is likely to be a long-term issue, hence these tweaks should be useful**

***

# Notes
1. Mixed results with QuickSync on Windows 8 - Currently when the transcode does not require a change of frame size (for example 1920x1080 -> 1920x1080) then the QuickSync output occasionally jumps back-and-forth. This is not the case when the frame size is resized (for example 1920x1080 -> 1280x720)
2. This file is located in your profile directory. For example if your Windows username is JohnSmith then your Emby installation directory is usually `C:\Users\JohnSmith\AppData\Roaming\MediaBrowser-Server`. You can use `%APPDATA%` as a shortcut to this folder - Pasting this shortcut in to Windows Explorer will take you straight to the AppData\Roaming folder.
3. If your bandwidth setting on your remote device is quite high and your source file already uses h264 video, then it's possible the source file won't be transcoded. Try lowering your client bandwidth and this should for transcoding to occur.
4. nVidia desktop graphics cards (GeForce) have a maximum of two hardware encoding sessions