# Contributor: Lex Black <autumn-wind@web.de>
# Contributor: Tmplt <tmplt@dragons.rocks>

pkgname=katriawm
pkgver=25.12
pkgrel=1
pkgdesc="non-reparenting, dynamic window manager for X11 with decorations"
arch=("i686" "x86_64")
url="https://www.uninformativ.de/git/katriawm/file/README.html"
license=("MIT")
makedepends=("git")
depends=("libx11" "libxft" "libxrandr")
source=("git+https://www.uninformativ.de/git/katriawm.git#tag=v${pkgver}")
sha256sums=('14f438961af70803d3999dac2af2451a5a155c0fb9db3259f751a1fddd659ea1')


prepare() {
  cd "${pkgname}/src"

  # Read custom config headers from $XDG_CONFIG_HOME/katria{wm,bi}-config.h
  config=${XDG_CONFIG_HOME:-~/.config/}

  if [[ -f "${config}/katriawm-config.h" ]]; then
      msg "Using custom config.h for katriawm(1)"
      cp -f "${config}/katriawm-config.h" core/config.h
  fi

  if [[ -f "${config}/katriabi-config.h" ]]; then
      msg "Using custom config.h for katriabi(1)"
      cp -f "${config}/katriabi-config.h" barinfo/config.h
  fi
}

build() {
  make -C "${pkgname}/src" prefix=/usr
}

package() {
  make -C "${pkgname}/src" prefix=/usr DESTDIR=${pkgdir} install
  install -Dm644 ${pkgname}/LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
