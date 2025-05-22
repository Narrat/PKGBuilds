# Contributor: Lex Black <autumn-wind@web.de>

pkgname=wireguard-go
pkgver=0.0.20250522
pkgrel=1
pkgdesc="Go userspace implementation of WireGuard"
arch=('i686' 'pentium4' 'x86_64' 'armv7h' 'armv6h' 'aarch64')
url="https://git.zx2c4.com/wireguard-go/"
license=('GPL')
makedepends=('go')
source=(https://git.zx2c4.com/wireguard-go/snapshot/${pkgname}-${pkgver}.tar.xz)
sha1sums=('01256e3a4539d7bef00638568b4089ce14880c15')


build() {
  cd "$pkgname-$pkgver"
  make DESTDIR="$pkgdir"
}

package() {
  cd "$pkgname-$pkgver"
  make DESTDIR="$pkgdir" PREFIX=/usr install
}
