[Read Me](README.md) > [Developer](DEVELOPER.md) > Release

# Release Info
Make sure you have [Rust installed](https://www.rust-lang.org/tools/install).

Minimum rust version is 1.65, as I'm testing on this specific version. However, if needed you may try to build rws on your own using older version with the _--ignore-rust-version_ flag.


## Build

> cargo build --release
>
> cd target/release
>
> ./http-to-https-letsencrypt --ip=127.0.0.1 --port=80 --threads=100


# Release
Build binary on specific platform to prepare release.

For each binary provide sha 256 check sum.

Releases initially being prepared at
[Drive](https://drive.google.com/drive/folders/1wize_LrCwGgs4MSvldhbpqDx4UTD3uEk?usp=share_link) mirror.

There are additional templates for
[Homebrew](https://brew.sh/),
[Portage](https://wiki.gentoo.org/wiki/Portage),
[Debian](https://www.debian.org/) and
[RPM](https://rpm.org/) package systems.


Here is the list of supported architectures:
1. x86 64-bit Apple: **x86_64-apple-darwin**
    1. [Homebrew Formula](https://github.com/bohdaq/homebrew-http-to-https-letsencrypt)
1. x86 64-bit Linux: **x86_64-unknown-linux-gnu**
   1.  Debian: **[create package](https://github.com/bohdaq/http-to-https-letsencrypt-create-deb)** 
   1.  RPM: **[create package](https://github.com/bohdaq/http-to-https-letsencrypt-create-rpm)**
   1.  Portage: **[http-to-https-letsencrypt create ebuild](https://github.com/bohdaq/http-to-https-letsencrypt-portage-ebuild)**
   1.  Pacman: **[http-to-https-letsencrypt create pacman package](https://github.com/bohdaq/http-to-https-letsencrypt-arch-package)**

1. ARM 64-bit Linux: **aarch64_unknown_linux_gnu**
   1.  Debian: **[create package](https://github.com/bohdaq/http-to-https-letsencrypt-create-deb)**
1. x86 64-bit Windows: **x86_64-pc-windows-msvc**


Also, you can clone the repository and build **http-to-https-letsencrypt** binary for [other platforms](https://doc.rust-lang.org/nightly/rustc/platform-support.html).
