# Maintainer: Lex Black <autumn-wind at web dot de>
# Contributor: Martin Miller <witsquash at lavabit dot com>
# Contributor: Christian Holme <cholme at gmx dot com>

pkgname=idlex
pkgver=1.18
pkgrel=2
pkgdesc="Extensions to IDLE, the Python IDE"
arch=('any')
url="http://idlex.sourceforge.net/"
license=('NCSA')
depends=('python')
options=(!emptydirs)
source=($pkgname.desktop "https://downloads.sourceforge.net/project/idlex/$pkgname-$pkgver.zip")
md5sums=('94c7662b5e4bf4bf94121a8f7c374d6d'
         '9efbaa83eebb95a50369028fb00a1ab9')

build() {
    cd "$pkgname-$pkgver"
    python setup.py build
}

package() {
    pushd "$pkgname-$pkgver"
    python setup.py install --root="$pkgdir/" --optimize=1 --skip-build
    install -Dm644 idlexlib/idlefork/idlelib/Icons/idle_48.png "$pkgdir"/usr/share/pixmaps/$pkgname.png
    popd
    install -Dm644 $pkgname.desktop "$pkgdir"/usr/share/applications/$pkgname.desktop
}
