# Parlatype

## What is it?

Parlatype is a minimal audio player for manual speech transcription, written for the GNOME desktop environment. It plays audio sources to transcribe them in your favourite text application.

![alt text](help/C/figures/parlatype-main-window.png "Parlatype")

 You can control the speed of playback, playing slowly as you type, playing fast for editing. The pitch is not altered, there is no “chipmunk” effect. Whenever you pause playback, it will rewind a few seconds, so that you can easier resume. Of course you can change how much it rewinds or whether it rewinds at all.

Parlatype can start on top of other windows. If you are working with a maximized text application, you can still see the Parlatype window.

![alt text](help/C/figures/parlatype-prefs-waveform.png "Parlatype Preferences")
![alt text](help/C/figures/parlatype-prefs-controls.png "Parlatype Preferences")
![alt text](help/C/figures/parlatype-prefs-window.png "Parlatype Preferences")

Parlatype can be controlled with the “Play” button from your multimedia keyboard. This way it doesn’t have to have focus to control it. You can type in your text application and still have some (basic) control over Parlatype.

A powerful feature of Parlatype is a set of LibreOffice helpers (macros). For example you can insert a time stamp into your document with a shortcut of your choice. If you put the cursor on such a time stamp and use another shortcut, Parlatype will jump to that position.


## What it’s not

Parlatype is just an audio player, you still need another program, where you write your transcription to, e.g. LibreOffice. It doesn’t work with videos or streaming media. It’s not a tool for scientific transcription, rather for your personal use. There is no speech recognition, you have to type yourself.

## Translations

Parlatype is translated at [Launchpad](https://translations.launchpad.net/parlatype). Currently there is an English and a German version. Any help in translations is welcome!

## Installation

### Packages

* Ubuntu: There is a PPA with stable releases of Parlatype at [Launchpad](https://launchpad.net/~gabor-karsay/+archive/ubuntu/parlatype).
* Debian: At [GitHub](https://github.com/gkarsay/parlatype/releases) you’ll find packages to download for Debian 8 “Jessie”.

### Dependencies

To install Parlatype from source you need these packages: make, autotools, intltool, gobject-introspection-1.0, gladeui-2.0, gtk-doc-tools, yelp-tools and finally gtk+-3.0 (minimum version 3.10) and gstreamer-1.0 with base plugins.

On a Debian based distro you can install these with:

```
$ sudo apt-get install build-essential automake autoconf intltool libgirepository1.0-dev libgladeui-dev gtk-doc-tools yelp-tools libgtk-3-dev libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
```

In order to run it needs at least Gtk+ 3.10 and GStreamer 1.0 with the set of “good” plugins.
The Debian based command is (but you probably have them already):
```
$ sudo apt-get install libgtk-3-0 libgstreamer1.0-0 gstreamer1.0-plugins-good
```

### Building 

#### Configure options
* --enable-gtk-doc: install library documentation (default: no)
* --enable-introspection: install gobject introspection (default: yes)
* --enable-glade-catalog: install a glade catalog (default: no)
* --with-lo: install LibreOffice macros (default: yes)

#### From git
Clone the repository and run autogen.sh. Assuming you want the program only:
```
$ git clone https://github.com/gkarsay/parlatype.git
$ cd parlatype
$ ./autogen.sh --prefix=/usr --disable-introspection
$ make
$ sudo make install
```

#### From tarball
Download a release tarball, extract it and run:
```
$ autoreconf # might be necessary
$ ./configure --prefix=/usr --disable-introspection
$ make
$ sudo make install
```

### LibreOffice helpers
The LibreOffice helpers/macros are installed together with Parlatype. However, this works only fine with --prefix=/usr. If you use a different prefix, it’s recommended to
```
$ ./configure --without-lo
```
In this case, please copy the macros manually:
```
$ sudo cp libreoffice/Parlatype.py /usr/lib/libreoffice/share/Scripts/python/
```
If you don’t want to install them system-wide, you can put them in your home dir instead:
```
$ cp libreoffice/Parlatype.py ~/.config/libreoffice/4/user/Scripts/python/
```
There is an integrated help in Parlatype with a page describing how to use the LibreOffice helpers.

## Credits

The idea and initial design of Parlatype is based on Frederik Elwert’s program *transcribe*.

The display of the audio wave form started with code from *Buzztrax*.

The icon is based on work from the GNOME team.
