# Maintainer: Lex Black <autumn-wind at web dot de>
# Contributor: alejandrogomez <alejandroogomez@gmail.com>

pkgname=ydiff
pkgver=1.2
pkgrel=2
pkgdesc="Colored, incremental, side-by-side diff viewer"
arch=('any')
url="http://pypi.python.org/pypi/ydiff/"
license=('BSD')
depends=('python')
makedepends=('python-setuptools')
optdepends=("patchutils: uses filterdiff for context diffs")
conflicts=('cdiff')
source=(https://files.pythonhosted.org/packages/source/${pkgname::1}/${pkgname}/${pkgname}-${pkgver}.tar.gz)
md5sums=('f11c69a90774ec0f3fb3e45137fca931')


package() {
   cd "$srcdir/$pkgname-$pkgver"

   python setup.py install --root="$pkgdir/" --prefix=/usr --optimize=1
}
