# Maintainer: Sameed Pervaiz <greenbagels@teknik.io>
# Contributor: Gustavo Alvarez <sl1pkn07@gmail.com>
# Contributor: Xiao-Long Chen <chenxiaolong@cxl.epac.to>
# Contributor: Jakub Schmidtke <sjakub-at-gmail-dot-com>
# Contributor: mosra <mosra@centrum.cz>

pkgname=kdevelop
pkgver=5.0.0
pkgrel=1
pkgdesc="A C/C++ development environment for KDE."
arch=('i686' 'x86_64')
url='http://www.kdevelop.org'
license=('GPL')
depends=('qt5-tools'
         'kdevplatform'
         'krunner'
         'hicolor-icon-theme'
         )
optdepends=('krunner: For enabling the KDevelop runner'
            'plasma-framework: Plasma libraries for enabling the plasma addons'
            'okteta: hex editor integration'
            'konsole: embedded terminal'
            'subversion: SVN support'
            'git: Git support'
            'cvs: Concurrent Versions System support'
            'gdb: GNU Debugger support'
            'qt4-doc: qt4 documentation integration'
            'qt5-doc: qt5 documentation integration'
            'cmake: build system'
            'kdevelop-pg-qt-git: Parser Generator'
            'clang: LLVM compiler plugin'
            )
makedepends=('extra-cmake-modules'
             'git'
             'okteta'
             'krunner'
             'plasma-framework'
             'kdevelop-pg-qt'
             'clang')
source=("git://anongit.kde.org/kdevelop.git#tag=v${pkgver}")
sha1sums=('SKIP')
install=kdevelop.install

pkgver() {
  cd "${srcdir}/${pkgname}"
  git describe --tags `git rev-list --tags --max-count=1` | sed 's/v//g'
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../kdevelop \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DBUILD_TESTING=OFF
  make
}

package() {
  make -C build DESTDIR="${pkgdir}" install
}
