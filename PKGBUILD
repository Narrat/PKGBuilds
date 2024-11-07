# Maintainer: Lex Black <autumn-wind@web.de>

pkgname=louvre 
pkgver=2.11.0_1
pkgrel=1
pkgdesc="C++ library for building Wayland compositors"
arch=('x86_64')
url="https://github.com/CuarzoSoftware/Louvre"
license=('MIT')
depends=('libsrm' 'wayland' 'libglvnd' 'libxcursor' 'libxkbcommon' 'pixman' 'libdrm' 'mesa' 'libinput' 'seatd' 'glibc' 'freeimage' 'fontconfig' 'freetype2' 'icu' 'systemd-libs')
makedepends=('meson')
source=(${pkgname}-${pkgver/_/-}.tar.gz::${url}/archive/refs/tags/v${pkgver/_/-}.tar.gz)
sha256sums=('e0f9362df6b37fbcbb5209c64f65ee3fb80766fd3467a063fc89f85eb65077e6')


build() {
    arch-meson "Louvre-${pkgver/_/-}/src" build
    meson compile -C build
}

package() {
    meson install -C build --destdir "$pkgdir"
}

