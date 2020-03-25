# jhonny-castaway-screensaver
Jhonny Castaway Screensaver for Linux Machines

This small project is inspired in https://github.com/graysky2/xscreensaver-aerial

## Dependencies
- coreutils
- mpv
- wget
- xscreensaver
- Jhonny Castaway Video (see instructions how to get [here](#download))

## Instalation

This was tested only in Ubuntu (and variations, like Mint)

1. Clone this repo, and copy the script `xscreensaver-johnny_castaway` to path: `/usr/lib/xscreensaver/xscreensaver-johnny_castaway`. Remember to check permissions. This file needs execution permission.

```sh
cp xscreensaver-johnny_castaway /usr/lib/xscreensaver/xscreensaver-johnny_castaway ; chmod +x usr/lib/xscreensaver/xscreensaver-johnny_castaway
```

2. Edit ~/.xscreensaver to add support for it to see this script. Look for the line that beings with "programs:" and simply add the following to the file:
```
xscreensaver-johnny_castaway		    \n\
```

## [Download Video](#download)
** This is a important step!! **

The screensaver needs a video file.
Get the video file with:
```sh
sudo mkdir -p /opt/jc
sudo wget https://storage.googleapis.com/jhonny-castway/jc.mkv -O /opt/jc/jc.mkv
```

This file was downloaded from [youtube](https://www.youtube.com/watch?v=-hPS_aQzueI) using [youtube-dl](https://youtube-dl.org/)
