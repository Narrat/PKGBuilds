# Contributor: Lex Black <autumn-wind@web.de>

_pkgname=opencloud
pkgname=opencloud-bin
pkgver=1.0.0
pkgrel=2
pkgdesc="secure and private way to store, access, and share your files"
url="https://github.com/opencloud-eu/opencloud"
arch=('aarch64' 'x86_64')
license=('Apache-2.0')
#depends=('glibc')
#makedepends=('go' 'pnpm')
install="opencloud.install"
conflicts=(opencloud)
provides=(opencloud)
backup=('etc/opencloud/opencloud.env')
source=("opencloud.env"
        "opencloud.service"
        "opencloud.sysusers"
        "opencloud.tmpfiles")
source_x86_64=(${_pkgname}-${pkgver}-x86_64::${url}/releases/download/v${pkgver}/${_pkgname}-${pkgver}-linux-amd64)
source_aarch64=(${_pkgname}-${pkgver}-aarch64::${url}/releases/download/v${pkgver}/${_pkgname}-${pkgver}-linux-arm64)
sha512sums=('cf83e1357eefb8bdf1542850d66d8007d620e4050b5715dc83f4a921d36ce9ce47d0d13c5d85f2b0ff8318d2877eec2f63b931bd47417a81a538327af927da3e'
            'f8dff935b7cc475c1067fd4c9577a84d1cbdca106f68b329346570adde08965eaea86b829ef3508af98e9b4463d2e179b85ef07ef7d8833d54e44f462295774b'
            '3fa38aba73ffea0e559cf20af9f12b85321a97b41d48aad5c7cea81e9ab7d35c08d7a495c62e6a9fdf6ac7c494a4926805d89171dca0d822d922902188babed3'
            'e4b8c5bfda8214d6493055c996010b385c3be62a861dbcb3564c68aa03851bb6f23cd269f1b869fe4eeec6396ca9943888628c2a46215a7bd3c02c2a8f000742')
sha512sums_aarch64=('09d39cbb1c651291356c9af626532b5860498962796ce0ba3533376f2f24560ab5389480d5066377d52a6612d14f3e4401225eb62e2e3334763b2c0cd1fe2ce2')
sha512sums_x86_64=('f8145baeea11123e57a6b863a1e49a057fd748974691b45304b2de8aba2320dcdb278a50af0a947e60915fb1de529dbfe87b0a4134b43b51ace94704237c4b27')


package() {
    install -vDm755 "${_pkgname}-${pkgver}-${CARCH}" "${pkgdir}/usr/bin/${_pkgname}"

    install -vdm755 "${pkgdir}/etc/${_pkgname}"
    install -vDm750 "${_pkgname}.env" -t "${pkgdir}/etc/${_pkgname}"

    install -vDm644 "${_pkgname}.service" -t "${pkgdir}/usr/lib/systemd/system"
    install -vDm644 "${_pkgname}.sysusers" "${pkgdir}/usr/lib/sysusers.d/${_pkgname}.conf"
    install -vDm644 "${_pkgname}.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/${_pkgname}.conf"
}
