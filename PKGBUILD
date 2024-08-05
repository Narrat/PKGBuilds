# Contributor: Lex Black <autumn-wind@web.de>

pkgname=mpvpaper
pkgver=1.7
pkgrel=1
pkgdesc="video wallpaper program for wlroots based wayland compositors"
arch=('i686' 'x86_64')
url="https://github.com/GhostNaN/$pkgname"
license=('GPL3')
depends=('libmpv.so' 'libwayland-client.so' 'libwayland-egl.so')
makedepends=('meson' 'ninja' 'wayland-protocols')
optdepends=('socat: control via sockets')
source=(${pkgname}-${pkgver}.tar.gz::https://github.com/GhostNaN/mpvpaper/archive/${pkgver}.tar.gz)
b2sums=('103582b7e5cce6293572c21299c125ef112441d1cec355e133bf54cb299123cde77deb92cd19f819102a0e6389018d4027965bb66070098a01c06f11c30b64c4')


build() {
  arch-meson "$pkgname-$pkgver" build
  meson compile -C build
}

package() {
  meson install -C build --destdir "$pkgdir"

  install -vDm644 "$pkgname-$pkgver"/mpvpaper.man "$pkgdir"/usr/share/man/man1/${pkgname}.1
}
