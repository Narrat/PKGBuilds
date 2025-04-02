# Contributor: Lex Black <autumn-wind@web.de>

pkgname=opencloud-desktop
pkgver=1.0.0_beta.1
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
sha256sums=('dd6ecc5697b3edde6b9a08428f696b824424e3fa7b5dad935ba2aadbc31b2781')


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
