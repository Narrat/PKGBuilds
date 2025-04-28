# Contributor: Lex Black <autumn-wind@web.de>

_pkgname=opencloud
pkgname=opencloud-bin
pkgver=2.2.0
pkgrel=1
pkgdesc="secure and private way to store, access, and share your files - upstream built binary"
url="https://github.com/opencloud-eu/opencloud"
arch=('aarch64' 'x86_64')
license=('Apache-2.0')
optdepends=("opencloud-web: if wanting to use a customized web interface")
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
sha512sums=('c4814a4843c4e82ea487e0152f09b08a2df6c8c90fc1139b18b9be4370fda12c692d85b86d2179f69e065790ec6bdb9a8cf8338ffa190636ea6bd7279dfed903'
            'af6b2e80ebaf130fb3e8f6038580bea4db811499d06f2962604941f75d1f8ef0dd3692bf21e54c0611864c49217c8fa457cb6773775a1aa47c7254330f83ba7f'
            '3fa38aba73ffea0e559cf20af9f12b85321a97b41d48aad5c7cea81e9ab7d35c08d7a495c62e6a9fdf6ac7c494a4926805d89171dca0d822d922902188babed3'
            'e4b8c5bfda8214d6493055c996010b385c3be62a861dbcb3564c68aa03851bb6f23cd269f1b869fe4eeec6396ca9943888628c2a46215a7bd3c02c2a8f000742')
sha512sums_aarch64=('feb8735910c24945371c276ac85dbf6fe6bf77a682b975f7a1cc5c125c8b942818f5ce64d822e7ed70c01da17f6ee63b03d30a8f30406cb86616c9d1994dd1b1')
sha512sums_x86_64=('58177dee0445a3b9986938617605e8bac4a3fdf335e6566138150be444fc137f10e179810d5f93ff542a8db7f61374ea179b1f75164efab0109433a57d3965e2')


package() {
    install -vDm755 "${_pkgname}-${pkgver}-${CARCH}" "${pkgdir}/usr/bin/${_pkgname}-server"

    install -vdm755 "${pkgdir}/etc/${_pkgname}"
    install -vDm750 "${_pkgname}.env" -t "${pkgdir}/etc/${_pkgname}"

    install -vDm644 "${_pkgname}.service" -t "${pkgdir}/usr/lib/systemd/system"
    install -vDm644 "${_pkgname}.sysusers" "${pkgdir}/usr/lib/sysusers.d/${_pkgname}.conf"
    install -vDm644 "${_pkgname}.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/${_pkgname}.conf"
}
