
[![GitHub package.json version](https://img.shields.io/github/package-json/v/xpack-dev-tools/patchelf-xpack)](https://github.com/xpack-dev-tools/patchelf-xpack/blob/xpack/package.json)
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/xpack-dev-tools/patchelf-xpack)](https://github.com/xpack-dev-tools/patchelf-xpack/releases/)
[![npm (scoped)](https://img.shields.io/npm/v/@xpack-dev-tools/patchelf.svg?color=blue)](https://www.npmjs.com/package/@xpack-dev-tools/patchelf/)
[![license](https://img.shields.io/github/license/xpack-dev-tools/patchelf-xpack)](https://github.com/xpack-dev-tools/patchelf-xpack/blob/xpack/LICENSE)

# The xPack NixOS patchelf

A standalone cross-platform (macOS/Linux) **NixOS patchelf**
binary distribution, intended for reproducible builds.

The main target is GNU/Linux, to adjust `DT_RPATH.

In addition to the the binary archives and the package meta data,
this project also includes the build scripts.

## Overview

This open source project is hosted on GitHub as
[`xpack-dev-tools/patchelf-xpack`](https://github.com/xpack-dev-tools/patchelf-xpack)
and provides the platform specific binaries for the
[xPack NixOS patchelf](https://xpack.github.io/patchelf/).

This distribution follows the official
[NixOS patchelf](https://github.com/NixOS/patchelf/releases/) releases.

The binaries can be installed automatically as **binary xPacks** or manually as
**portable archives**.

## Release schedule

This distribution is generally one minor release behind the upstream releases.
In practical terms, when the minor release number changes, it awaits a few
more weeks to get the latest patch release.

## User info

This section is intended as a shortcut for those who plan
to use the NixOS patchelf binaries. For full details please read the
[xPack NixOS patchelf](https://xpack.github.io/patchelf/) pages.

### Easy install

The easiest way to install NixOS patchelf is using the **binary xPack**, available as
[`@xpack-dev-tools/patchelf`](https://www.npmjs.com/package/@xpack-dev-tools/patchelf)
from the [`npmjs.com`](https://www.npmjs.com) registry.

#### Prerequisites

A recent [xpm](https://xpack.github.io/xpm/),
which is a portable [Node.js](https://nodejs.org/) command line application.

It is recommended to update to the latest version with:

```sh
npm install --location=global xpm@latest
```

For details please follow the instructions in the
[xPack install](https://xpack.github.io/install/) page.

#### Install

With the `xpm` tool available, installing
the latest version of the package and adding it as
a dependency for a project is quite easy:

```sh
cd my-project
xpm init # Only at first use.

xpm install @xpack-dev-tools/patchelf@latest

ls -l xpacks/.bin
```

This command will:

- install the latest available version,
into the central xPacks store, if not already there
- add symbolic links to the central store into
the local `xpacks/.bin` folder.

The central xPacks store is a platform dependent
folder; check the output of the `xpm` command for the actual
folder used on your platform).
This location is configurable via the environment variable
`XPACKS_STORE_FOLDER`; for more details please check the
[xpm folders](https://xpack.github.io/xpm/folders/) page.

It is also possible to install NixOS patchelf globally, in the user home folder:

```sh
xpm install --global @xpack-dev-tools/patchelf@latest
```

After install, the package should create a structure like this (macOS files;
only the first two depth levels are shown):

```console
$ tree -L 2 xpacks/xpack-dev-tools-patchelf/.content/
xpacks/xpack-dev-tools-patchelf/.content/
├── README.md
├── bin
│   └── patchelf
└── distro-info
    ├── CHANGELOG.md
    ├── licenses
    ├── patches
    └── scripts

5 directories, 3 files
```

No other files are installed in any system folders or other locations.

#### Uninstall

The binaries are distributed as portable archives; thus they do not need
to run a setup and do not require an uninstall; simply removing the
folder is enough.

To remove the links created by xpm in the current project:

```sh
cd my-project

xpm uninstall @xpack-dev-tools/patchelf
```

To completely remove the package from the global store:

```sh
xpm uninstall --global @xpack-dev-tools/patchelf
```

### Manual install

For all platforms, the **xPack NixOS patchelf**
binaries are released as portable
archives that can be installed in any location.

The archives can be downloaded from the
GitHub [Releases](https://github.com/xpack-dev-tools/patchelf-xpack/releases/)
page.

For more details please read the
[Install](https://xpack.github.io/patchelf/install/) page.

### Versioning

The version strings used by the NixOS patchelf project are three number strings
like `0.15.0`;
to this string the xPack distribution adds a four number,
but since semver allows only three numbers, all additional ones can
be added only as pre-release strings, separated by a dash,
like `0.15.0-1`. When published as a npm package, the version gets
a fifth number, like `0.15.0-1.1`.

Since adherence of third party packages to semver is not guaranteed,
it is recommended to use semver expressions like `^0.15.0` and `~0.15.0`
with caution, and prefer exact matches, like `0.15.0-1.1`.

## Maintainer info

For maintainer info, please see the
[README-MAINTAINER](https://github.com/xpack-dev-tools/patchelf-xpack/blob/xpack/README-MAINTAINER.md)

## Support

The quick answer is to use the GitHub
[Discussions](https://github.com/xpack-dev-tools/patchelf-xpack/discussions/).

For more details please read the
[Support](https://xpack.github.io/patchelf/support/) page.

## License

The original content is released under the
[MIT License](https://opensource.org/licenses/MIT), with all rights
reserved to [Liviu Ionescu](https://github.com/ilg-ul/).

The binary distributions include several open-source components; the
corresponding licenses are available in the installed
`distro-info/licenses` folder.

## Download analytics

- GitHub [`xpack-dev-tools/patchelf-xpack`](https://github.com/xpack-dev-tools/patchelf-xpack/) repo
  - latest xPack release
[![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/patchelf-xpack/latest/total.svg)](https://github.com/xpack-dev-tools/patchelf-xpack/releases/)
  - all xPack releases [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/patchelf-xpack/total.svg)](https://github.com/xpack-dev-tools/patchelf-xpack/releases/)
  - [individual file counters](https://somsubhra.github.io/github-release-stats/?username=xpack-dev-tools&repository=patchelf-xpack) (grouped per release)
- npmjs.com [`@xpack-dev-tools/patchelf`](https://www.npmjs.com/package/@xpack-dev-tools/patchelf/) xPack
  - latest release, per month
[![npm (scoped)](https://img.shields.io/npm/v/@xpack-dev-tools/patchelf.svg)](https://www.npmjs.com/package/@xpack-dev-tools/patchelf/)
[![npm](https://img.shields.io/npm/dm/@xpack-dev-tools/patchelf.svg)](https://www.npmjs.com/package/@xpack-dev-tools/patchelf/)
  - all releases [![npm](https://img.shields.io/npm/dt/@xpack-dev-tools/patchelf.svg)](https://www.npmjs.com/package/@xpack-dev-tools/patchelf/)

Credit to [Shields IO](https://shields.io) for the badges and to
[Somsubhra/github-release-stats](https://github.com/Somsubhra/github-release-stats)
for the individual file counters.
