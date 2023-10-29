# Install Alpine Linux in chroot on a device

This is a branch of original script intended for quick Alpine setup on a device with low capabilities.

Tested on a router with AsusWRT-Merlin and Entware

## Why

Because Alpine is ideal for running containerized services.

Even though chroot is not a container.

## Modifications to original script

* `APK_TOOLS_URI` and `APK_TOOLS_SHA256` defaults are set to `aarch64` binary.
* `busybox-suid` and `musl-utils` are removed from base install.
* `ALPINE_PACKAGES` are set to empty list.
* Shebang is modified to use Entware bash (built-in busybox does not provide `getopts`).

## Requirements

Installation script requires following Entware packages to be installed:

* `coreutils-id`
* `coreutils-mktemp` (optional)
* `bash`
* `coreutils-sha256sum`

List may appear incomplete.

`curl` or `wget`, `chroot`, `sed` and other basic commands are provided by AsusWRT-Merlin.

## Installation

* Download [raw script](https://github.com/pelepelin/alpine-chroot-install/raw/aarch64/alpine-chroot-install).
* `chmod +x alpine-chroot-install`
* `./alpine-chroot-install -h` for usage. Default `CHROOT_DIR` is most likely not where you want to install.
* `./alpine-chroot-install -d CHROOT_DIR`.

## Uninstallation

**Warning! Don't** `rm -rf` the chrooted directory while it has bind-mounted directories inside.
Use the created `$CHROOT_DIR/destroy` script.

**Warning!** Run the `destroy` script using its canonical absolute path, otherwise it can miss mounted directories.

## More

Also see the original [README](README-original.adoc).
