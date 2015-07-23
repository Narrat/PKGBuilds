# Maintainer: Lex Black <autumn-wind at web dot de>

_pkgname=canto-next
pkgname=canto-daemon
pkgver=0.9.4
pkgrel=1
pkgdesc="News aggregator for Atom/RSS/RDF"
url="http://codezen.org/canto-ng/"
license=('GPL')
arch=('any')
depends=('python-feedparser')
optdepends=('canto-curses: Curses interface'
            'python-requests: Needed by inoreader plugin')
source=(https://github.com/themoken/${_pkgname}/archive/v${pkgver}.tar.gz)
md5sums=('d53c061b8936c330993f507faf58461f')


package() {
    cd ${_pkgname}-${pkgver}

    python setup.py install --prefix=/usr --root=${pkgdir} #--optimize=1
}
