# Maintainer: Lex Black <autumn-wind at web dot de>

_pkgname=canto-curses
pkgname=canto-curses-git
pkgver=0.9.9.r3.g13648d5
pkgrel=2
pkgdesc="ncurses user interface for canto-daemon/canto-next. Git version"
url="http://codezen.org/canto-ng/"
license=('GPL')
arch=('i686' 'x86_64')
depends=('ncurses' 'readline' 'canto-next-git>=0.9.2')
makedepends=('git' 'python-setuptools' 'python-build' 'python-installer' 'python-wheel')
optdepends=('xdg-utils: xdg-open is used as default browser')
conflicts=('canto-curses')
provides=('canto-curses=0.9.7')
source=('git+https://github.com/themoken/canto-curses#branch=master')
md5sums=('SKIP')


pkgver() {
    cd $_pkgname
    git describe --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g;s/v//'
}

build() {
    cd $srcdir/$_pkgname
    python -m build --wheel --no-isolation
}

package() {
    cd $srcdir/$_pkgname
    python -m installer --destdir="$pkgdir" dist/*.whl
}
