# Original creator of AUR Package: Katy Moe katy@katy.moe
# Patch creator: Moreno G moreno.giussani@protonmail.com
# Adaptation author: Brandom Rodriguez brandomrobor@tuta.io

_kernver="$(uname -r)"
_kernver_base="$(echo $_kernver | cut -d- -f1)"
pkgname=btusb-210681-fix
_pkgname=btusb
url=https://github.com/BrandomRobor/btusb-210681-fix
pkgver="$_kernver_base"
pkgrel=1
pkgdesc="patch btusb so it works on QCA devices with id 0x3004"
arch=('i686' 'x86_64')
license=('GPL')
source=("Makefile"
	"rome_fix.patch"
	"btusb-210681-fix.install"
	"btusb.c::https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/plain/drivers/bluetooth/btusb.c?id=refs/tags/v$_kernver_base"
	"btintel.h::https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/plain/drivers/bluetooth/btintel.h?id=refs/tags/v$_kernver_base"
	"btbcm.h::https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/plain/drivers/bluetooth/btbcm.h?id=refs/tags/v$_kernver_base"
	"btrtl.h::https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/plain/drivers/bluetooth/btrtl.h?id=refs/tags/v$_kernver_base")
install=btusb-210681-fix.install
	
pkgver() {
 printf "$_kernver_base"
}

prepare() {
	echo $_kernver_base
	\cp --remove-destination $(readlink btusb.c) btusb.c
	patch -p1 < rome_fix.patch
}

build() {
	make
}

package() {
	install -Dm644 btusb.ko "$pkgdir/usr/lib/modules/$_kernver/updates/btusb.ko"
}

md5sums=('369ff1a06ddfa06bc68bd776d3fbc97e'
         '15fa68976876a8c569106f2ddca4a6a0'
         'db64ca96ea96e856b9e200cdeb86b681'
         'SKIP'
         'SKIP'
         'SKIP'
         'SKIP')
