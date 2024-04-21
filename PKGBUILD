# Contributor: Lex Black <autumn-wind@web.de>

pkgname=mpvpaper
pkgver=1.5
pkgrel=1
pkgdesc="video wallpaper program for wlroots based wayland compositors"
arch=('i686' 'x86_64')
url="https://github.com/GhostNaN/$pkgname"
license=('GPL3')
depends=('mpv' 'wlroots')
makedepends=('meson' 'ninja' 'wayland-protocols')
optdepends=('socat: control via sockets')
source=(${pkgname}-${pkgver}.tar.gz::https://github.com/GhostNaN/mpvpaper/archive/${pkgver}.tar.gz)
b2sums=('c65382423d7fd83d7ff670f29f89fdb5990b822014727e9a675ae02b4befbff6587ee57d14a5ae6a9ad2b41ade45dd2cca8458a9cd8618b98bd95043e42b5102')


build() {
  arch-meson "$pkgname-$pkgver" build
  meson compile -C build
}

package() {
  meson install -C build --destdir "$pkgdir"

  install -vDm644 "$pkgname-$pkgver"/mpvpaper.man "$pkgdir"/usr/share/man/man1/${pkgname}.1
}
