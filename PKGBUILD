# Maintainer: Lex Black <autumn-wind@web.de>

pkgname=louvre 
pkgver=2.3.2_1
pkgrel=1
pkgdesc="C++ library for building Wayland compositors"
arch=('x86_64')
url="https://github.com/CuarzoSoftware/Louvre"
license=('MIT')
depends=('libsrm' 'wayland' 'libglvnd' 'libxcursor' 'libxkbcommon' 'pixman' 'libdrm' 'mesa' 'libinput' 'seatd' 'glibc' 'freeimage' 'fontconfig' 'freetype2' 'icu' 'systemd-libs')
makedepends=('meson')
source=(${pkgname}-${pkgver/_/-}.tar.gz::${url}/archive/refs/tags/v${pkgver/_/-}.tar.gz)
sha256sums=('b9e3ec33fafe9a26c855b8b74de2804680e5f840150053c844cbfba717e9b41a')


build() {
    arch-meson "Louvre-${pkgver/_/-}/src" build
    meson compile -C build
}

package() {
    meson install -C build --destdir "$pkgdir"
}

