#Maintainer Erik Inkinen <erik.inkinen@gmail.com>
pkgname=hadess-sensorfw-proxy
provides=('hadess-sensorfw-proxy')
_pkgbase=hadess-sensorfw-proxy
pkgver=26.6291246
pkgrel=1
arch=('armv7h' 'aarch64' 'x86' 'x86_64')
url="https://github.com/droidian/hadess-sensorfw-proxy"
license=('GPL3')
depends=('libgbinder' 'sensorfw-hybris' 'iio-sensor-proxy' 'qt5-base')
makedepends=('git' 'pkgconfig')
source=("hadess-sensorfw-proxy::git+https://github.com/droidian/hadess-sensorfw-proxy.git")
md5sums=('SKIP')
options=(debug !strip)

pkgver() {
  cd "${srcdir}/${_pkgbase}"
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
  cd "${srcdir}/${_pkgbase}"
  mkdir build
  cd build
  cmake .. -DCMAKE_INSTALL_BINDIR=/usr/bin
  make
}

package() {
  cd "${srcdir}/${_pkgbase}"
  make DESTDIR="$pkgdir/" install
  install -d "${pkgdir}/etc/systemd/system/iio-sensor-proxy.service.d/"
  install -Dm 644 10-hadess-sensorfw-proxy.conf "${pkgdir}/etc/systemd/system/iio-sensor-proxy.service.d/"
}


