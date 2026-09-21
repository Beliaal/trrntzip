# TorrentZip

This project tries to enhance the code of the [original
trrntzip](https://sourceforge.net/projects/trrntzip/) implementation
for modern systems.

Torrentzip converts zip archives to a standard format with some
pre-defined values, sorting the files, and using particular
compression settings so that running it on zip archives created by
other tools will always result in the same output. This helps
e.g. with sharing zip archives using
[BitTorrent](https://www.bittorrent.org) (which is where the name
comes from).

# Installation

## Requirements

* A C compiler (e.g. gcc or clang)
* [zlib](http://zlib.net/) (at least version 1.2.2)
* [zstd](https://facebook.github.io/zstd/) (libzstd-dev)
* [CMake](https://cmake.org/) (at least version 3.12)

## Building

* mkdir build
* cd build
* cmake ..
* make
* make install

## Building static

Make sure the static versions of zlib and zstd are installed. On Debian/Ubuntu, for example:

```bash
sudo apt install zlib1g-dev libzstd-dev
```

To locate the static libraries:

```bash
find /usr /usr/local -type f \( -name 'libz.a' -o -name 'libzstd.a' \) 2>/dev/null
```

On a typical x86-64 Debian/Ubuntu system they are located at:

```text
/usr/lib/x86_64-linux-gnu/libz.a
/usr/lib/x86_64-linux-gnu/libzstd.a
```

Then build with:

```bash
mkdir build
cd build

cmake .. \
    -DZLIB_LIBRARY=/usr/lib/x86_64-linux-gnu/libz.a \
    -DZLIB_INCLUDE_DIR=/usr/include \
    -DZSTD_LIBRARY=/usr/lib/x86_64-linux-gnu/libzstd.a \
    -DCMAKE_EXE_LINKER_FLAGS="-static"

make
make install
```

# Packages

* [Gentoo](https://github.com/gentoo/gentoo/tree/master/app-arch/torrentzip)
* [pkgsrc](https://github.com/NetBSD/pkgsrc/tree/trunk/archivers/trrntzip)

# Status

[![build](https://github.com/0-wiz-0/trrntzip/actions/workflows/build.yml/badge.svg)](https://github.com/0-wiz-0/trrntzip/actions/workflows/build.yml)
