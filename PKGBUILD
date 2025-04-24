# Contributor: Lex Black <autumn-wind@web.de>

pkgname=opencloud-desktop
pkgver=1.0.0
pkgrel=1
pkgdesc='opencloud desktop application'
arch=('x86_64')
url="https://github.com/opencloud-eu/desktop"
license=('GPL-2.0-only')
depends=(gcc-libs
         glibc
         kdsingleapplication
         libre-graph-api
         qt6-base
         qtkeychain-qt6
         sqlite
         zlib)
makedepends=(doxygen
             extra-cmake-modules
             python-sphinx
	         qt6-declarative
             qt6-tools)
backup=('etc/OpenCloud/sync-exclude.lst')
source=("${pkgname}-${pkgver/_/-}.tar.gz::https://github.com/opencloud-eu/desktop/archive/refs/tags/v${pkgver/_/-}.tar.gz")
sha256sums=('b4c821cf3b1806339d4e9419a0caa7ee53a49402b573038bf4cbc3973af80730')


build() {
	cmake \
		-B build \
		-S "desktop-${pkgver/_/-}" \
		-DCMAKE_BUILD_TYPE=None \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DCMAKE_SKIP_INSTALL_RPATH=ON \
		-DBUILD_TESTING=OFF \
		-DKDE_INSTALL_SYSCONFDIR=/etc
	make -C build
}

package() {
	make DESTDIR="${pkgdir}/" -C build install
}
