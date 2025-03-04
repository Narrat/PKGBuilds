# Contributor: Lex Black <autumn-wind@web.de>

pkgname=opencloud
pkgver=1.0.0
pkgrel=3
pkgdesc="secure and private way to store, access, and share your files"
url="https://github.com/opencloud-eu/opencloud"
arch=('aarch64' 'x86_64')
license=('Apache-2.0')
#depends=('glibc')
makedepends=('git' 'go' 'pnpm')
install="opencloud.install"
backup=('etc/opencloud/opencloud.env')
source=("git+https://github.com/opencloud-eu/opencloud.git#tag=v${pkgver}"
        "go.mk.patch"
        "0001-Bump-mockery-to-2.53.0.patch"
        "opencloud.env"
        "opencloud.service"
        "opencloud.sysusers"
        "opencloud.tmpfiles")
sha512sums=('1c80285c77e8866841422ee98f109708647e62272648bb220b1a0987c83d105da721b957e87c99891955eb6565a8df784edb53410ce75ab73ef97c2d0444de0d'
            'da70b77bf25c87d75f1a662d00a339f9b8756e6f8e33e17dcc0663d2dcd7d4981720a93fe1ba6c788d8a5e7f484f8e292e59273793106d496955c5a670862318'
            'ee58b9be8fbd9d6c891497b3986c7d7f218cdfd8cdcc405b3029c1df70d321fc2d5796f6b3a66cc2f8fe77fa3a1065c3859598ddcafdb762cc96f3a448f9740c'
            'cf83e1357eefb8bdf1542850d66d8007d620e4050b5715dc83f4a921d36ce9ce47d0d13c5d85f2b0ff8318d2877eec2f63b931bd47417a81a538327af927da3e'
            '7d222cad3f0d42c9e070fb429319e6cd6eeda1065c052336a1969dbcf86319c0a70601b77ee2ab3cbe35f276a70195affd925fe4c8bcc7f692bccf408ebc9279'
            '3fa38aba73ffea0e559cf20af9f12b85321a97b41d48aad5c7cea81e9ab7d35c08d7a495c62e6a9fdf6ac7c494a4926805d89171dca0d822d922902188babed3'
            'e4b8c5bfda8214d6493055c996010b385c3be62a861dbcb3564c68aa03851bb6f23cd269f1b869fe4eeec6396ca9943888628c2a46215a7bd3c02c2a8f000742')


prepare() {
    cd "${pkgname}"
        
    patch .make/go.mk "${srcdir}"/go.mk.patch
    patch -Np1 -i "${srcdir}"/0001-Bump-mockery-to-2.53.0.patch
}

build() {
    cd ${pkgname}

    export CGO_CPPFLAGS="${CPPFLAGS}"
    export CGO_CFLAGS="${CFLAGS}"
    export CGO_CXXFLAGS="${CXXFLAGS}"
    export CGO_LDFLAGS="${LDFLAGS}"
    export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"

    make generate
    make build
}

package() {
    install -vDm755 "${pkgname}/${pkgname}/bin/${pkgname}" "${pkgdir}/usr/bin/${pkgname}-server"

    install -vdm755 "${pkgdir}/etc/${pkgname}"
    install -vDm750 "${pkgname}.env" -t "${pkgdir}/etc/${pkgname}"

    install -vDm644 "${pkgname}.service" -t "${pkgdir}/usr/lib/systemd/system"
    install -vDm644 "${pkgname}.sysusers" "${pkgdir}/usr/lib/sysusers.d/${pkgname}.conf"
    install -vDm644 "${pkgname}.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/${pkgname}.conf"
}
