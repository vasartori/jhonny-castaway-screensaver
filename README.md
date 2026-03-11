# Johnny Castaway Screensaver for Linux

This project provides a simple way to use the classic **Johnny Castaway** animation as a screensaver on Linux systems using **xscreensaver** and **mpv**.

The implementation is inspired by the approach used in the project:
https://github.com/graysky2/xscreensaver-aerial

Instead of rendering frames directly, the screensaver runs an `mpv` instance embedded inside the xscreensaver window and plays the Johnny Castaway animation video.

The script also selects a random start position in the video so the animation does not always begin from the same point.

## Dependencies

The following packages are required:

- coreutils
- mpv
- xscreensaver
- yt-dlp (used to download the videos)

## Compatibility

This screensaver works in **X11 environments**.

Modern Wayland-based desktop sessions (such as GNOME Wayland or KDE Wayland) do not support XScreenSaver.

If you want to use this project, make sure your session is running under X11.

## Installation

This was tested on Ubuntu and Ubuntu-based distributions (such as Linux Mint), but should work on most Linux systems using **xscreensaver**.

### 1. Install the screensaver script

Clone this repository and copy the script to the xscreensaver directory:

```bash
sudo cp xscreensaver-johnny_castaway /usr/libexec/xscreensaver/xscreensaver-johnny_castaway
sudo chmod +x /usr/libexec/xscreensaver/xscreensaver-johnny_castaway
```

Note: Some older documentation refers to `/usr/lib/xscreensaver/`, but on modern distributions the correct path is usually:

```
/usr/libexec/xscreensaver/
```

### 2. Register the screensaver in xscreensaver

Edit the file:

```
~/.xscreensaver
```

Locate the line that begins with:

```
programs:
```

Add the following entry:

```
xscreensaver-johnny_castaway    \n\
```

After restarting xscreensaver, the new screensaver should appear in the list.

## Downloading the Videos

The screensaver requires the Johnny Castaway animation video files.

Create the destination directory:

```bash
sudo mkdir -p /opt/jc
```

Then download the videos using **yt-dlp**:

```bash
sudo yt-dlp -o /opt/jc/jc.mp4 https://youtu.be/l8D6qppreiI
sudo yt-dlp -o /opt/jc/jc-xmas.mp4 https://youtu.be/yeFMQ-OK50A
```

These two videos correspond to:

- the regular Johnny Castaway animation
- a Christmas-themed version used during December

## Videos

You can find them here:

- https://youtu.be/l8D6qppreiI
- https://youtu.be/yeFMQ-OK50A

All credit for the original animation and video capture belongs to the respective creators.

## Notes

The script randomly chooses a starting timestamp in the video so that the animation appears continuous and does not always start from the same scene.

The Christmas version of the animation is automatically used during December.

The starting position in the video also depends on the current time of day:

- During the day (06:00–18:00), the script starts the video in segments corresponding to daytime scenes.
- During the night (18:00–06:00), the script starts the video in segments corresponding to nighttime scenes.

This behavior applies to both the regular Johnny Castaway animation and the Christmas version.

The script assumes that specific time ranges in the video correspond to day and night scenes and selects the starting timestamp accordingly.

If you are a Linux Mint user, follow [these steps](https://forums.linuxmint.com/viewtopic.php?f=42&t=284037) to get xscreensaver running.
