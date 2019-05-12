# https://github.com/Earnestly/pkgbuilds/tree/master/bemenu-git
pkgname=bemenu-git
pkgver=r223.c3abc43
pkgrel=1

pkgdesc='Dynamic menu library and client program inspired by dmenu with support for wayland compositors.'
url='https://github.com/Cloudef/bemenu'
arch=('i686' 'x86_64')
license=('GPL3' 'LGPL3')
depends=('pango')
makedepends=('git' 'cmake' 'libxkbcommon' 'libxinerama' 'wayland')
optdepends=('wayland: For the wayland backend.'
            'libxkbcommon: For the wayland backend.'
            'libxinerama: For the x11 backend.'
            'ncurses: For the curses backend.')

provides=('bemenu')
conflicts=('bemenu')

source=('git://github.com/Cloudef/bemenu')

md5sums=('SKIP')

pkgver() {
    cd bemenu
    printf 'r%s.%s' "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
    cd bemenu
    cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_INSTALL_LIBDIR=/usr/lib
    make
}

check() {
    cd bemenu
    make test
}

package() {
    cd bemenu
    make DESTDIR="$pkgdir" install
}
