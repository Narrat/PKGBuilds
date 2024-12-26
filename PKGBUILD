# Maintainer: Lex Black <autumn-wind at web dot de>

_pkgname=canto-curses
pkgname=canto-curses-git
pkgver=0.9.9.r3.g13648d5
pkgrel=4
pkgdesc="ncurses user interface for canto-daemon/canto-next. Git version"
url="http://codezen.org/canto-ng/"
license=('GPL')
arch=('i686' 'x86_64')
depends=('ncurses' 'readline' 'canto-next-git>=0.9.2')
makedepends=('git' 'python-setuptools' 'python-build' 'python-installer' 'python-wheel')
optdepends=('xdg-utils: xdg-open is used as default browser')
conflicts=('canto-curses')
provides=('canto-curses=0.9.7')
source=('git+https://github.com/themoken/canto-curses#branch=master'
        fix-build.patch
        remove-pipes-import.patch)
md5sums=('SKIP'
         '05f1e4b6ced0363581b697c14d67d640'
         'd6b501040ab0b37ac2d8922c6119c00e')


pkgver() {
    cd $_pkgname
    git describe --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g;s/v//'
}

prepare() {
    cd $_pkgname
    patch -Np1 -i ../fix-build.patch
    patch -Np2 -i ../remove-pipes-import.patch
}

build() {
    cd $_pkgname
    python -m build --wheel --no-isolation
}

package() {
    cd $_pkgname
    python -m installer --destdir="$pkgdir" dist/*.whl
}
