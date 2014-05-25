Lapse
=====

Convert still photos from a GoPro camera into a video file.  This is useful for
stop motion or time lapse photography.

This script works with the filenames produced by a GoPro camera, which look like
this:

    G0010076.JPG
    G0010077.JPG
    G0010078.JPG

If your photos use a different naming scheme, you'll have to edit that line in
the script to make it work.

Invoke the script by giving it the source and target directories.  For example,
I might type this:

~~~ sh
lapse /Volumes/SD64A/DCIM ~/Movies/Lapse
~~~

...where the name of my SD card is "SD64A" (it's 64 GB, and I have two of them),
and I keep my time lapses in a directory called "Lapse".

The script combines each subdirectory of DCIM into one video file, then
concatenates them into one huge file.

You will need a bunch of free storage to do this.  The resulting video files are
about 2/3 the size of the still photos.  If you have 64 GB of 5 megapixel
stills, you will need perhaps 90 GB for the video files.  (You can delete half
of this once the script has finished running.)

That's not even at the highest quality level, which you can adjust.  You can
choose a value from 0-3 inclusive.  The default is 2.  You can adjust it like
so:

~~~ sh
lapse /Volumes/SD64A/DCIM ~/Movies/Lapse 3
~~~

The bigger the number, the bigger the video's file size, and the higher the
quality.  The final output is a ProRes video file.  Converting to H.264 (or
whatever you're into) requires further processing.

I then import the resulting video file into iMovie or Final Cut Pro.  The
entire purpose of this script is to replace GoPro Cineform Studio with a
shell command, at least for this one task.

## Compatibility

Debian and Ubuntu (among others) ship with a fork of FFMPEG called Libav.  You
will need to either install FFMPEG, or use avconv (and therefore a modified or
entirely different wrapper script) instead.

## Installation on Mac OS X

This script uses FFMPEG to do the heavy lifting.  To install FFMPEG on Mac OS X
with Homebrew, enter this in the Terminal app:

~~~ sh
brew install ffmpeg --devel
~~~

The "--devel" flag gets you the latest version, which is faster.  More info here:
https://trac.ffmpeg.org/wiki/CompilationGuide/MacOSX

### Legal

All trademarks (such as GoPro, Cineform Studio, iMovie, and Final Cut Pro)
belong to their respective owners.
