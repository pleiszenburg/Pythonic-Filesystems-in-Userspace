# Pythonic Filesystems in Userspace (FUSE) in 2019

[Filesystem in Userspace](https://en.wikipedia.org/wiki/Filesystem_in_Userspace)

## API

Two widely used versions exist: 2 and 3. While version 3 is currently being adopted by more and more projects, most FUSE file systems tend to use version 2 at this point.

Besides API versions, there are also two API levels: The high level FUSE API and the low level FUSE API.

Not all FUSE libraries and bindings offer both API versions and/or API levels. This must be taken into consideration when developing a cross-platform FUSE file system.

## Libraries

While FUSE is (at least in the Unix world) a Kernel feature, several user space libraries exist for easy access. `libfuse` acts as the reference implementation.

- [libfuse](https://github.com/libfuse/libfuse) (Linux, FreeBSD)
- [libfuse](https://github.com/openbsd/src/tree/master/lib/libfuse) (OpenBSD)
- [librefuse](https://github.com/NetBSD/src/tree/netbsd-8/lib/librefuse) (NetBSD) through [PUFFS](https://en.wikipedia.org/wiki/PUFFS_(NetBSD))
- [FUSE for macOS](https://github.com/osxfuse/osxfuse) (OSX)
- [MacFUSE](https://code.google.com/archive/p/macfuse/) (OSX), no longer maintained
- [WinFsp](https://github.com/billziss-gh/winfsp) (Windows)
- [Dokany](https://github.com/dokan-dev/dokany) (Windows)
- [Dokan](https://code.google.com/archive/p/dokan/) (Windows), no longer maintained

In summary, FUSE is supported on Linux, FreeBDS, OpenBSD, NetBSD, Mac OS X and Windows. APIs are (more or less) compatible. FUSE is also known to work on OpenSolaris/Illumos, Minix and Android.

## Python bindings

Several competing Python bindings for FUSE exist. Some are unmaintained. Some are offering access only to the high level API or to the low level API. Some are not suitable for cross-platform use.

- [fuse-python](https://github.com/libfuse/python-fuse) (used by 90+)
- [llfuse](https://github.com/python-llfuse/python-llfuse) (used by *30+*), officially no longer maintained
- [pyfuse3](https://github.com/libfuse/pyfuse3) (used by 3+)
- [fusepy](https://github.com/fusepy/fusepy) (used by 300+), [practically no longer maintained](https://github.com/fusepy/fusepy/issues/134)
- [refuse](https://github.com/pleiszenburg/refuse) (used by 2+)

Getting precise usage statistics is not trivial. The above numbers are based partially on GitHub's "used by" statistics and partially on current numbers from [libraries.io](https://www.libraries.io).

`python-fuse` (high level API, versions 2) and `python-llfuse` (low level API, version 2) were developed by the original `libfuse` authors - specifically as bindings to `libfuse`. While `python-fuse` is still being maintained, support for `python-llfuse` has been dropped. It is superseded by `pyfuse3` (low level API, version 3), which is also being developed by the `libfuse` team. `pyfuse3` is the currently only async-enabled Python FUSE package.

`fusepy` is the currently only viable cross-platform Python implementation. It offers both low and high level API bindings in version 2 where possible. Its is based on `ctypes`. Development seized in 2016 and was only briefly resumed in 2018. Several forks attempt to continue development, e.g. `refuse`.

## Python binding abstraction layers

- [fusetree](https://github.com/paulo-raca/fusetree)

## Introductions

- 2013-10-30: [Writing a FUSE filesystem in Python](https://www.stavros.io/posts/python-fuse-filesystem/)

## Relevant news

- 2019-03-12: [FUSE Is Fusing More Performance Improvements In Linux 5.1](https://www.phoronix.com/scan.php?page=news_item&px=Faster-FUSE-Linux-5.1)
