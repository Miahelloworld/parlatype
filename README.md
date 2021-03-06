# Parlatype

For a screenshot, an overview what Parlatype actually is and packages please visit https://www.parlatype.org.

The following instructions are for developers, contributors and those who want to have the latest version from the master branch.

## Build from source

### Dependencies

To build Parlatype from source you need these packages:
* meson >= 0.47.2 (older versions not tested)
* gettext >= 0.19.7
* gobject-introspection-1.0
* yelp-tools
* gtk+-3.0 >= 3.22
* gstreamer-1.0 >= 1.6.3
* gstreamer-plugins-base-1.0
* sphinxbase
* pocketsphinx

Optional, depending on your configure options:
* gladeui-2.0 (>= 3.12.2; with `glade=true`)
* gtk-doc (with `gtk-doc=true`)
* desktop-file-utils (if installed, this checks the desktop file)
* appstream-utils (if installed, this checks the appstream file)

Runtime dependencies:
* GStreamer "Good" Plugins
* If you need MP3 support for GStreamer versions older than 1.14, you have to install the "Ugly" Plugins.

Debian based distros have to be Debian >= 9 (Stretch) or Ubuntu >= 18.04 (Bionic). On Debian Stretch meson must be installed from backports. Install these packages:

```
$ sudo apt-get install meson build-essential libgirepository1.0-dev libgladeui-dev gtk-doc-tools yelp-tools libgtk-3-dev libgtk-3-0 libgstreamer1.0-dev libgstreamer1.0-0 libgstreamer-plugins-base1.0-dev gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly libatspi2.0-dev libsphinxbase-dev libpocketsphinx-dev
```
On Fedora this should work:

```
$ su -c 'dnf install meson gcc gobject-introspection-devel glade-devel gtk-doc yelp-tools gtk3-devel gstreamer1-devel gstreamer1-plugins-base-devel gstreamer1-plugins-good gstreamer1-plugins-ugly at-spi2-core-devel sphinxbase-devel pocketsphinx-devel'
```

### Configure options

Parlatype ships its own library, libparlatype. Developers might be interested in having a library documentation, gobject introspection and a glade catalog for the widgets. These are the configure options:

* `asr`: build with automatic speech recognition, requires sphinxbase and pocketsphinx (default: true)
* `gir`: install gobject introspection (default: false)
* `gtk-doc`: install library documentation (default: false)
* `glade`: install a glade catalog (default: false)

### Build from git
Clone the repository and build with meson. You can use any prefix but you may have to adjust LD_LIBRARY_PATH for other prefixes. In this case Meson prints a message with those paths.
```
$ git clone https://github.com/gkarsay/parlatype.git
$ cd parlatype
$ meson build --prefix=/usr
$ cd build
$ ninja
$ sudo ninja install
```

### Build from tarball
Download the latest release tarball from https://github.com/gkarsay/parlatype/releases/latest. Assuming it’s version 2.1 and you want the program only:
```
$ wget https://github.com/gkarsay/parlatype/releases/download/v2.1/parlatype-2.1.tar.gz
$ tar -zxvf parlatype-2.1.tar.gz
$ cd parlatype-2.1/
$ meson build --prefix=/usr
$ cd build
$ ninja
$ sudo ninja install
```

## Bugs
Please report bugs at https://github.com/gkarsay/parlatype/issues.
