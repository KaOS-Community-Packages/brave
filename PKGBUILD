pkgname=brave
pkgver=0.9.1
pkgrel=1
pkgdesc="A web browser automatically blocks ads and trackers"
arch=("x86_64")
url="https://www.brave.com/"
license=('GPL')
depends=('gconf' 'libcap' 'gtk2' 'nss' 'libxtst' 'libnotify' 'alsa-lib' 'libxss' 'libcups' 'libgnome-keyring' 'libxrandr')
source=("https://github.com/brave/browser-laptop/releases/download/v${pkgver}dev/brave_${pkgver}_amd64.deb")
md5sums=('c3e7bfb0bbfcd912e2824e6545d37c6e')

package() {
  tar -xJf $srcdir/data.tar.xz -C $pkgdir
  chmod -R 755 $pkgdir/usr
  rm -r $pkgdir/usr/share/{doc,lintian}
}
