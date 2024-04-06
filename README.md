# zpkg [![Fork ome on GitHub](https://github.blog/wp-content/uploads/2008/12/forkme_right_orange_ff7600.png?resize=149%2C149)](https://github.com/Anonyming/zpkg)

With zpkg you can install and use programs from other distributions

## Documentation

### Zpkg - a meta package manager

### Use programs from other Linux distributions

## Install

    $ curl -Lf https://github.com/Anonyming/zpkg/releases/download/0.2.5/zpkg.zpkg | tar -xJf - -C ~/.local

## What does zpkg do?

With zpkg you can install programs from other distributions into your system

    $ zpkg add gimp --from alpine --apk gimp

zpkg will install programs to your home directory.

    $ readlink ~/.local/bin/gimp
                ../lib/zpkg/gimp/gimp

You can upgrade zpkg packages. Upgrades are atomic for each package.

    $ zpkg upgrade

It is possible to repackage added programs into standalone zpkg packages. These packages can be easily installed into other machines. The only system requirement is _tar_. Standalone zpkg packages may be managed (removed, upgraded) with zpkg.

    $ zpkg package gimp /tmp/gimp.zpkg
                Install package locally:
                $ tar -xf /tmp/gimp.zpkg -C ~/.local
                
                Install package globally:
                $ tar -xf /tmp/gimp.zpkg -C /usr/local

## What else should I know?

* For package managers that need multi user support - like _apt_ - you need _newuidmap_ installed and _/etc/subuid_ configured when running zpkg unprivileged (Done in Ubuntu).
* Packages should never change files of it's base system.

## More examples

    $ zpkg ls
    gimp
    zpkg
    
    $ zpkg freeze
    zpkg add gimp --from alpine --apk gimp
    zpkg add zpkg --from-github Anonyming/zpkg
    
    $ zpkg rm gimp
    
    $ zpkg add --from ubuntu --apt gimp
    
    $ zpkg --help

## Usage

    USAGE
        zpkg [-g|-l] {add,flush,freeze,ls,package,rebuild,rm,upgrade} ...
    
    SUBCOMMANDS
        add [PKG] BUILD-ARGS   builds and adds a package
        flush                  flushes the build cache
        freeze                 print package with build instruction
        ls                     lists all installed packages
        package PKG FILE       creates a standalone package
        rebuild PKG            rebuild given package
        rm PKG                 uninstalls the given package
        unfreeze FREEZED-FILE  apply frozen file
        upgrade                upgrades each package atomically
    
    ARGUMENTS
        --global, -g
            affects the system globally
        --local, -l
            saves packages in cwd under ./zpkg
    
    BUILD ARGUMENTS
        --from, -f
            choose a base image
        --run, -x
            run any shell (/bin/sh) command
        --layer, -l
            adds a layer for build caching
        --from-github
            build according to instructions at GitHub project
        --add-apt-repository, --apt, --apk, --apt, --dnf, --emerge, --npm,
        --pacman, --pip, --pip3, --yum
            Invokes the given tool with it's primary action
        -A same as `--from alpine:edge --apk`
        -C same as `--from centos:8 --yum`
        -D same as `--from debian:sid --apt`
        -F same as `--from fedora:32 --dnf`
        -G same as `--from gentoo:current --emerge`
        -R same as `--from archlinux:current --pacman`
        -U same as `--from ubuntu:focal --apt`
    
    EXAMPLE
        zpkg add xeyes -U x11-apps
        zpkg add -A gimp
        zpkg add -A py3-pip --pip3 yapf
        zpkg rm yapf

## FAQ

### How stable is zpkg?

Alpha.

### How is zpkg licensed?

zpkg and [plash](http://plash.io) are under the MIT licence.

### What else can I do with zpkg?

* Quickly use applications from other Linux distributions.
* Install applications without root.
* Distribute applications with _zpkg package_. This is by the way how zpkg is distributed.
* Deploy web applications or services with _zpkg package_.
* Have distribution independent applications in your home folder or a usb stick.

### Does zpkg run on Windows/MacOS/BSD?

zpkg requires a Linux kernel. Running on another host operating system is only possible with it's eventual Linux compability mechanisms.

### What applications work with zpkg?

Everything except System Programs. As an example: _Bash_, _synaptic_, _apt_, and _gnome-tweak-tool_ may not work as desired. _LibreOffice_, _Firefox_, _Gimp_ and _pylint_ are fully supported.

### Which build commands are supported?

All of _[plash's](http://plash.io)_ build commands are supported when adding packages.

### What happens if a package changes files of its base image?

This would also affect other packages with the same base image. If that ever happens you need to remove the bad package (_zpkg rm badpkg_) and upgrade (_zpkg upgrade_).

### How do I keep zpkg updated?

Since zpkg is packaged with zpkg, running _zpkg upgrade_ will upgrade it.

### Can I contribute?

[Absolutely](http://github.com/Anonyming/zpkg)

## Thank you

If you like zpkg, [star it on GitHub](https://github.com/Anonyming/zpkg). Help others
by [reporting any issue](https://github.com/Anonyming/zpkg/issues). Feel free
to [contact me directly](mailto:nick.zamega@yandex.ru&subject=Zpkg?body=I%20searched%20a%20bud,%20have%20an%20idea,%20want%20to%20help%20etc.?cc=%6D%61%69%6C%40%69%72%61%65%2%6ED%65)
for anything.
to [contact me directly](mailto:mailto:) for anything.

[Documentation external website](https://ihucos.github.io/zpkg/)

## How stable?
Alpha
