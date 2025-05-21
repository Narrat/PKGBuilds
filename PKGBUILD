# Maintainer: Lex Black (autumn-wind at web.de)
# Contributor: andre.vmatos

_pkgname=resynthesizer
pkgname=gimp-plugin-$_pkgname-git
pkgver=2.0.3.r153.g3846f79
pkgrel=1
pkgdesc="Suite of gimp plugins for texture synthesis (like heal-selection). Git-Version"
arch=('i686' 'x86_64')
url="https://github.com/bootchk/resynthesizer"
license=('GPL2')
depends=('gimp')
makedepends=('git' 'meson')
conflicts=('gimp-resynth' 'gimp-resynth-git')
provides=("${pkgname/-git/}=3.0")
options=('!emptydirs')
source=('git+https://github.com/bootchk/resynthesizer#branch=resynthesizer3')
md5sums=('SKIP')


pkgver() {
    cd $_pkgname
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g;s/^v//'
}

build() {
    arch-meson ${_pkgname} build
    meson compile -C build
}

package() {
    meson install -C build --destdir "${pkgdir}"
}
