# Maintainer : speps <speps at aur dot archlinux dot org>
# Contributor: Xavion <Xavion (dot) 0 (at) Gmail (dot) com>
# Contributor: Giovanni Scafora <linuxmania@gmail.com>

pkgname=v4l2ucp
pkgver=2.0.2
pkgrel=4
pkgdesc="A universal control panel for Video for Linux Two (V4L2) devices"
arch=("i686" "x86_64")
url="http://${pkgname}.sourceforge.net"
license=('GPL2')
depends=('qt4' 'v4l-utils')
optdepends=('mplayer: Video Preview')
makedepends=('cmake')
install="$pkgname.install"
source=("http://downloads.sourceforge.net/sourceforge/$pkgname/$pkgname-$pkgver.tar.bz2"
        "$pkgname.desktop")
md5sums=('e5bc6e71e2cd3ab123c277b2f7154b4f'
         'db20c209857533aeeb00e30c4872efd3')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  # remove old v4l header
  sed -i 's|\(videodev\)\.|\12\.|' src/v4l2ctrl.c

  cmake . -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  make DESTDIR="$pkgdir/" install

  # Install Desktop file
  install -Dm644 ../$pkgname.desktop "$pkgdir/usr/share/applications/$pkgname.desktop"
}
