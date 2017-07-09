pkgname=pulseconnect
pkgver="8.2R5"
pkgrel=1
pkgdesc="Pulse Connect Secure VPN client"
arch=("i686" "x86_64")
url="https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB40126"
license=("unknown")
depends=("glibc" "zlib" "nss" "glib-networking" "libproxy" "libxmu")
makedepends=()
options=("emptydirs")
source=("pulse-${pkgver}.i386.rpm"
"ConfigurePulse.patch"
"PulseClient.patch")
md5sums=("cb5be8f78674cd413f6abee6efc7f909"
"16b7b40b594e82244029280241536e9e"
"99927497a8ace634d9d45de880c269c2")
install=pulse.install

prepare() {
  patch -p0 "${srcdir}/usr/local/pulse/ConfigurePulse.sh" < "${srcdir}/ConfigurePulse.patch"
  patch -p0 "${srcdir}/usr/local/pulse/PulseClient.sh" < "${srcdir}/PulseClient.patch"
}

package() {
  cp -r "${srcdir}/usr/local/" "${pkgdir}/opt/"
}
