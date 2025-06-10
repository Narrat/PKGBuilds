# Contributor: Lex Black <autumn-wind@web.de>

pkgname=opencloud-web
pkgver=3.0.0
pkgrel=1
pkgdesc="Web UI for OpenCloud"
url="https://github.com/opencloud-eu/web"
arch=('aarch64' 'x86_64')
license=('AGPL-3.0-only')
makedepends=('git' 'pnpm')
install="opencloud-web.install"
backup=("var/lib/opencloud-web/config.json")
source=("${pkgname}::git+https://github.com/opencloud-eu/web.git#tag=v${pkgver/_/-}"
        "config.json")
sha512sums=('d76e988ca7acb6bd09362d509b9c6c40e70fba6f4fbed7be856aa176e2186c8e83549500b107b8763f89d9fb36854d4388e5dda83f18462c7738c7aea5f92352'
            'c3692ff7d3f42af2c42d97d633cd14094c3b6421099b7eb74372ba9959ceca95f69c38da679b908802b7b5a5c2199484bb42ddc028e9e1372fb040fe51683e27')


build() {
    make -C ${pkgname} -j1 -f Makefile.release build
}

package() {
    # Base install location
    install -vdm755 "${pkgdir}/var/lib/${pkgname}"

    # Copy the created files from dist directory
    cp -rv ${pkgname}/dist/* "${pkgdir}/var/lib/${pkgname}"

    # Install custom web-ui config
    install -vm644 "${srcdir}/config.json" "${pkgdir}/var/lib/${pkgname}"
}
