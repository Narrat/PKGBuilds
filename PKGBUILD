# Maintainer: Lex Black <autumn-wind@web.de>

_pkgname=srm
pkgname=lib${_pkgname}
pkgver=0.5.6_2
pkgrel=1
pkgdesc="C library that simplifies the development of Linux DRM/KMS applications"
arch=('x86_64')
url="https://github.com/CuarzoSoftware/SRM"
license=('GPL3')
depends=('libglvnd' 'libdrm' 'mesa' 'libdisplay-info' 'libinput' 'seatd' 'glibc' 'systemd-libs')
makedepends=('meson')
source=(${_pkgname}-${pkgver/_/-}.tar.gz::$url/archive/refs/tags/v${pkgver/_/-}.tar.gz)
sha256sums=('9438dcf544174bd5954f184e4d181dfc19aefada87d4b17c01c4cc0ab9e0f061')


build() {
    arch-meson "SRM-${pkgver/_/-}/src" build
    meson compile -C build
}

package() {
    meson install -C build --destdir "$pkgdir"
}

