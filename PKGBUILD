# Maintainer: Lex Black <autumn-wind at web dot de>
# Contributor: patlefort <northon_patrick3 at yahoo dot ca>
# Contributor: Daniel Larsson <znixen@live.se>

pkgbase=patool
pkgname='patool'
pkgver=2.4.0
pkgrel=1
pkgdesc="portable command line archive file manager"
arch=('any')
url="https://wummel.github.io/patool/"
license=('GPL-3-only')
depends=(python)
makedepends=(python-build python-installer python-wheel python-setuptools python-argcomplete)
optdepends=("lz4: extracting LZ4 archives"
    "p7zip: extracting ZIP and 7z files"
    "unarchiver: extracting various formats"
    "unrar: extracting RAR files"
    "zstd: extracting ZSTANDARD files")
#source=("https://pypi.python.org/packages/source/p/$pkgbase/$pkgbase-$pkgver.tar.gz")
source=(https://github.com/wummel/${pkgname}/releases/download/dist%2F${pkgname}-${pkgver}-py2.py3-none-any.whl/${pkgname}-${pkgver}.tar.gz)
sha256sums=('2c54bcd2b904bf37253fad4f5d04cec808056b15fa974fd36b2a84fc931f3c0f')


build() {
  cd "${pkgbase}-${pkgver}"
  python -m build --wheel --no-isolation
}

package() {
  cd "${pkgbase}-${pkgver}"
  python -m installer --destdir="$pkgdir" dist/*.whl

  install -dm755 "${pkgdir}/usr/share/bash-completion/completions"
  register-python-argcomplete patool > "${pkgdir}/usr/share/bash-completion/completions/patool"

  install -Dm644 'doc/patool.1' -t "${pkgdir}/usr/share/man/man1"
}
