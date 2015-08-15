# Maintainer: Daniel Beecham <daniel@lunix.se>
# Contributor: Jens Staal <staal1978@gmail.com>

options=(!strip)
pkgname="busybox-util-linux"
pkgver="1"
pkgrel=2
pkgdesc="Replacing the util-linux utilities from Base with symlinks to busybox"
arch=('any')
url="http://busybox.net/"
license=('GPLv2')
depends=('busybox')
provides=('util-linux')
conflicts=('util-linux')

source=('busybox.utillinux.bin.ls'      \
        'busybox.utillinux.sbin.ls'     \
        'busybox.utillinux.usr.bin.ls'  \
        'busybox.utillinux.usr.sbin.ls' \
        'busybox.missing.ls')

md5sums=('093eb0b438d374d65af716505a4acd75' \
         'aba11e0b2f4471ee91e7048c207dab93' \
         '2b426957e781c13c0d7a78bda36e8943' \
         '78c6a11bc7ed9c31376ee821a596a204' \
         '27330790fdff75d09c147255d69cd604')


package() {

_bin=("$srcdir/busybox.utillinux.bin.ls")
_sbin=("$srcdir/busybox.utillinux.sbin.ls")
_usrbin=("$srcdir/busybox.utillinux.usr.bin.ls")
_usrsbin=("$srcdir/busybox.utillinux.usr.sbin.ls")
_missing=("$srcdir/busybox.missing.ls")
  
  msg "creating package directories"
  mkdir -p "$pkgdir/usr/bin"
  mkdir -p "$pkgdir/usr/sbin"
  mkdir -p "$pkgdir/usr/share/getopt"
  mkdir -p "$pkgdir/usr/share/man/man1"
  mkdir -p "$pkgdir/var/lib/hwclock"

  msg "creating symlinks for binary replacements"

    for i in $(cat $_bin)
      do
      ln -s /usr/bin/busybox "$pkgdir/usr/bin/$i"
    done

    for i in $(cat $_sbin)
      do
      ln -s /usr/bin/busybox "$pkgdir/usr/sbin/$i"
    done

    for i in $(cat $_usrbin)
      do
      ln -s /usr/bin/busybox "$pkgdir/usr/bin/$i"
    done

    for i in $(cat $_usrsbin)
      do
      ln -s /usr/bin/busybox "$pkgdir/usr/sbin/$i"
    done

  warning "BIG warning! This package has lots of missing corresponding utilities:"
  warning "$(cat $_missing)"
  warning "make sure that it fulfills your needs before you install it, and do not install on production system"
}
