pkgname=brave
pkgver=0.11.0
pkgrel=1
pkgdesc="A web browser automatically blocks ads and trackers"
arch=("x86_64")
url="https://www.brave.com/"
license=('GPL')
depends=('gconf' 'libcap' 'gtk2' 'nss' 'libxtst' 'libnotify' 'alsa-lib' 'libxss' 'libcups' 'libgnome-keyring' 'libxrandr')
source=("https://github.com/brave/browser-laptop/releases/download/v${pkgver}dev/brave_${pkgver}_amd64.deb")
md5sums=('20e64af2c50ff749b5c30c19df1dce39')
package() {
  tar -xJf $srcdir/data.tar.xz -C $pkgdir
  chmod -R 755 $pkgdir/usr
  rm -r $pkgdir/usr/share/{doc,lintian}
}
