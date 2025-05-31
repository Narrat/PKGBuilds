# Maintainer: Lex Black <autumn-wind@web.de>

_pkgname=srm
pkgname=lib${_pkgname}
pkgver=0.12.1_1
pkgrel=1
pkgdesc="C library that simplifies the development of Linux DRM/KMS applications"
arch=('x86_64')
url="https://github.com/CuarzoSoftware/SRM"
license=('LGPL-2.1-only')
depends=('libglvnd' 'libdrm' 'mesa' 'libdisplay-info' 'libinput' 'seatd' 'glibc' 'systemd-libs')
makedepends=('meson')
source=(${_pkgname}-${pkgver/_/-}.tar.gz::$url/archive/refs/tags/v${pkgver/_/-}.tar.gz)
sha256sums=('9b7c35ffa6b90d61db814ca472f86dd22e5a3f914d7a5bede40492f9062411f3')


build() {
    arch-meson "SRM-${pkgver/_/-}/src" build
    meson compile -C build
}

package() {
    meson install -C build --destdir "$pkgdir"
}

