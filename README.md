# Void lx-brand Image Builder

This is a collection of scripts used for creating an lx-brand [Void
Linux][void] image.

## Requirements

In order to use these scripts you'll need:

- Void Linux running in a VM (required for the `install` script).
- A SmartOS (or SDC headnode) install (required for the `create-lx-image`
  script)

Note that the `install` script will fail if run in an lx-brand environment.

## Usage

### 1. Install Void Linux into a tarball

Run `./install` under Void to install Void Linux in a given directory.  This
will create a tarball of the installation in your working directory (named
`<image name>-<YYMMDD>.tar.gz`).

See `./install -h` for detailed usage.

Dependencies:

    xbps-install git
    xbps-install wget
    xbps-install xz
    git submodule update --init # needed for guesttools

Example:

    # ./install -a x86_64 -d void-install -m https://alpha.de.repo.voidlinux.org -i void -p 'Void Linux'


### 2. Create a VM image

Copy the tarball generated in step 1 to a SmartOS machine or SDC headnode and
run `./create-lx-image` to create the image.

See `./create-lx-image -h` for detail usage.

Example:

    # ./create-lx-image -t ~/void-20200408.tar.gz -k 5 -m "$(uname -v | cut -d_ -f2)" -i void -d 'Void 64-bit lx-brand image.'

[void]: https://voidlinux.org
