# Maintainer: Lex Black <autumn-wind@web.de>
# Contributor: Alexander F Rødseth <xyproto@archlinux.org>
# Contributor: Thomas S Hatch <thatch45@gmail.com>
# Contributor: Corrado 'bardo' Primier <corrado.primier@mail.polimi.it>
# Contributor: Jochem Kossen <j.kossen@home.nl>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>

pkgname=scite
pkgver=4.0.3
pkgrel=1
pkgdesc='Editor with facilities for building and running programs'
arch=('x86_64')
url='http://www.scintilla.org/SciTE.html'
license=('custom:scite')
depends=('gtk3')
backup=('usr/share/scite/SciTEGlobal.properties')
source=("http://downloads.sourceforge.net/sourceforge/scintilla/${pkgname}${pkgver//./}.tgz")
sha256sums=('72b54920ca8be1c6ec5e0f429dcfdb09282d921979d647973327dfd7ae54abde')

build() {
  GTK3=1 make -C "scintilla/gtk"
  GTK3=1 make -C "$pkgname/gtk"
}

package() {
  GTK3=1 make -C "$pkgname/gtk" DESTDIR="$pkgdir" install
  install -Dm644 "$pkgname/License.txt" \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE-scite"
  install -Dm644 "scintilla/License.txt" \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE-scintilla"
  ln -sf "/usr/bin/SciTE" "$pkgdir/usr/bin/scite"
}
