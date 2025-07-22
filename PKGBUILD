# Maintainer: Daniel Zanco <dangpzanco at gmail dot com>

pkgname=yacreader-full
pkgver=9.15.0
pkgrel=1
pkgdesc="Comic reader for cross-platform reading and managing your digital comic collection. Complete set of features: Poppler (better PDF support); libarchive (better archive support: tar, 7z, zip, rar, zstd); headless server."
arch=(x86_64)
url="https://www.yacreader.com/"
license=(GPL3)
depends=(poppler-qt6 qt6-base qt6-multimedia qt6-declarative qt6-5compat libarchive
         glibc libglvnd gcc-libs hicolor-icon-theme)
makedepends=(git qt6-tools qt6-svg)
optdepends=('qt6-imageformats: Support for extra image formats'
            'qrencode: YACReaderLibrary server info qr codes')
provides=(yacreader yacreaderlibraryserver)
conflicts=(yacreader)
source=("git+https://github.com/YACReader/yacreader.git#tag=${pkgver}")
sha256sums=('SKIP')

build() {
  cd "${srcdir}/yacreader"
  qmake6 CONFIG+="poppler libarchive server_standalone"
  make
}

package() {
  cd "${srcdir}/yacreader"
  make INSTALL_ROOT="$pkgdir" sub-YACReader-install_subtargets sub-YACReaderLibrary-install_subtargets sub-YACReaderLibraryServer-install_subtargets
}
