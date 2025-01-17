pkgname=goguma-git
pkgver=v0.7.0.r95.g6ae36e2
pkgrel=1
pkgdesc='An IRC client for mobile devices'
url="https://codeberg.org/emersion/goguma"
arch=('x86_64')
license=('GPL3')
depends=() #TODO
makedepends=('flutter')
source=('git+https://codeberg.org/emersion/goguma.git' 'goguma.desktop')
md5sums=('SKIP' 'SKIP')

pkgver() {
  cd $srcdir/goguma
  git describe --long | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
  cd $srcdir/goguma
  flutter build linux
}

package() {
  mkdir -p $pkgdir/opt/goguma/
  cp -r $srcdir/goguma/build/linux/x64/release/bundle/* $pkgdir/opt/goguma/

  mkdir -p $pkgdir/usr/bin/
  ln -s $pkgdir/opt/goguma/goguma $pkgdir/usr/bin/goguma

  mkdir -p $pkgdir/usr/share/applications/
  cp $srcdir/goguma.desktop $pkgdir/usr/share/applications/

  mkdir -p $pkgdir/usr/share/icons/hicolor/192x192/apps/
  cp $srcdir/goguma/android/app/src/main/res/mipmap-xxxhdpi/ic_launcher.png $pkgdir/usr/share/icons/hicolor/192x192/apps/goguma.png
}
