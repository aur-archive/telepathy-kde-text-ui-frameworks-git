# Maintainer: Antonio Rojas 

pkgname=telepathy-kde-text-ui-frameworks-git
pkgver=r1708.d4bb578
pkgrel=1
pkgdesc='Telepathy handler for Text Chats'
arch=('i686' 'x86_64')
url='http://community.kde.org/Real-Time_Communication_and_Collaboration'
license=('GPL')
depends=('telepathy-kde-common-internals-frameworks-git')
makedepends=('extra-cmake-modules' 'git' 'kdoctools' 'python')
conflicts=('telepathy-kde-text-ui-frameworks' 'telepathy-kde-text-ui')
provides=('telepathy-kde-text-ui-frameworks')
source=("git://anongit.kde.org/ktp-text-ui.git#branch=frameworks")
sha256sums=('SKIP')

pkgver() {
  cd ktp-text-ui
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../ktp-text-ui \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release \
    -DLIB_INSTALL_DIR=lib \
    -DLIBEXEC_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
