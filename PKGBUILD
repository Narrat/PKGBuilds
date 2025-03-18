# Contributor: Lex Black <autumn-wind@web.de>

pkgname=opencloud
pkgver=1.1.0
pkgrel=1
pkgdesc="secure and private way to store, access, and share your files"
url="https://github.com/opencloud-eu/opencloud"
arch=('aarch64' 'x86_64')
license=('Apache-2.0')
#depends=('glibc')
makedepends=('git' 'go' 'pnpm')
install="opencloud.install"
backup=('etc/opencloud/opencloud.env')
source=("git+https://github.com/opencloud-eu/opencloud.git#tag=v${pkgver/_/-}"
        "go.mk.patch"
        "opencloud.env"
        "opencloud.service"
        "opencloud.sysusers"
        "opencloud.tmpfiles")
sha512sums=('55480069e8371f5ad71896cac033b4f885ab7e014db5bc6626c09687ec27f1e40ab0b6e5ca196f77fd616f9233c6ff633f30940f9f8d7089be6dc7ac7bbda183'
            'da70b77bf25c87d75f1a662d00a339f9b8756e6f8e33e17dcc0663d2dcd7d4981720a93fe1ba6c788d8a5e7f484f8e292e59273793106d496955c5a670862318'
            'cf83e1357eefb8bdf1542850d66d8007d620e4050b5715dc83f4a921d36ce9ce47d0d13c5d85f2b0ff8318d2877eec2f63b931bd47417a81a538327af927da3e'
            'af6b2e80ebaf130fb3e8f6038580bea4db811499d06f2962604941f75d1f8ef0dd3692bf21e54c0611864c49217c8fa457cb6773775a1aa47c7254330f83ba7f'
            '3fa38aba73ffea0e559cf20af9f12b85321a97b41d48aad5c7cea81e9ab7d35c08d7a495c62e6a9fdf6ac7c494a4926805d89171dca0d822d922902188babed3'
            'e4b8c5bfda8214d6493055c996010b385c3be62a861dbcb3564c68aa03851bb6f23cd269f1b869fe4eeec6396ca9943888628c2a46215a7bd3c02c2a8f000742')


prepare() {
    cd "${pkgname}"
        
    patch .make/go.mk "${srcdir}"/go.mk.patch
}

build() {
    cd ${pkgname}

    export CGO_CPPFLAGS="${CPPFLAGS}"
    export CGO_CFLAGS="${CFLAGS}"
    export CGO_CXXFLAGS="${CXXFLAGS}"
    export CGO_LDFLAGS="${LDFLAGS}"
    export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"

    make -j1 generate
    make -C opencloud build
}

package() {
    install -vDm755 "${pkgname}/${pkgname}/bin/${pkgname}" "${pkgdir}/usr/bin/${pkgname}-server"

    install -vDm644 "${pkgname}.env" -t "${pkgdir}/etc/${pkgname}"

    install -vDm644 "${pkgname}.service" -t "${pkgdir}/usr/lib/systemd/system"
    install -vDm644 "${pkgname}.sysusers" "${pkgdir}/usr/lib/sysusers.d/${pkgname}.conf"
    install -vDm644 "${pkgname}.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/${pkgname}.conf"
}
