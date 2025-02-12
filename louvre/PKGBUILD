# Maintainer: Lex Black <autumn-wind@web.de>

pkgname=louvre 
pkgver=2.14.1_1
pkgrel=1
pkgdesc="C++ library for building Wayland compositors"
arch=('x86_64')
url="https://github.com/CuarzoSoftware/Louvre"
license=('LGPL-2.1-only')
depends=('libsrm' 'wayland' 'libglvnd' 'libxcursor' 'libxkbcommon' 'pixman' 'libdrm' 'mesa' 'libinput' 'seatd' 'glibc' 'freeimage' 'fontconfig' 'freetype2' 'icu' 'systemd-libs')
makedepends=('meson')
source=(${pkgname}-${pkgver/_/-}.tar.gz::${url}/archive/refs/tags/v${pkgver/_/-}.tar.gz)
sha256sums=('bb1a5b3954068471505a21438496eba7e254cfe63fa40a4df2e7f3f09a70c364')


build() {
    arch-meson "Louvre-${pkgver/_/-}/src" build
    meson compile -C build
}

package() {
    meson install -C build --destdir "$pkgdir"
}

