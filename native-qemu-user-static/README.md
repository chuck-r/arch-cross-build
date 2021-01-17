## qemu-user-static

This is a static build of qemu that provides qemu-${arch}-static binaries for use in emulation.

I have applied a custom patch to it that has not been upstreamed yet (pending further testing). For 99% of use cases it works fine, I just can't say that the other 1% of issues aren't related to the patch just yet.

To install the handler into the kernel, once you build the package run:

    /usr/lib/qemu-user-static/qemu-binfmt-update.sh --systemd ${system_to_emulate} --persist yes

Use `/usr/lib/qemu-user-static/qemu-binfmt-update.sh --help` for a full list of options.

Once the handler is installed, you should be able to run emulation within a chroot without any issues. Running outside of a chroot is a little trickier, however.

When building and testing my cross-packages I have set my `LDFLAGS`, `CFLAGS`, and `CXXFLAGS` within my makepkg.conf to include `-Wl,-rpath=/usr/arm-linux-gnueabihf,-rpath-link=/usr/arm-linux-gnueabihf`. This way, when the loader loads any of the programs compiled in this way, it first checks for libraries in /usr/arm-linux-gnueabihf before the standard locations (/lib, /usr/lib, /lib32, /lib64).
