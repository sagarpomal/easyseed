# easyseed(1)

## The easy, secure *multilanguage* mnemonic phrase and seed generator for ![₿](img/bitcoin_32px.png) Bitcoin [BIP 39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)

### Now with full BIP 39 functionality

- By nullius <[nullius@nym.zone](mailto:nullius@nym.zone)>
- PGP: [0xC2E91CD74A4C57A105F6C21B5A00591B2F307E0C](https://sks-keyservers.net/pks/lookup?op=get&search=0xC2E91CD74A4C57A105F6C21B5A00591B2F307E0C)
- Bitcoin, tips welcome: [3NULL3ZCUXr7RDLxXeLPDMZDZYxuaYkCnG](bitcoin:3NULL3ZCUXr7RDLxXeLPDMZDZYxuaYkCnG)

I originally wrote this because I needed a lightweight, reliable BIP 39 mnemonic phrase generator with easily auditable sources and minimal dependencies for use on a stripped-down airgap machine.  Correctness and reliability are important to me; thus, **easyseed(1)** has extensive built-in self-tests against the official test vectors.  In addition to simple mnemonic generation, **easyseed(1)** can now optionally output:

- The input entropy in hexadecimal
- The mnemonic corresponding to that entropy
- The BIP 39 output seed, optionally generated with an additional passphrase
- The BIP 32 `xprv` master extended private key (*[do not use with Electrum](https://github.com/spesmilo/electrum/issues/3671)*)

The source code is written in (mostly sort of) [KNF](https://www.freebsd.org/cgi/man.cgi?query=style&apropos=0&sektion=9&manpath=FreeBSD+11.1-RELEASE+and+Ports&arch=default&format=html).  It’s easy to read, and lovingly commented.  Anybody with basic knowledge of the C programming language should be able to understand what it does at a glance.

**easyseed(1) can generate mnemonics in all languages and writing systems for which a wordlist exists in the [BIP 39 repository](https://github.com/bitcoin/bips/tree/master/bip-0039).**  Listed in alphabetical order:

 - Chinese (Simplified) (汉语)
 - Chinese (Traditional) (漢語)
 - English [default]
 - French (Français)
 - Italian (Italiano)
 - Japanese (日本語)
 - Korean (한국어)
 - Spanish (Español)

It has been tested on FreeBSD, my main platform, and on Linux.  [Unfortunately, I may have slightly mussed the BSD building while preparing for publication; this should soon be fixed.  The build system generally is still wonky.  This is an early release, with most attention paid to the source code and manpage!]

For further details, [RTFM](https://raw.githubusercontent.com/nym-zone/easyseed/master/easyseed.1.txt).  Yes, it has a manpage.  Software is unworthy of release if it does not have a proper manpage.

License: AVL v0.0.1 with Bitcoin clause.  I would prefer to disclaim copyright, and and release things to the public domain (*the public domain is not a license, “CC0” people*).  However, this is not an ideal world.

Please direct usage discussion to the [forum thread](https://bitcointalk.org/index.php?topic=2664861.0), and bugs or concrete technical matters to the issue tracker.

## Installation

### FreeBSD:

```
make && make check
```

...then, `make install` as root (via `sudo` or otherwise).  Other BSDs are probably similar.

### Linux (GNUmakefile instead of Makefile):

```
make && make check && sudo make install
```

To enable passphrase entry, you must have `libbsd` and its headers installed.  (On Debian or Ubuntu, try `sudo apt-get install libbsd-dev`.)  Then to build, type:

```
make LBSD=1 && make check && sudo make install
```
