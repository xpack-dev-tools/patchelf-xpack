---
title:  xPack NixOS PatchELF v{{ XBB_RELEASE_VERSION }} released

TODO: select one summary

summary: "Version **{{ XBB_RELEASE_VERSION }}** is a maintenance release; it fixes <...>."

summary: "Version **{{ XBB_RELEASE_VERSION }}** is a new release; it follows the upstream release."

patchelf_version: "0.17.2"
patchelf_date: "10 Jan 2022"

version: "{{ XBB_RELEASE_VERSION }}"
npm_subversion: "1"

download_url: https://github.com/xpack-dev-tools/patchelf-xpack/releases/tag/v{{ XBB_RELEASE_VERSION }}/

comments: true

date:   {{ RELEASE_DATE }}

# For Jekyll releases selection.
categories:
  - releases
  - patchelf

# For navigation; use scripts/createtag.sh in Jekyll.
tags:
  - releases
  - patchelf

---

[The xPack NixOS PatchELF](https://xpack.github.io/patchelf/)
is a standalone cross-platform binary distribution of
[NixOS PatchELF](https://github.com/NixOS/patchelf/).

There are separate binaries for
**macOS** (Intel 64-bit, Apple Silicon 64-bit)
and **GNU/Linux** (Intel 64-bit, Arm 32/64-bit).

{% raw %}{% include note.html content="The main targets for the Arm binaries
are the **Raspberry Pi** class devices (armv7l and aarch64;
armv6 is not supported)." %}{% endraw %}

## Download

The binary files are available from GitHub [Releases]({% raw %}{{ page.download_url }}{% endraw %}).

## Prerequisites

- GNU/Linux Intel 64-bit: any system with **GLIBC 2.27** or higher
  (like Ubuntu 18 or later, Debian 10 or later, RedHat 8 later,
  Fedora 29 or later, etc)
- GNU/Linux Arm 32/64-bit: any system with **GLIBC 2.27** or higher
  (like Raspberry Pi OS, Ubuntu 18 or later, Debian 10 or later, RedHat 8 later,
  Fedora 29 or later, etc)
- Intel macOS 64-bit: 10.13 or later
- Apple Silicon macOS 64-bit: 11.6 or later

## Install

The full details of installing the **xPack NixOS PatchELF** on various platforms
are presented in the separate
[Install]({% raw %}{{ site.baseurl }}{% endraw %}/dev-tools/patchelf/install/) page.

### Easy install

The easiest way to install NixOS PatchELF is with
[`xpm`]({% raw %}{{ site.baseurl }}{% endraw %}/xpm/)
by using the **binary xPack**, available as
[`@xpack-dev-tools/patchelf`](https://www.npmjs.com/package/@xpack-dev-tools/patchelf)
from the [`npmjs.com`](https://www.npmjs.com) registry.

With the `xpm` tool available, installing
the latest version of the package and adding it as
a development dependency for a project is quite easy:

```sh
cd my-project
xpm init # Add a package.json if not already present

xpm install @xpack-dev-tools/patchelf@latest --verbose

ls -l xpacks/.bin
```

To install this specific version, use:

```sh
xpm install @xpack-dev-tools/patchelf@{% raw %}{{ page.version }}.{{ page.npm_subversion }}{% endraw %} --verbose
```

It is also possible to install Meson Build globally, in the user home folder,
but this requires xPack aware tools to automatically identify them and
manage paths.

```sh
xpm install --global @xpack-dev-tools/patchelf@latest --verbose
```

### Uninstall

To remove the links created by xpm in the current project:

```sh
cd my-project

xpm uninstall @xpack-dev-tools/patchelf
```

To completely remove the package from the central xPack store:

```sh
xpm uninstall --global @xpack-dev-tools/patchelf
```

## Compliance

The xPack NixOS PatchELF generally follows the official
[NixOS PatchELF](https://github.com/NixOS/patchelf) releases.

The current version is based on:

- NixOS PatchELF version {% raw %}{{ page.patchelf_version }}{% endraw %}
from {% raw %}{{ page.patchelf_date }}{% endraw %}.

## Changes

Compared to the upstream version, there are no functional changes.

## Bug fixes

- none

## Enhancements

- none

## Known problems

- none

## Shared libraries

On all platforms the packages are standalone, and expect only the standard
runtime to be present on the host.

All dependencies that are build as shared libraries are copied locally
in the `libexec` folder (or in the same folder as the executable for Windows).

### `DT_RPATH` and `LD_LIBRARY_PATH`

On GNU/Linux the binaries are adjusted to use a relative path:

```console
$ readelf -d library.so | grep runpath
 0x000000000000001d (RPATH)            Library rpath: [$ORIGIN]
```

In the GNU ld.so search strategy, the `DT_RPATH` has
the highest priority, higher than `LD_LIBRARY_PATH`, so if this later one
is set in the environment, it should not interfere with the xPack binaries.

Please note that previous versions, up to mid-2020, used `DT_RUNPATH`, which
has a priority lower than `LD_LIBRARY_PATH`, and does not tolerate setting
it in the environment.

### `@rpath` and `@loader_path`

Similarly, on macOS, the binaries are adjusted with `install_name_tool` to use a
relative path.

## Documentation

The original documentation is available
[online](https://github.com/NixOS/patchelf/).

## Build

The binaries for all supported platforms
(Windows, macOS and GNU/Linux) were built using the
[xPack Build Box (XBB)](https://xpack.github.io/xbb/), a set
of build environments based on slightly older distributions, that should be
compatible with most recent systems.

The scripts used to build this distribution are in:

- `distro-info/scripts`

For the prerequisites and more details on the build procedure, please see the
[How to build](https://github.com/xpack-dev-tools/patchelf-xpack/blob/xpack/README-MAINTAINER.md) page.

## CI tests

Before publishing, a set of simple tests were performed on an exhaustive
set of platforms. The results are available from:

- [GitHub Actions](https://github.com/xpack-dev-tools/patchelf-xpack/actions/)
- [Travis CI](https://app.travis-ci.com/github/xpack-dev-tools/patchelf-xpack/builds/)

## Tests

TBD

## Checksums

The SHA-256 hashes for the files are:
