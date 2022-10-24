# Scripts to test the NixOS PatchELF xPack

The binaries can be available from one of the pre-releases:

<https://github.com/xpack-dev-tools/pre-releases/releases>

## Download the repo

The test script is part of the NixOS PatchELF xPack:

```sh
rm -rf ${HOME}/Work/patchelf-xpack.git; \
mkdir -p ~/Work; \
git clone \
  --branch xpack-develop \
  https://github.com/xpack-dev-tools/patchelf-xpack.git  \
  ${HOME}/Work/patchelf-xpack.git
```

## Start a local test

To check if NixOS PatchELF starts on the current platform, run a native test:

```sh
bash ${HOME}/Work/patchelf-xpack.git/tests/scripts/native-test.sh
```

The script stores the downloaded archive in a local cache, and
does not download it again if available locally.

To force a new download, remove the local archive:

```sh
rm -rf ~/Work/cache/xpack-patchelf-*-*
```
