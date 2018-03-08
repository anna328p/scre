# scre
Screenshot utility that mimics the usability of ShareX.

## What does it do?

When invoked, scre takes a screenshot, optionally processes it, uploads it to a server, then copies the URL to the clipboard.

## Dependencies

- GNU Bash
- GNU coreutils
- maim
- (By default) xdotool
- xclip
- OpenSSH or another provider of `scp`
- alsa-utils

## How to use

1. Clone the repo.
2. Configure scre by editing the file options.
3. Symlink scre to a location in your `$PATH`.
4. Bind to PrtScn or similar.

## Configuration

```bash
# Settings

# The path to store the screenshots locally.
localpath=~/Pictures

# The server that the images will be scp'd to.
server='user@server'

# The path on the server to put the images.
serverpath='/path/to/www/dir'

# Retrieve the name of the current active program.
program=$(xprop -id $(xdotool getactivewindow) | grep _NET_WM_NAME | cut -d'"' -f2|cut -d \n -f2)

# Format the date in your desired format.
date=$(date +'%Y-%m-%d_%H-%M-%S')

# The final filename that will be stored/copied.
filename="$program"-"$date".png

# The prefix to the URLs that the images will have when uploaded.
url_prefix="http://domain.tld/folder"

# The sound played after a successful upload.
sound=~/bin/TaskCompletedSound.wav
```
