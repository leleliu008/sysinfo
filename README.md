# sysinfo

A command-line utility to get your currently running system's information.

## Build with CMake

```bash
git clone --depth=1 https://github.com/leleliu008/sysinfo
cd sysinfo

cmake -S . -B   build.d -G Ninja -DCMAKE_INSTALL_PREFIX=/usr/local
cmake --build   build.d
cmake --install build.d
```

|`target`|`component`|`installed files`|
|-|-|-|
|`sysinfo`|`bin`|`bin/sysinfo`|
|`sysinfo-static`|`lib`|`lib/libsysinfo.a`|
|`sysinfo-shared`|`lib`|`lib/libsysinfo.so`|
||`dev`|`include/sysinfo.h`<br>`lib/pkgconfig/libsysinfo.pc`<br>`lib/cmake/sysinfo/*.cmake`|

## Build without CMake

```bash
git clone --depth=1 https://github.com/leleliu008/sysinfo
cd sysinfo

cc -Os -s -flto -o sysinfo src/main/sysinfo.c src/lib/sysinfo.c -Isrc/lib
```

## sysinfo command usage

- **show help of this command**

    ```bash
    sysinfo -h
    sysinfo --help
    ```

- **show version of this command**

    ```bash
    sysinfo -v
    sysinfo --version
    ```

- **show your currently running system info**

    ```bash
    sysinfo
    ```

- **show your currently running system belong to kind**

    ```bash
    sysinfo kind
    ```

    result might be any one of `windows` `darwin` `dragonflybsd` `freebsd` `netbsd` `openbsd` `linux` `android`

- **show your currently running system belong to type**

    ```bash
    sysinfo type
    ```

    result might be any one of `windows` `macos` `ios` `tvos` `watchos` `dragonflybsd` `freebsd` `netbsd` `openbsd` `linux` `android`

- **show your currently running system code**

    ```bash
    sysinfo code
    ```

    result might be any one of `windows` `macos` `ios` `tvos` `watchos` `dragonflybsd` `freebsd` `netbsd` `openbsd` `android` `debian` `ubuntu` `centos` `fedora` `arch` `manjaro` `gentoo` `apline` `void`

- **show your currently running system display name**

    ```bash
    sysinfo name
    ```

    result might be any one of `Windows` `macOS` `iOS` `tvOS` `watchOS` `DragonFlyBSD` `FreeBSD` `NetBSD` `OpenBSD` `Android` `Debian GNU/Linux` `Ubuntu` `CentOS` `Fedora`

- **show your currently running system's version**

    ```bash
    sysinfo vers
    ```

- **show your currently running system's display name**

    ```bash
    sysinfo arch
    ```

    result might be any one of `x86_64` `amd64` `aarch64` `riscv64` `ppc64le` `loongarch64` `armv7` `armv7l`

- **show your currently running system's avaiable number of cpu**

    ```bash
    sysinfo ncpu
    ```

- **show your currently running system's libc**

    ```bash
    sysinfo libc
    ```

    result might be any one of `glibc` `musl`

## common used system list

|kind|type|code|name|libc|sys-pkg|subs|sub-sys-pkg|
|-|-|-|-|-|-|-|-|
|`darwin`|`macos`|`macos`|[macOS](https://www.apple.com/macos)||[HomeBrew](https://brew.sh/)|||
|`linux`|`linux`|`debian`|[Debian GNU/Linux](https://www.debian.org/releases/)|`glibc`|[apt-get](https://manpages.debian.org/buster/apt/apt-get.8.en.html)|||
|`linux`|`linux`|`ubuntu`|[Ubuntu](https://releases.ubuntu.com/)|`glibc`|[apt-get](http://manpages.ubuntu.com/manpages/cosmic/man8/apt-get.8.html)|||
|`linux`|`linux`|`linuxmint`|[LinuxMint](https://linuxmint.com/)|`glibc`|[apt-get](https://community.linuxmint.com/tutorial/view/588)|||
|`linux`|`linux`|`fedora`|[Fedora](https://getfedora.org/)|`glibc`|[yum](http://yum.baseurl.org/) [dnf](https://github.com/rpm-software-management/dnf)|||
|`linux`|`linux`|`centos`|[CentOS](https://www.centos.org/centos-linux/)|`glibc`|[yum](http://yum.baseurl.org/) [dnf](https://github.com/rpm-software-management/dnf)|||
|`linux`|`linux`|`rocky`|[RockyLinux](https://rockylinux.org/)|`glibc`|[yum](http://yum.baseurl.org/) [dnf](https://github.com/rpm-software-management/dnf)|||
|`linux`|`linux`|`opensuse-leap`|[openSUSE Leap](https://get.opensuse.org/leap)|`glibc`|[zypper](https://en.opensuse.org/Portal:Zypper)|||
|`linux`|`linux`|`alpine`|[AlpineLinux](https://alpinelinux.org/)|`musl`|[apk](https://docs.alpinelinux.org/user-handbook/0.1a/Working/apk.html)|||
|`linux`|`linux`|`void`|[VoidLinux](https://voidlinux.org/)|`musl`|[xbps](https://github.com/void-linux/xbps/)|||
|`linux`|`linux`|`void`|[VoidLinux](https://voidlinux.org/)|`glibc`|[xbps](https://github.com/void-linux/xbps/)|||
|`linux`|`linux`|`arch`|[ArchLinux](https://archlinux.org/)|`glibc`|[pacman](https://wiki.archlinux.org/index.php/pacman)|||
|`linux`|`linux`|`manjaro`|[Manjaro](https://manjaro.org/)|`glibc`|[pacman](https://wiki.manjaro.org/index.php?title=Pacman_Overview)|||
|`linux`|`linux`|`gentoo`|[Gentoo](https://www.gentoo.org/)|`glibc`|[Portage](https://wiki.gentoo.org/wiki/Portage)|||
|`freebsd`|`freebsd`|`freebsd`|[FreeBSD](https://www.freebsd.org/)||[pkg](https://github.com/freebsd/pkg)|||
|`openbsd`|`openbsd`|`openbsd`|[OpenBSD](https://www.openbsd.org/)||[pkg_*](https://www.openbsdhandbook.com/package_management/)|||
|`netbsd`|`netbsd`|`netbsd`|[NetBSD](https://www.netbsd.org/)||[pkgin](https://pkgin.net/)|||
|`windows`|`windows`|`windows`|[Windows](https://www.microsoft.com/en-us/windows)||[Chocolatey](https://chocolatey.org/)|[cygwin](https://www.cygwin.com/)|[Chocolatey](https://chocolatey.org/)|
|`windows`|`windows`|`windows`|[Windows](https://www.microsoft.com/en-us/windows)||[Chocolatey](https://chocolatey.org/)|[msys2](https://www.msys2.org/)|[pacman](https://www.msys2.org/docs/package-management/)|
|`windows`|`windows`|`windows`|[Windows](https://www.microsoft.com/en-us/windows)||[Chocolatey](https://chocolatey.org/)|[mingw32](https://www.msys2.org/)|[pacman](https://www.msys2.org/docs/package-management/)|
|`windows`|`windows`|`windows`|[Windows](https://www.microsoft.com/en-us/windows)||[Chocolatey](https://chocolatey.org/)|[mingw64](https://www.msys2.org/)|[pacman](https://www.msys2.org/docs/package-management/)|
|`android`|`android`|`android`|[Andriod](https://www.android.com/)|`bionic`||[termux](https://termux.com/)|[pkg](https://wiki.termux.com/wiki/Package_Management)|
