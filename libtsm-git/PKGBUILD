# Contributor: Aetf <aetf at unlimitedcodeworks dot xyz>

pkgname=libtsm-git
pkgver=4.4.2.r1.g8f8e314
pkgrel=1
pkgdesc="Terminal-emulator State Machine"
arch=('i686' 'x86_64')
url='https://github.com/kmscon/libtsm'
license=('MIT')
depends=(glibc)
makedepends=(
  check
  git
  meson
  libxkbcommon
)
provides=('libtsm')
conflicts=('libtsm')
options=(!libtool)
source=(git+${url}.git)
b2sums=('SKIP')

pkgver() {
  cd "${pkgname%-git}"
  git describe --long --tags --abbrev=7 | sed -r "s/^$_gitname-//;s/([^-]*-g)/r\\1/;s/-/./g;s/^v//"
}

build() {
  arch-meson "${pkgname%-git}" build
  meson compile -C build
}

package() {
  meson install -C build --destdir="$pkgdir"
  install -Dm644 ${pkgname%-git}/COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

# vim:set ts=2 sw=2 et:
