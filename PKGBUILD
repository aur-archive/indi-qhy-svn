# $Id: PKGBUILD 62098 2010-01-02 09:13:44Z tpowa $
# Maintainer: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Tobias Powalowski <tpowa@archlinux.org>

pkgname=indi-qhy-svn
pkgver=0.2
pkgrel=2
pkgdesc="The INDI drivers for the QHY family CCDs"
url="http://www.indilib.org/index.php?title=Main_Page"
license=('GPL2')
arch=('i686' 'x86_64')
depends=('libnova' 'cfitsio' 'boost-libs' 'libindi')
makedepends=('pkgconfig' 'cmake' 'boost')
options=('!libtool')

build() {
  svn co https://indi.svn.sourceforge.net/svnroot/indi/trunk/3rdparty/indi-qhy
  cd "${srcdir}"
  mkdir -p build
  cd build 
  LDFLAGS="-lm" cmake ../indi-qhy \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd "${srcdir}"/build
  make DESTDIR="${pkgdir}" install
  mv "${pkgdir}/lib" "${pkgdir}/usr/lib"
}
