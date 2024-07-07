# Maintainer: Lex Black <autumn-wind@web.de>

_pkgname=srm
pkgname=lib${_pkgname}
pkgver=0.6.1_1
pkgrel=1
pkgdesc="C library that simplifies the development of Linux DRM/KMS applications"
arch=('x86_64')
url="https://github.com/CuarzoSoftware/SRM"
license=('GPL3')
depends=('libglvnd' 'libdrm' 'mesa' 'libdisplay-info' 'libinput' 'seatd' 'glibc' 'systemd-libs')
makedepends=('meson')
source=(${_pkgname}-${pkgver/_/-}.tar.gz::$url/archive/refs/tags/v${pkgver/_/-}.tar.gz)
sha256sums=('ae3d2dcbd8df5b2856f662596962b632f5b56cd3d6d6da333242238b2756bfd8')


build() {
    arch-meson "SRM-${pkgver/_/-}/src" build
    meson compile -C build
}

package() {
    meson install -C build --destdir "$pkgdir"
}

