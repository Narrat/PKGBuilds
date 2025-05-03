# Maintainer: Lex Black <autumn-wind@web.de>

pkgname=louvre 
pkgver=2.17.0_1
pkgrel=1
pkgdesc="C++ library for building Wayland compositors"
arch=('x86_64')
url="https://github.com/CuarzoSoftware/Louvre"
license=('LGPL-2.1-only')
depends=('libsrm' 'wayland' 'libglvnd' 'libxcursor' 'libxkbcommon' 'pixman' 'libdrm' 'mesa' 'libinput' 'seatd' 'glibc' 'freeimage' 'fontconfig' 'freetype2' 'icu' 'systemd-libs')
makedepends=('meson')
source=(${pkgname}-${pkgver/_/-}.tar.gz::${url}/archive/refs/tags/v${pkgver/_/-}.tar.gz)
sha256sums=('4f3a48d2a220b151479995e016b5827f95c8fca6d201b743452d8f5271631a07')


build() {
    arch-meson "Louvre-${pkgver/_/-}/src" build
    meson compile -C build
}

package() {
    meson install -C build --destdir "$pkgdir"
}

