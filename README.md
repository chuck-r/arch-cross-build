## Arch packages for cross-compiling

This is a collection of packages that I have either copied or modified in order to work better for cross-compiling on an Arch-based Linux distribution.

I have taken the liberty to try and make all packages reside solely under /usr/[triplet] (i.e. /usr/arm-linux-gnueabihf) as much as possible. In addition while others have done things like skip tests in order to get them to build, I have tried to maintain these tests whenever possible.

One of the first things one should do when starting to use these packages is to install qemu-user-static. These are static binaries for user-mode Linux emulation. As a static binary, they are suitable for using in, for example, a chroot environment. If properly installed in /etc/binfmt.d/, Linux will call the emulator whenever the system attempts to run a non-native binary. This makes test and other compilation features work correctly -- even if they aren't cross-build compatible.
