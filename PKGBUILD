# Contributor: Lex Black <autumn-wind@web.de>

_pkgname=opencloud
pkgname=opencloud-bin
pkgver=3.0.0
pkgrel=4
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
sha512sums=('86d6cb0d07cbe48c3ee4e78378393aac0613526330a858956338b9e3d2069481f5466456cb79f6426993272d47d1cc08e37d7131478de7711729e281b5ade83d'
            'af6b2e80ebaf130fb3e8f6038580bea4db811499d06f2962604941f75d1f8ef0dd3692bf21e54c0611864c49217c8fa457cb6773775a1aa47c7254330f83ba7f'
            '3fa38aba73ffea0e559cf20af9f12b85321a97b41d48aad5c7cea81e9ab7d35c08d7a495c62e6a9fdf6ac7c494a4926805d89171dca0d822d922902188babed3'
            'e4b8c5bfda8214d6493055c996010b385c3be62a861dbcb3564c68aa03851bb6f23cd269f1b869fe4eeec6396ca9943888628c2a46215a7bd3c02c2a8f000742')
sha512sums_aarch64=('1565f07a284a66ea829c1e7349f0b73bcd148b2d0c44999dda7e6f46732a5abeaaf7091dccb3dd907a0386f2bb1ac2df12c20e96c1e5841aef73c7f09ac1997b')
sha512sums_x86_64=('515159c1a10972099e9f16dcc513ef20b14a60f14a7e69172fc5d75f2c96f3214772d501031d107e0c547b6f38006fd5084581ca118df3ac9c57f98f739bbca8')


package() {
    install -vDm755 "${_pkgname}-${pkgver}-${CARCH}" "${pkgdir}/usr/bin/${_pkgname}-server"

    install -vdm755 "${pkgdir}/etc/${_pkgname}"
    install -vDm644 "${_pkgname}.env" -t "${pkgdir}/etc/${_pkgname}"

    install -vDm644 "${_pkgname}.service" -t "${pkgdir}/usr/lib/systemd/system"
    install -vDm644 "${_pkgname}.sysusers" "${pkgdir}/usr/lib/sysusers.d/${_pkgname}.conf"
    install -vDm644 "${_pkgname}.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/${_pkgname}.conf"
}
