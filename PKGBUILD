# Maintainer: Daniel Zanco <dangpzanco at gmail dot com>
# Contributors:
# Felix Kauselmann <licorn at gmail dot com>
# Fabio 'Lolix' Loli <fabio.loli@disroot.org> -> https://github.com/FabioLolix

pkgname=yacreader-full
pkgver=9.14.2
pkgrel=1
pkgdesc="Comic reader for cross-platform reading and managing your digital comic collection. Complete set of features: Poppler (better PDF support); libarchive (better archive support: tar, 7z, zip, rar, zstd); headless server."
arch=(x86_64)
url="https://www.yacreader.com/"
license=(GPL3)
depends=(poppler-qt5 qt5-base qt5-multimedia qt5-quickcontrols2 qt5-graphicaleffects qt5-svg libarchive)
makedepends=(git qt5-tools)
optdepends=('qt5-imageformats: Support for extra image formats'
            'qrencode: YACReaderLibrary server info qr codes')
provides=(yacreader yacreaderlibraryserver)
conflicts=(yacreader)
source=("git+https://github.com/YACReader/yacreader.git#tag=${pkgver}")
sha256sums=('SKIP')

build() {
  cd "${srcdir}/yacreader"
  qmake-qt5 CONFIG+="poppler libarchive server_standalone"
  make
}

package() {
  cd "${srcdir}/yacreader"
  make INSTALL_ROOT="$pkgdir" sub-YACReader-install_subtargets sub-YACReaderLibrary-install_subtargets sub-YACReaderLibraryServer-install_subtargets
}
