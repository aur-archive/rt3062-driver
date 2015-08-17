#Maintainer Chais <chais.z3r0[at]gmail[dot]com>

DLAGENTS=('http::/usr/bin/curl -d "sn=5019&uname=ArchUser&email=user%40arch.fake" -O %u')
pkgname=rt3062-driver
pkgver=2.4.1.1_20101217
pkgrel=3
pkgdesc="Driver for the Ralink RT3062 chipset"
arch=('any')
url="http://www.ralinktech.com"
license=('GPL2 or any later version')
makedepends=('linux-headers')
install='rt3062-driver.install'
source=("DPO_RT3562_3592_3062_LinuxSTA_V$pkgver.tgz::http://www.mediatek.com/_en/07_downloads/dl.php"
	'Makefile.patch'
	'Makefile.6.patch'
	'config.mk.patch')
md5sums=('a5e9af70abccdb7b86d1ef605bb34491'
         '85f896eb933eb7a34515db4d6d433868'
         '2c1fe0467261039bd3eed27cb1e3d174'
         'c24c23f4c15ce78ceb8f490b4d04dd8c')

build(){
	cd $srcdir/DPO_RT3562_3592_3062_LinuxSTA_V$pkgver
	patch -Np1 -i $srcdir/config.mk.patch
	patch -Np1 -i $srcdir/Makefile.patch
	patch -Np1 -i $srcdir/Makefile.6.patch
	cd ${srcdir}/DPO_RT3562_3592_3062_LinuxSTA_V${pkgver}/
	make
}
package (){
	cd $srcdir/${source[0]%%\.tgz*}
	mkdir ${pkgdir}/etc
	make DESTDIR="${pkgdir}" install
}
