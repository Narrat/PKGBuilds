# Contributor: Sinnamon (George Aladin) <AngleSi at yahoo dot com>

pkgname=loop-aes
_pkgname=loop-AES
pkgver=3.7p
pkgrel=1
pkgdesc="This package provides loadable Linux kernel module loop
that has AES,Twofish,Blowfish,Serpent cipher built-in."
arch=('i686' 'x86_64')
license=('GPL2')
url="https://loop-aes.sourceforge.net"
depends=('linux' 'util-linux-aes')
makedepends=('linux-headers')
install=${pkgname}.install
source=(${url}/${_pkgname}/${_pkgname}-v${pkgver}.tar.bz2{,.sign})
md5sums=('a8e8f2c3fe27b67f332c33555b9d8c8e'
         'SKIP')
validpgpkeys=('F0733C808132F189')


build() {
	cd "${_pkgname}-v${pkgver}"
	make MODINST=n EXTRA_CIPHERS=y -j1 LINUX_SOURCE=/usr/lib/modules/$(uname -r)/build
}

package() {
	cd "${_pkgname}-v${pkgver}/tmp-d-kbuild/"
	gzip loop.ko
	gzip loop_serpent.ko
	gzip loop_twofish.ko
	gzip loop_blowfish.ko
	install -D loop.ko.gz ${pkgdir}/usr/lib/modules/$(uname -r)/$(readlink /usr/lib/modules/$(uname -r)/extramodules)/loop-aes.ko.gz
	install loop_serpent.ko.gz ${pkgdir}/usr/lib/modules/$(uname -r)/$(readlink /usr/lib/modules/$(uname -r)/extramodules)/
	install loop_twofish.ko.gz ${pkgdir}/usr/lib/modules/$(uname -r)/$(readlink /usr/lib/modules/$(uname -r)/extramodules)/
	install loop_blowfish.ko.gz ${pkgdir}/usr/lib/modules/$(uname -r)/$(readlink /usr/lib/modules/$(uname -r)/extramodules)/
	install -d -m755 "${pkgdir}/usr/lib/modprobe.d"
	install -d -m755 "${pkgdir}/usr/lib/modules-load.d"
	echo "blacklist loop" >> "${pkgdir}/usr/lib/modprobe.d/loop.conf"
	echo "alias loop loop-aes" > "${pkgdir}/usr/lib/modprobe.d/loop.conf"
	echo "loop-aes" > "${pkgdir}/usr/lib/modules-load.d/loop.conf"
	echo "loop_serpent" >> "${pkgdir}/usr/lib/modules-load.d/loop.conf"
	echo "loop_twofish" >> "${pkgdir}/usr/lib/modules-load.d/loop.conf"
	echo "loop_blowfish" >> "${pkgdir}/usr/lib/modules-load.d/loop.conf"
}
