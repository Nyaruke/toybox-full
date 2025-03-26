# Maintainer: Score_Under <seejay.11@gmail.com>
# Contributor: Gavin Lloyd <gavinhungry@gmail.com>
# Contributor: Pablo Lezaeta <prflr88@gmail.com>
# Contributor: BlackLotus89 <maxmusterm@gmail.com>

_pkgname=toybox
pkgname=toybox-full
pkgver=0.8.12
pkgrel=1
pkgdesc='All-in-one Linux command line (An experimental version that enables all available commands.)'
arch=('i686' 'x86_64' 'armv6h' 'armv7h')
url='https://landley.net/toybox'
license=('BSD')
depends=('attr')
conflicts=('toybox')
source=(
    "https://landley.net/${_pkgname}/downloads/${_pkgname}-${pkgver}.tar.gz"
    "defconfig"
    # Alternative link (checksum will be different due to compression): "https://github.com/landley/${pkgname}/archive/${pkgver}.tar.gz"
)
sha256sums=('ad88a921133ae2231d9f2df875ec0bd42af4429145caea7d7db9e02208a6fd2e'
            'SKIP')

build() {
  cd "${srcdir}/${_pkgname}-${pkgver}"

  make defconfig
  cp -f "${srcdir}/defconfig" "${srcdir}/${_pkgname}-${pkgver}/.config"
  
  NOSTRIP=1 make
}

package() {
  cd "${srcdir}/${_pkgname}-${pkgver}"

  PREFIX="${pkgdir}/opt/${_pkgname}" make install
  install -Dm755 "$_pkgname" "${pkgdir}/usr/bin/${_pkgname}"
  ln -sf "/usr/bin/${_pkgname}" "${pkgdir}/opt/${_pkgname}/bin/${_pkgname}"
  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${_pkgname}/LICENSE"
}
