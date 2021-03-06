## Synopsis

*acme-client-portable* is yet another
[ACME](https://letsencrypt.github.io/acme-spec/) client, specifically for
[Let's Encrypt](https://letsencrypt.org), but one with a strong focus on
security. 

It was named *letskencrypt-portable* until version 0.1.11.

Please see
[kristaps.bsd.lv/acme-client](https://kristaps.bsd.lv/acme-client) for
stable releases: this repository is for current development of the
portable branch, which tracks
[acme-client](https://github.com/kristapsdz/acme-client) with goop to
allow compilation and secure operation on Linux, Mac OS X, NetBSD, and
FreeBSD (hence "-portable").
You will need [libressl](http://www.libressl.org/) on all systems and
[libbsd](https://libbsd.freedesktop.org/wiki/) on Linux.

This repository mirrors the master CVS repository: any source changes
will occur on the master and be pushed periodically to GitHub.  If you
have bug reports or patches, either file them here or e-mail them to me.
Feature requests will be ignored unless joined by a patch.

What are the difference between this and the non-portable release?

* Conditional support for OpenBSD's sandbox or Mac OS X.
* Proper preprocessor flags for unlocking some Linux functions.
* Different library names on Linux.
* Uses GNU make instead of BSD make.

This version tries its best to be secure, but some of its supported
operating systems are hostile to security.

On both Linux and Mac OS X, for example, the DNS resolution process is
effectively run in the main file-system and un-sandboxed due to the
complexity of lookups (needing mDNSresponder in the latter case or a
slew of mystery files in the former).

Moreover, while the sandbox on Mac OS X (which is deprecated?) exists,
its behaviour is not well-documented and, morever, is weakened to
co-exist with the file-system jail.  On Linux, the sandbox has not been
implemented in *acme-client-portable*, as it's just too complicated.

What can you do?

* If you know Linux sandboxing, please have at it!  There's only one
function to fill in.
* Same with the FreeBSD sandbox.

## License

Sources use the ISC (like OpenBSD) license.  See the
[LICENSE.md](LICENSE.md) file for details.

The [jsmn.c](jsmn.c) and [jsmn.h](jsmn.h) files use the MIT license.
See [https://github.com/zserge/jsmn](https://github.com/zserge/jsmn) for
details.
