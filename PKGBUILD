# Merged with official ABS kcolorpicker PKGBUILD by João, 2021/03/05 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: dracorp aka Piotr Rogoza <piotr.r.public at gmail.com>

pkgname=kcolorpicker-git
pkgver=0.1.5_r68.g8c6a364
pkgrel=1
pkgdesc='Qt based Color Picker with popup menu'
arch=($CARCH)
url='https://github.com/DamirPorobic/kColorPicker'
license=(GPL)
makedepends=(git cmake-git)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
depends=(qt5-base)
source=("git+https://github.com/ksnip/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'project(kColorPicker' CMakeLists.txt | sed 's/.* //g' | tr - .)"
  echo "${_ver%)}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DBUILD_SHARED_LIBS=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
