# Maintainer: Lex Black <autumn-wind@web.de>

pkgname=prosody-mod-invites-register-web
pkgver=2020.10.06
pkgrel=2
_commit="39d1a4ecdee6"
pkgdesc="Register accounts via the web using invite tokens"
arch=('any')
url="https://modules.prosody.im/mod_invites_register_web.html"
license=('MIT')
depends=('prosody' 'prosody-mod-invites-page')
makedepends=('mercurial')
optdepends=("prosody-mod-register-apps: Configuring list of XMPP clients")
source=("hg+https://hg.prosody.im/prosody-modules/"#revision=$_commit)
sha1sums=('SKIP')


package() {
  cd "${srcdir}/prosody-modules/mod_invites_register_web"
  find . -type f -name '*.lua' -exec install -Dm 644 '{}' "${pkgdir}/usr/lib/prosody/modules/{}" \;
  install -Dm644 html/* -t "${pkgdir}/usr/lib/prosody/modules/html/"
  find . -type f ! -name '*.lua' -exec install -Dm 644 '{}' "${pkgdir}/usr/share/doc/${pkgname}/{}" \;
  rm -r "${pkgdir}/usr/share/doc/${pkgname}/html"
}
