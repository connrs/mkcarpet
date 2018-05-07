# mkcarpet

My idea was to make a bash script that takes a URL to a Carpet server release from Scicraft's mods channel and to be able to pass it as a parameter to a bash script. That script will then:

* Check if you already have a cached copy of 1.12 server (if you don't then it will download it to ~/.mkcarpet)
* Check if it can unzip/unrar the path that you've provided
* Check if it's a URL (if it spots http(s) it assumes a URL and otherwise defaults to a local path)
* Downloads the URL to a temp directory
* Creates a temporary output directory
* Unpacks the server in to it
* Unpacks the Carpet release in to the output directory
* Zips it back up
* Gives it a .jar extension
* Moves it to your specified output directory

## Usage:

mkcarpet carpetpathurl outputdir

**carpetpathurl**: This is the HTTP(S) URL to a Carpet release or a local file path to a pre-downloaded .zip or .rar file
**outputdir**: This is the directory you'd like the final Carpet release to be moved to.

## Installation

* Download mkcarpet to your machine.
* Make it executable: `chmod +x mkcarpet`
* Use it (if mkcarpet isn't in your executable path): `/full/path/to/mkcarpet https://example.com/Carpet_v42_42_42.zip .`
* Use if (if you moved mkcarpet to /usr/local/bin or /usr/bin or in your path): `mkcarpet https://example.com/Carpet_v42_42_42.rar`

## Caveats/Warnings

I've set it to exit immediately on any unexpected errors and I've set it to output useful debugging info when it's running. If
it exits in a random spot then the last line of logging may help identify how far the process reached and could be used to fix
bugs in this script or make improvements.

In an ideal world, everyone's machine would already have all the packages that you need to use this little bashscript. If the
carpet releases are always a .zip file then there's a good chance that a Mac or Linux machine will already have the following
binaries installed:

* `curl`
* `unzip`
* `zip`

If the carpet release is a .rar file then you may need to check that you have an `unrar` binary installed. On a Debian/Ubuntu
based system this may need you to run `sudo apt-get install unrar-free` in a terminal. On Red Hat/Fedora based systems you may
need to have the EPEL yum repo activated and I suspect that `sudo yum install unrar` will work for you. On a mac you will likely
need to install [homebrew](https://brew.sh/).

## Fixes

I've tried to comment this as well as possible but I'd welcome any suggestions. If there's a way to make the code clearer to read
or if there's a comment that needs some tweaking to be easier to understand then do fire any feedback my way. I'm in full time
work with a family so apologies in advance if I'm a little slow to resolve things.

You're welcome to make your own adjustments and to fork this and steal this. For those who prefer to have an explicit OSS licence
I've opted to use the Unlicense so that it's clear it's free to use and tweak.
