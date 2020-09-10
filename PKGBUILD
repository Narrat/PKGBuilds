# Contributor: Lex Black <autumn-wind@web.de>

pkgname=mpvpaper
pkgver=1.0
pkgrel=1
pkgdesc="video wallpaper program for wlroots based wayland compositors"
arch=('i686' 'x86_64')
url="https://github.com/GhostNaN/$pkgname"
license=('GPL3')
depends=('mpv' 'wlroots')
makedepends=('meson' 'ninja')
optdepends=('socat: control via sockets')
source=(${pkgname}-${pkgver}.tar.gz::https://github.com/GhostNaN/mpvpaper/archive/1.0.tar.gz)
md5sums=('5968d21a913e3b7e9fc782074d5e24f1')


build() {
  cd $pkgname-$pkgver
  meson build --prefix=/usr
  ninja -C build
}

package() {
  cd $pkgname-$pkgver
  DESTDIR="$pkgdir" ninja -C build install
}
