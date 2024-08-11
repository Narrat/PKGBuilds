# Contributor: Lex Black <autumn-wind@web.de>
# Contributor: Ista Zahn <istazahn[at]gmail[dot]com>

pkgbase=python-altair
_pyname=altair
pkgname=('python-altair')
pkgver=5.4.0
pkgrel=1
pkgdesc="Declarative statistical visualization library for Python"
arch=('any')
url="https://altair-viz.github.io/"
license=('BSD-3-Clause')
depends=(python-jinja python-jsonschema python-narwhals)
makedepends=(python-build python-installer python-wheel python-hatchling)
optdepends=('python-numpy: for NumPy and Pandas imports'
            'python-pandas: for Pandas imports'
            'python-selenium: png and svg export support'
            'python-vl-convert: png and svg export support via vega-lite specs')
source=("${_pyname}-${pkgver}.tar.gz::https://files.pythonhosted.org/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz")
sha256sums=('27c69e93d85b7bb3c98fa3626ef7e6bc6939a1466a55a8f8bf68c4bff31cf030')


build() {
  cd "${_pyname}-${pkgver}"
  python -m build --wheel --no-isolation
}

package() {
  cd "${_pyname}-${pkgver}"
  python -m installer --destdir="$pkgdir" dist/*.whl
  install -Dm 644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  install -Dm 644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README"
}

# vim:set et sw=2 ts=2 tw=79:
